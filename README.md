# 🛡️ Shield SDK

> **Sistema Híbrido Independente de Envio Livre de Dados**

[![Kotlin](https://img.shields.io/badge/Kotlin-1.9.22-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white)](https://kotlinlang.org)
[![JDK](https://img.shields.io/badge/JDK-17+-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)](https://openjdk.org)
[![License](https://img.shields.io/badge/license-GPL%203.0-blue?style=for-the-badge)](LICENSE)

[![Post-Quantum](https://img.shields.io/badge/Post--Quantum-Kyber--1024-blueviolet?style=for-the-badge&logo=atom&logoColor=white)](https://csrc.nist.gov/projects/post-quantum-cryptography)
[![NIST](https://img.shields.io/badge/NIST-FIPS%20203%20%7C%20204%20%7C%20205-003087?style=for-the-badge&logo=nist&logoColor=white)](https://csrc.nist.gov/projects/post-quantum-cryptography)
[![Security](https://img.shields.io/badge/Security-Hybrid%20PQ-critical?style=for-the-badge&logo=security&logoColor=white)]()

[![LGPD](https://img.shields.io/badge/LGPD-Compliant-009c3b?style=for-the-badge)](https://www.gov.br/cidadania/pt-br/acesso-a-informacao/dados-abertos/lgpd)
[![GDPR](https://img.shields.io/badge/GDPR-Compliant-003399?style=for-the-badge)](https://gdpr.eu)
[![Consent](https://img.shields.io/badge/Consent-Granular-009c3b?style=for-the-badge)]()

[![Platform](https://img.shields.io/badge/Platform-Android%20%7C%20JVM%20%7C%20Spring%20%7C%20Ktor-orange?style=for-the-badge&logo=android&logoColor=white)]()
[![Build](https://img.shields.io/badge/build-passing-brightgreen?style=for-the-badge)]()
[![Tests](https://img.shields.io/badge/tests-173%20passing-brightgreen?style=for-the-badge&logo=junit5&logoColor=white)]()

---

## 🔐 O Que é o Shield

**Shield SDK** é uma biblioteca criptográfica Kotlin/JVM que resolve um problema fundamental da era digital: **como compartilhar dados sensíveis de forma que apenas o destinatário autorizado possa ler, sem depender de servidores ou infraestrutura centralizada**.

### Em Uma Frase

> Seus dados são seus. Ponto.

### A Premissa

Compartilhar dados sensíveis hoje significa escolher entre conveniência e segurança. APIs expõem dados a intermediários. Criptografia clássica não resiste a computadores quânticos futuros. Sistemas de consentimento vivem fora da criptografia — são verificados *depois*, não *durante*.

O Shield resolve os três problemas simultaneamente:

| Problema | Solução Shield |
|----------|----------------|
| **Dados expostos em trânsito** | Criptografia no dispositivo do usuário, **antes** de qualquer transmissão |
| **Vulnerabilidade quântica** | Protocolo híbrido ECDH-P256 + Kyber-1024 → HKDF-SHA256 |
| **Consentimento frágil** | Campos não autorizados são descartados **antes** de encriptar — parte da criptografia |

---

## 🎯 Para Que Serve

### Casos de Uso Reais

O Shield é **agnóstico de setor** — funciona em qualquer domínio que necessite compartilhamento seguro de dados com consentimento granular.

#### 🏦 Setor Financeiro
- **Open Banking**: Compartilhamento de dados de cliente com fintechs parceiras
- **Análise de Crédito**: Envio seguro de informações para bureaus de crédito
- **Declaração de IR**: Transmissão de dados financeiros para contadores e Receita Federal

#### 🏥 Saúde
- **Prontuário Eletrônico**: Compartilhamento de histórico médico entre hospitais
- **Encaminhamento Médico**: Envio de dados para especialistas com consentimento do paciente
- **Planos de Saúde**: Autorização de procedimentos com operadoras

#### 🏛️ Governo
- **Benefícios Sociais**: Verificação de elegibilidade entre órgãos governamentais
- **Matrícula Escolar**: Compartilhamento de dados entre escolas e secretarias de educação
- **Identidade Digital**: Prova de atributos sem revelar documentos completos

#### 🛒 E-commerce & Varejo
- **Entrega de Produtos**: Compartilhamento de endereço com transportadoras
- **Gateways de Pagamento**: Transmissão segura de dados para processamento
- **Marketplace**: Compartilhamento com vendedores para fulfillment

#### 📚 Educação
- **Histórico Acadêmico**: Transferência de registros entre instituições de ensino
- **Verificação de Diplomas**: Validação de credenciais com universidades

#### 🚗 Seguros & Automotivo
- **Processamento de Sinistros**: Compartilhamento com vistoriadoras
- **Apólices Digitais**: Gestão de seguros com corretoras

#### 📱 Telecomunicações
- **Portabilidade Numérica**: Transferência de dados entre operadoras

---

## ⚙️ Como Funciona

### Arquitetura Macro

```
┌─────────────────────────────────────────────────────────────┐
│  EMISSOR (Dispositivo do Usuário)                           │
│                                                             │
│  Dados do Usuário + Consentimento                           │
│         ↓                                                   │
│  ┌─────────────────────────────────────────────────────┐   │
│  │  Shield SDK                                         │   │
│  │  1. Filtra campos consentidos                       │   │
│  │  2. Deriva chave de sessão (KEM Pós-Quântico)      │   │
│  │  3. Criptografa payload (AES-256-GCM)              │   │
│  │  4. Assina ciphertext + metadata (ECDSA/Dilithium) │   │
│  │  5. Produz SecureDataEnvelope                       │   │
│  └─────────────────────────────────────────────────────┘   │
│         ↓                                                   │
│  SecureDataEnvelope (opaco, serializável)                  │
└─────────────────────────────────────────────────────────────┘
                    ↓
        [Qualquer canal de transporte]
        HTTP / REST / gRPC / Kafka / Bluetooth / Arquivo
                    ↓
┌─────────────────────────────────────────────────────────────┐
│  RECEPTOR (Serviço/Parceiro)                                │
│                                                             │
│  SecureDataEnvelope                                         │
│         ↓                                                   │
│  ┌─────────────────────────────────────────────────────┐   │
│  │  Shield SDK                                         │   │
│  │  1. Valida assinatura                               │   │
│  │  2. Verifica expiração                              │   │
│  │  3. Deriva chave de sessão (KEM Pós-Quântico)      │   │
│  │  4. Decriptografa payload (AES-256-GCM)            │   │
│  │  5. Retorna dados consentidos                       │   │
│  └─────────────────────────────────────────────────────┘   │
│         ↓                                                   │
│  Dados do Usuário (apenas campos consentidos)              │
└─────────────────────────────────────────────────────────────┘
```

### Características Técnicas

| Característica | Descrição |
|----------------|-----------|
| **Plataforma** | Kotlin/JVM (Android API 24+, Spring Boot, Ktor, qualquer JVM 17+) |
| **Criptografia** | Híbrida pós-quântica: ECDH-P256 + Kyber-1024 → HKDF-SHA256 + AES-256-GCM |
| **Assinatura** | ECDSA SHA256withECDSA ou Dilithium5 (NIST FIPS 204) |
| **Consentimento** | Granular por campo de dados, com propósito e base legal |
| **Infraestrutura** | Zero dependência de servidor — funciona completamente offline |
| **Licença** | Apache License 2.0 (uso comercial permitido sem open source) |

### Protocolo de Segurança

#### Camada de Transporte da Chave
```
ECDH(P-256) + Kyber-1024 → HKDF-SHA256 → 32 bytes
     ↓                        ↓              ↓
  Clássico                Pós-Quântico   Chave de Sessão
```

A chave final só é comprometida se **ambos** os algoritmos forem quebrados simultaneamente.

#### Camada de Payload
- **Cipher**: AES-256-GCM ou ChaCha20-Poly1305
- **AAD**: `requestId|recipientId` — autentica o contexto junto com o ciphertext
- **Binding**: Mover o ciphertext para outro envelope invalida a tag

#### Assinatura Digital
- **Padrão**: ECDSA sobre ciphertext + metadata ordenado
- **Pós-Quântico**: Dilithium5 (NIST FIPS 204 / ML-DSA-65) disponível
- **Verificação**: Offline, sem estado, em qualquer sessão

---

## 🚀 Instalação

### Gradle (Kotlin DSL)
```kotlin
dependencies {
    implementation("io.Shield:Shield-sdk:2.0.0")
}
```

### Maven
```xml
<dependency>
    <groupId>io.Shield</groupId>
    <artifactId>Shield-sdk</artifactId>
    <version>2.0.0</version>
</dependency>
```

**Requisitos:**
- JVM 17+
- Kotlin 1.9.22+
- Android API 24+ (para uso em mobile)

---

## 💻 Uso Básico

### Modo Recomendado — Protocolo Híbrido Pós-Quântico

```kotlin
import io.Shield.config.SDKConfigBuilder
import io.Shield.models.share.DataField
import io.Shield.models.share.ShareSelection
import io.Shield.sdk.ShieldSDK

// ── Inicialização (uma vez por processo) ─────────────────────────────────
val sdk = ShieldSDK.initialize(SDKConfigBuilder().build())

// ── Receptor gera seu par de chaves ──────────────────────────────────────
// Em produção: persistir no Android Keystore, HSM ou Vault
val recipientKp = sdk.generateRecipientKeyPair()
// Publicar recipientKp.publicKey para quem precisar emitir envelopes

// ── Emissor define o consentimento ───────────────────────────────────────
val consent = ShareSelection(
    fields                = listOf(DataField.NAME, DataField.CPF),
    contextId             = "banco-parceiro",
    purpose               = "abertura-de-conta",
    legalBasis            = "consentimento-explicito",
    expiresAtEpochSeconds = System.currentTimeMillis() / 1000 + 3600
)

// ── Emissor cria o envelope ───────────────────────────────────────────────
val envelope = sdk.createSecureEnvelopePQ(
    userData     = mapOf("NAME" to "Ana Costa", "CPF" to "123.456.789-00"),
    consent      = consent,
    recipientId  = "banco-parceiro",
    recipientKey = recipientKp.publicKey
)
// envelope é serializável — envie por qualquer canal

// ── Receptor valida e decripta ────────────────────────────────────────────
sdk.validateAndConsumeEnvelope(envelope)   // valida + registra no anti-replay

val data = sdk.decryptEnvelopePQ(envelope, recipientKp)
// data = {"name" to "Ana Costa", "cpf" to "123.456.789-00"}
// Somente campos consentidos, em lowercase, sem exceção
```

### DSL — Sintaxe Fluente

```kotlin
import io.Shield.sdk.dsl.Shield

val envelope = Shield.createPQ(recipientKp.publicKey) {
    from(user = mapOf("NAME" to "João Silva", "CPF" to "987.654.321-00"))
    fields(DataField.NAME, DataField.CPF)
    with(recipient = "orgao-federal")
    `for`(purpose = "verificacao-identidade", legalBasis = "obrigacao-legal")
    expires(inHours = 24)
}
```

---

## 🔒 Garantias de Segurança

| Propriedade | Mecanismo | O Que Detecta |
|-------------|-----------|---------------|
| **Confidencialidade** | AES-256-GCM / ChaCha20-Poly1305 | Leitura por terceiros |
| **Integridade do Payload** | Tag GCM 128 bits | Qualquer alteração no ciphertext |
| **Binding de Contexto** | AAD `requestId\|recipientId` | Envelope movido para outro receptor |
| **Autenticidade** | ECDSA sobre ciphertext + metadata | Forja de envelope |
| **Anti-Replay** | ReplayGuard com janela de 1h | Reenvio do mesmo envelope |
| **Resistência Quântica (KEM)** | Kyber-1024 + ECDH-P256 via HKDF | Adversário com computador quântico |
| **Resistência Quântica (Assinatura)** | Dilithium5 (opcional) | Forja via algoritmo de Shor |

### Gerenciamento de Memória

Materiais criptográficos são zerados imediatamente após o uso:
- `ecSecret.fill(0)` e `kyberSecret.fill(0)` em bloco `finally`
- `sessionKey.fill(0)` após decriptografia
- `payloadBytes.fill(0)` após encriptação
- `decryptedBytes.fill(0)` após deserialização

---

## 📜 Conformidade Regulatória

| Requisito | Como o Shield Atende |
|-----------|----------------------|
| **LGPD Art. 46** — Medidas de segurança | AES-256-GCM + Kyber-1024, acima dos mínimos |
| **LGPD Art. 7** — Consentimento | `ShareSelection` com campos, propósito, base legal e expiração |
| **GDPR Art. 32** — Segurança do tratamento | Criptografia forte, minimização, auditoria |
| **GDPR Art. 17** — Direito ao esquecimento | Expiração configurável por envelope |
| **PCI DSS Req. 3-4** — Proteção de dados | Criptografia em trânsito e controle de acesso |

---

## 🌍 Ecossistema Soberana

O Shield SDK é a **fundação criptográfica** de um ecossistema mais amplo de soberania de dados:

```
┌─────────────────────────────────────────────────────────────┐
│                   Malha Soberana                            │
│   Rede distribuída de nós validados                         │
│   • Identidade criptográfica descentralizada                │
│   • Roteamento seguro de envelopes                          │
│   • Escala nacional/federal                                 │
└─────────────────────────────────────────────────────────────┘
                            ↑
                            │ fundamenta
                            ↓
┌─────────────────────────────────────────────────────────────┐
│                   Soberana App                              │
│   Cofre pessoal de identidade no dispositivo                │
│   • Documentos e atributos criptografados                   │
│   • Consentimento granular via UI                           │
│   • Backend zero-knowledge (NUNTIUS)                        │
└─────────────────────────────────────────────────────────────┘
                            ↑
                            │ utiliza
                            ↓
┌─────────────────────────────────────────────────────────────┐
│                   Shield SDK                                │
│   Primitiva criptográfica de compartilhamento seguro        │
│   • Open Source (Apache 2.0)                                │
│   • Funciona em qualquer JVM                                │
│   • Sem dependência de servidor                             │
└─────────────────────────────────────────────────────────────┘
```

### Visão de Futuro

O Shield SDK nasceu como uma primitiva criptográfica open source. Seu potencial se expande em duas direções:

#### 1. App de Governança de Dados Pessoais
Uma aplicação onde cidadãos armazenam documentos e atributos criptografados no próprio dispositivo, decidindo conscientemente o que compartilhar, com quem, por quanto tempo e sob quais condições. Servidores atuam como mensageiros cegos — transportam envelopes opacos sem jamais acessar o conteúdo.

#### 2. Rede de Nós Distribuídos
Em escala nacional, cada dispositivo pode operar como nó de uma rede overlay onde:
- Dispositivos validam identidades mutuamente sem autoridade central
- Envelopes roteiam-se com garantias criptográficas de origem e destinatário
- Dados sensíveis só circulam com identidade verificável e trilha de auditoria
- A internet permanece como transporte físico; a Malha é a camada lógica de soberania

> **Estas são possibilidades arquiteturais.** A implementação concreta depende de adoção, parcerias institucionais e acordos de governança que transcendem o código.

---

## 📚 Documentação

| Documento | Descrição |
|-----------|-----------|
| [Visão Geral](docs/visao-geral.md) | Arquitetura e objetivos |
| [Casos de Uso](docs/casos-uso.md) | Exemplos práticos por setor |
| [Guia de Uso](docs/guia-uso.md) | Fluxos principais passo a passo |
| [Configuração](docs/configuracao.md) | Todas as opções do `SDKConfig` |
| [API Reference](docs/api-reference.md) | Referência completa da API |
| [Segurança e Conformidade](docs/seguranca-conformidade.md) | LGPD, GDPR, PCI DSS |

---

## 📄 Licença

Copyright © 2026 Luan Gabriel Machado

Licenciado sob **GPL-3.0 license**

---

## 🔗 Links

- **Repositório**: [github.com/luangabriel/shield-sdk](https://github.com/luangabriel/shield-sdk)
- **NIST Post-Quantum Cryptography**: [csrc.nist.gov/projects/post-quantum-cryptography](https://csrc.nist.gov/projects/post-quantum-cryptography)
- **LGPD**: [gov.br/cidadania/pt-br/acesso-a-informacao/dados-abertos/lgpd](https://www.gov.br/cidadania/pt-br/acesso-a-informacao/dados-abertos/lgpd)

---

<p align="center">
  <strong>Seus dados são seus. Ponto.</strong>
</p>
