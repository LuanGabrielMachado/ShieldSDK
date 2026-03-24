# Shield SDK

**Sistema Híbrido Independente de Envio Livre de Dados**

SDK Kotlin/JVM para compartilhamento seguro de dados com consentimento granular e proteção criptográfica de nível pós-quântico. Funciona em Android, Spring Boot, Ktor e qualquer JVM — sem dependência de servidor, sem infraestrutura obrigatória.

![Build](https://img.shields.io/badge/build-passing-brightgreen?style=for-the-badge&logo=kotlin&logoColor=white)
![Tests](https://img.shields.io/badge/tests-173%20passing-brightgreen?style=for-the-badge&logo=junit5&logoColor=white)
![Coverage](https://img.shields.io/badge/coverage-70%25%2B-brightgreen?style=for-the-badge&logo=jacoco&logoColor=white)
![Kotlin](https://img.shields.io/badge/Kotlin-1.9.22-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white)
![JDK](https://img.shields.io/badge/JDK-17+-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![License](https://img.shields.io/badge/license-Apache%202.0-blue?style=for-the-badge)

![Post-Quantum](https://img.shields.io/badge/Post--Quantum-Kyber--768-blueviolet?style=for-the-badge&logo=atom&logoColor=white)
![Dilithium](https://img.shields.io/badge/Signature-Dilithium3-blueviolet?style=for-the-badge&logo=atom&logoColor=white)
![NIST](https://img.shields.io/badge/NIST-FIPS%20203%20%7C%20204-003087?style=for-the-badge&logo=nist&logoColor=white)
![KEM](https://img.shields.io/badge/KEM-ECDH--P256%20%2B%20Kyber--768-8A2BE2?style=for-the-badge)

![AES](https://img.shields.io/badge/Cipher-AES--256--GCM-red?style=for-the-badge&logo=letsencrypt&logoColor=white)
![HKDF](https://img.shields.io/badge/KDF-HKDF--SHA256-red?style=for-the-badge)
![Memory](https://img.shields.io/badge/Memory-Zeroization-critical?style=for-the-badge&logo=security&logoColor=white)
![AntiReplay](https://img.shields.io/badge/Anti--Replay-Protected-critical?style=for-the-badge)

![LGPD](https://img.shields.io/badge/LGPD-Compliant-009c3b?style=for-the-badge)
![GDPR](https://img.shields.io/badge/GDPR-Compliant-003399?style=for-the-badge)
![Consent](https://img.shields.io/badge/Consent-Granular-009c3b?style=for-the-badge)
![HarvestNow](https://img.shields.io/badge/Harvest%20Now%20Decrypt%20Later-Protected-8A2BE2?style=for-the-badge)

![Platform](https://img.shields.io/badge/Platform-Android%20%7C%20JVM%20%7C%20Spring%20%7C%20Ktor-orange?style=for-the-badge&logo=android&logoColor=white)
![BouncyCastle](https://img.shields.io/badge/BouncyCastle-1.77-yellow?style=for-the-badge)
![Audit](https://img.shields.io/badge/Security%20Audit-30+%20fixes-success?style=for-the-badge&logo=checkmarx&logoColor=white)

<svg viewBox="0 0 1000 780" xmlns="http://www.w3.org/2000/svg" font-family="'Segoe UI', system-ui, sans-serif">
  <defs>
    <linearGradient id="bg" x1="0" y1="0" x2="1" y2="1">
      <stop offset="0%" stop-color="#0d1117"/>
      <stop offset="100%" stop-color="#161b22"/>
    </linearGradient>
    <marker id="ab" markerWidth="8" markerHeight="6" refX="7" refY="3" orient="auto"><path d="M0,0 L8,3 L0,6 z" fill="#58a6ff"/></marker>
    <marker id="ag" markerWidth="8" markerHeight="6" refX="7" refY="3" orient="auto"><path d="M0,0 L8,3 L0,6 z" fill="#3fb950"/></marker>
    <marker id="ap" markerWidth="8" markerHeight="6" refX="7" refY="3" orient="auto"><path d="M0,0 L8,3 L0,6 z" fill="#bc8cff"/></marker>
    <marker id="ay" markerWidth="8" markerHeight="6" refX="7" refY="3" orient="auto"><path d="M0,0 L8,3 L0,6 z" fill="#d29922"/></marker>
    <marker id="ar" markerWidth="8" markerHeight="6" refX="7" refY="3" orient="auto"><path d="M0,0 L8,3 L0,6 z" fill="#ff7b72"/></marker>
    <filter id="s"><feDropShadow dx="0" dy="2" stdDeviation="5" flood-color="#000" flood-opacity="0.6"/></filter>
  </defs>

  <!-- BG -->
  <rect width="1000" height="780" fill="url(#bg)" rx="14"/>

  <!-- TITLE -->
  <text x="500" y="38" text-anchor="middle" fill="#f0f6fc" font-size="20" font-weight="700" letter-spacing="0.5">Shield SDK — Hybrid PQ Protocol</text>
  <text x="500" y="58" text-anchor="middle" fill="#8b949e" font-size="12">ECDH-P256 + Kyber-768  →  HKDF-SHA256  →  AES-256-GCM</text>

  <!-- ─────────────────────────────────────────────────────────────── -->
  <!-- COLUMN LEFT: x=30, width=270                                    -->
  <!-- COLUMN CENTER: x=365, width=270                                 -->
  <!-- COLUMN RIGHT: x=700, width=270                                  -->
  <!-- ─────────────────────────────────────────────────────────────── -->

  <!-- ── EMISSOR ── -->
  <rect x="30" y="76" width="270" height="48" rx="8" fill="#1f6feb" filter="url(#s)"/>
  <text x="165" y="96" text-anchor="middle" fill="#fff" font-size="12" font-weight="700">📱  EMISSOR</text>
  <text x="165" y="114" text-anchor="middle" fill="#cae8ff" font-size="11">userData + ShareSelection</text>

  <!-- ── RECEPTOR ── -->
  <rect x="700" y="76" width="270" height="48" rx="8" fill="#238636" filter="url(#s)"/>
  <text x="835" y="96" text-anchor="middle" fill="#fff" font-size="12" font-weight="700">🏛️  RECEPTOR</text>
  <text x="835" y="114" text-anchor="middle" fill="#c8e6c9" font-size="11">HybridRecipientKeyPair</text>

  <!-- ── BOX 1: KEY GENERATION (receptor) ── -->
  <rect x="700" y="152" width="270" height="84" rx="8" fill="#161b22" stroke="#238636" stroke-width="1.5"/>
  <text x="835" y="172" text-anchor="middle" fill="#3fb950" font-size="11" font-weight="700">① KEY GENERATION (receptor)</text>
  <text x="835" y="192" text-anchor="middle" fill="#8b949e" font-size="11">EC P-256 KeyPair (Keystore)</text>
  <text x="835" y="210" text-anchor="middle" fill="#8b949e" font-size="11">Kyber-768 KeyPair (BCPQC)</text>
  <text x="835" y="228" text-anchor="middle" fill="#8b949e" font-size="10">→ HybridRecipientPublicKey publicada</text>
  <!-- RECEPTOR → BOX1 -->
  <line x1="835" y1="124" x2="835" y2="152" stroke="#3fb950" stroke-width="1.5" marker-end="url(#ag)"/>

  <!-- ── BOX 2: ECDH EFÊMERO (emissor) ── -->
  <rect x="30" y="152" width="270" height="84" rx="8" fill="#161b22" stroke="#1f6feb" stroke-width="1.5"/>
  <text x="165" y="172" text-anchor="middle" fill="#58a6ff" font-size="11" font-weight="700">② ECDH EFÊMERO (emissor)</text>
  <text x="165" y="192" text-anchor="middle" fill="#8b949e" font-size="11">gera EC KeyPair efêmero</text>
  <text x="165" y="210" text-anchor="middle" fill="#8b949e" font-size="11">ECDH(ephPriv, recipientEcPub)</text>
  <text x="165" y="228" text-anchor="middle" fill="#8b949e" font-size="10">→ ecSecret: 32 bytes</text>
  <!-- EMISSOR → BOX2 -->
  <line x1="165" y1="124" x2="165" y2="152" stroke="#58a6ff" stroke-width="1.5" marker-end="url(#ab)"/>

  <!-- ── BOX 3: KYBER KEM (emissor) ── -->
  <rect x="30" y="262" width="270" height="84" rx="8" fill="#161b22" stroke="#8957e5" stroke-width="1.5"/>
  <text x="165" y="282" text-anchor="middle" fill="#bc8cff" font-size="11" font-weight="700">③ KYBER-768 KEM (emissor)</text>
  <text x="165" y="302" text-anchor="middle" fill="#8b949e" font-size="11">KyberKEM.encapsulate(kyberPub)</text>
  <text x="165" y="320" text-anchor="middle" fill="#8b949e" font-size="11">→ kyberSecret: 32 bytes</text>
  <text x="165" y="338" text-anchor="middle" fill="#8b949e" font-size="10">→ ciphertext: 1088 bytes (público)</text>
  <!-- BOX2 → BOX3 -->
  <line x1="165" y1="236" x2="165" y2="262" stroke="#8957e5" stroke-width="1.5" marker-end="url(#ap)"/>

  <!-- ── BOX 4: HKDF (center) ── -->
  <rect x="365" y="214" width="270" height="96" rx="8" fill="#161b22" stroke="#d29922" stroke-width="2"/>
  <text x="500" y="236" text-anchor="middle" fill="#e3b341" font-size="11" font-weight="700">④ HKDF-SHA256</text>
  <text x="500" y="256" text-anchor="middle" fill="#8b949e" font-size="11">ikm = ecSecret ‖ kyberSecret</text>
  <text x="500" y="274" text-anchor="middle" fill="#8b949e" font-size="11">salt = requestId  (binding único)</text>
  <text x="500" y="292" text-anchor="middle" fill="#8b949e" font-size="11">info = "shield-hybrid-pq-v1"</text>
  <text x="500" y="310" text-anchor="middle" fill="#e3b341" font-size="11" font-weight="600">→ sessionKey: 32 bytes 🔑</text>
  <!-- BOX2 → HKDF (seta diagonal do ecSecret) -->
  <path d="M 300 194 L 365 248" stroke="#d29922" stroke-width="1.5" fill="none" marker-end="url(#ay)"/>
  <!-- BOX3 → HKDF (seta diagonal do kyberSecret) -->
  <path d="M 300 310 L 365 294" stroke="#d29922" stroke-width="1.5" fill="none" marker-end="url(#ay)"/>

  <!-- ── BOX 5: AES-256-GCM ── -->
  <rect x="365" y="334" width="270" height="84" rx="8" fill="#161b22" stroke="#da3633" stroke-width="1.5"/>
  <text x="500" y="354" text-anchor="middle" fill="#ff7b72" font-size="11" font-weight="700">⑤ AES-256-GCM ENCRYPT</text>
  <text x="500" y="374" text-anchor="middle" fill="#8b949e" font-size="11">encrypt(payload, sessionKey, aad)</text>
  <text x="500" y="392" text-anchor="middle" fill="#8b949e" font-size="11">aad = len ‖ requestId ‖ recipientId</text>
  <text x="500" y="410" text-anchor="middle" fill="#8b949e" font-size="10">iv: 12 bytes    tag auth: 16 bytes</text>
  <!-- HKDF → AES -->
  <line x1="500" y1="310" x2="500" y2="334" stroke="#ff7b72" stroke-width="1.5" marker-end="url(#ar)"/>

  <!-- ── BOX 6: SIGN ── -->
  <rect x="30" y="374" width="270" height="70" rx="8" fill="#161b22" stroke="#58a6ff" stroke-width="1.5"/>
  <text x="165" y="394" text-anchor="middle" fill="#58a6ff" font-size="11" font-weight="700">⑥ ECDSA / DILITHIUM3 SIGN</text>
  <text x="165" y="414" text-anchor="middle" fill="#8b949e" font-size="11">sign(ciphertext ‖ metadata_sorted)</text>
  <text x="165" y="432" text-anchor="middle" fill="#8b949e" font-size="10">signerPublicKey viaja no envelope</text>
  <!-- BOX3 → BOX6 -->
  <line x1="165" y1="346" x2="165" y2="374" stroke="#58a6ff" stroke-width="1.5" marker-end="url(#ab)"/>

  <!-- ── BOX 7: DECAPSULATE (receptor) ── -->
  <rect x="700" y="262" width="270" height="96" rx="8" fill="#161b22" stroke="#8957e5" stroke-width="1.5"/>
  <text x="835" y="282" text-anchor="middle" fill="#bc8cff" font-size="11" font-weight="700">⑦ DECAPSULATE (receptor)</text>
  <text x="835" y="302" text-anchor="middle" fill="#8b949e" font-size="11">ECDH(privEc, ecEphPub) → ecSecret</text>
  <text x="835" y="320" text-anchor="middle" fill="#8b949e" font-size="11">Kyber.decapsulate(privKyber, CT)</text>
  <text x="835" y="338" text-anchor="middle" fill="#8b949e" font-size="11">→ kyberSecret</text>
  <text x="835" y="356" text-anchor="middle" fill="#e3b341" font-size="11" font-weight="600">HKDF → mesma sessionKey 🔑</text>
  <!-- BOX1 → BOX7 -->
  <line x1="835" y1="236" x2="835" y2="262" stroke="#8957e5" stroke-width="1.5" marker-end="url(#ap)"/>

  <!-- ── BOX 8: VALIDATE + DECRYPT ── -->
  <rect x="700" y="386" width="270" height="70" rx="8" fill="#161b22" stroke="#3fb950" stroke-width="1.5"/>
  <text x="835" y="406" text-anchor="middle" fill="#3fb950" font-size="11" font-weight="700">⑧ VALIDATE + DECRYPT</text>
  <text x="835" y="426" text-anchor="middle" fill="#8b949e" font-size="11">verify(sig, ciphertext, metadata)</text>
  <text x="835" y="444" text-anchor="middle" fill="#8b949e" font-size="11">AES-GCM.decrypt → userData ✓</text>
  <!-- BOX7 → BOX8 -->
  <line x1="835" y1="358" x2="835" y2="386" stroke="#3fb950" stroke-width="1.5" marker-end="url(#ag)"/>

  <!-- ─────────────────────────────────────────────────────────────── -->
  <!-- ENVELOPE                                                        -->
  <!-- ─────────────────────────────────────────────────────────────── -->
  <rect x="30" y="472" width="940" height="138" rx="10" fill="#161b22" stroke="#d29922" stroke-width="2" filter="url(#s)"/>
  <text x="500" y="494" text-anchor="middle" fill="#e3b341" font-size="13" font-weight="700">📦  SecureDataEnvelope</text>

  <!-- 7 cells equally spaced inside envelope -->
  <!-- cell width: (940-60)/7 = ~125.7 → use 124, gaps 6 -->
  <!-- start x = 36, y = 504 -->

  <rect x="36"   y="504" width="124" height="46" rx="5" fill="#21262d" stroke="#30363d"/>
  <text x="98"   y="521" text-anchor="middle" fill="#8b949e" font-size="10">sealedPayload</text>
  <text x="98"   y="540" text-anchor="middle" fill="#ff7b72" font-size="10" font-weight="600">AES-256-GCM</text>

  <rect x="166"  y="504" width="124" height="46" rx="5" fill="#21262d" stroke="#30363d"/>
  <text x="228"  y="521" text-anchor="middle" fill="#8b949e" font-size="10">kemEncapsulation</text>
  <text x="228"  y="540" text-anchor="middle" fill="#bc8cff" font-size="10" font-weight="600">ecEphPub + kyberCT</text>

  <rect x="296"  y="504" width="124" height="46" rx="5" fill="#21262d" stroke="#30363d"/>
  <text x="358"  y="521" text-anchor="middle" fill="#8b949e" font-size="10">userSignature</text>
  <text x="358"  y="540" text-anchor="middle" fill="#58a6ff" font-size="10" font-weight="600">ECDSA / Dilithium3</text>

  <rect x="426"  y="504" width="124" height="46" rx="5" fill="#21262d" stroke="#30363d"/>
  <text x="488"  y="521" text-anchor="middle" fill="#8b949e" font-size="10">signerPublicKey</text>
  <text x="488"  y="540" text-anchor="middle" fill="#58a6ff" font-size="10" font-weight="600">X.509 Base64</text>

  <rect x="556"  y="504" width="124" height="46" rx="5" fill="#21262d" stroke="#30363d"/>
  <text x="618"  y="521" text-anchor="middle" fill="#8b949e" font-size="10">metadata</text>
  <text x="618"  y="540" text-anchor="middle" fill="#e3b341" font-size="10" font-weight="600">signed · v1.2</text>

  <rect x="686"  y="504" width="124" height="46" rx="5" fill="#21262d" stroke="#30363d"/>
  <text x="748"  y="521" text-anchor="middle" fill="#8b949e" font-size="10">identityFingerprint</text>
  <text x="748"  y="540" text-anchor="middle" fill="#3fb950" font-size="10" font-weight="600">SHA-256 Base64</text>

  <rect x="816"  y="504" width="148" height="46" rx="5" fill="#21262d" stroke="#30363d"/>
  <text x="890"  y="521" text-anchor="middle" fill="#8b949e" font-size="10">deviceBinding</text>
  <text x="890"  y="540" text-anchor="middle" fill="#3fb950" font-size="10" font-weight="600">hardware-backed</text>

  <text x="500" y="598" text-anchor="middle" fill="#484f58" font-size="10">requestId  ·  recipientId  ·  createdAtEpochSeconds  ·  selectedFields</text>

  <!-- Arrows into envelope -->
  <!-- BOX6 → envelope left -->
  <line x1="165" y1="444" x2="165" y2="472" stroke="#d29922" stroke-width="1.5" marker-end="url(#ay)"/>
  <!-- BOX5 → envelope center -->
  <line x1="500" y1="418" x2="500" y2="472" stroke="#d29922" stroke-width="1.5" marker-end="url(#ay)"/>
  <!-- BOX8 → envelope right (curved) -->
  <path d="M 835 456 Q 835 465 835 472" stroke="#d29922" stroke-width="1.5" fill="none" marker-end="url(#ay)"/>

  <!-- Dashed line: envelope sends KEM to receptor -->
  <path d="M 228 504 Q 228 460 835 456" stroke="#8957e5" stroke-width="1.2" fill="none" stroke-dasharray="5,4"/>
  <text x="530" y="452" text-anchor="middle" fill="#8957e5" font-size="10">kemEncapsulation  →  receptor</text>

  <!-- ─────────────────────────────────────────────────────────────── -->
  <!-- SECURITY BADGES                                                 -->
  <!-- ─────────────────────────────────────────────────────────────── -->
  <rect x="30"   y="628" width="170" height="28" rx="6" fill="#21262d" stroke="#30363d"/>
  <text x="115"  y="647" text-anchor="middle" fill="#3fb950" font-size="11">✅  Anti-Replay Guard</text>

  <rect x="210"  y="628" width="190" height="28" rx="6" fill="#21262d" stroke="#30363d"/>
  <text x="305"  y="647" text-anchor="middle" fill="#bc8cff" font-size="11">🔮  Harvest Now Protected</text>

  <rect x="410"  y="628" width="180" height="28" rx="6" fill="#21262d" stroke="#30363d"/>
  <text x="500"  y="647" text-anchor="middle" fill="#e3b341" font-size="11">🧹  Memory Zeroization</text>

  <rect x="600"  y="628" width="185" height="28" rx="6" fill="#21262d" stroke="#30363d"/>
  <text x="692"  y="647" text-anchor="middle" fill="#58a6ff" font-size="11">📋  LGPD / GDPR Consent</text>

  <rect x="795"  y="628" width="175" height="28" rx="6" fill="#21262d" stroke="#30363d"/>
  <text x="882"  y="647" text-anchor="middle" fill="#ff7b72" font-size="11">🔒  AAD Context Binding</text>

  <!-- ─────────────────────────────────────────────────────────────── -->
  <!-- NIST LABELS                                                     -->
  <!-- ─────────────────────────────────────────────────────────────── -->
  <rect x="30"   y="672" width="300" height="26" rx="6" fill="#21262d" stroke="#30363d"/>
  <text x="180"  y="689" text-anchor="middle" fill="#8b949e" font-size="10">NIST FIPS 203 (Kyber/ML-KEM)  ·  FIPS 204 (Dilithium/ML-DSA)</text>

  <rect x="340"  y="672" width="320" height="26" rx="6" fill="#21262d" stroke="#30363d"/>
  <text x="500"  y="689" text-anchor="middle" fill="#8b949e" font-size="10">RFC 5869 (HKDF)  ·  NIST SP 800-38D (AES-GCM)  ·  SEC1 (ECDH)</text>

  <rect x="670"  y="672" width="300" height="26" rx="6" fill="#21262d" stroke="#30363d"/>
  <text x="820"  y="689" text-anchor="middle" fill="#8b949e" font-size="10">BouncyCastle 1.77  ·  JDK 21  ·  Apache 2.0</text>

  <!-- watermark -->
  <text x="500" y="748" text-anchor="middle" fill="#21262d" font-size="11">Shield SDK · github.com/LuanGabrielMachado/shield-sdk</text>
</svg>

---

## Por que o Shield SDK existe

Compartilhar dados sensíveis entre sistemas hoje significa escolher entre conveniência e segurança. APIs REST expõem dados em trânsito a qualquer intermediário. Criptografia clássica ponto-a-ponto não resiste a computadores quânticos. Sistemas de consentimento vivem em camadas de aplicação, fora da criptografia.

O Shield resolve os três problemas ao mesmo tempo:

- **O dado nunca viaja em claro** — a criptografia acontece no dispositivo do usuário, antes de qualquer transmissão.
- **O receptor é o único que pode ler** — a chave de sessão é derivada via KEM pós-quântico, nunca existe como um valor transportado.
- **O consentimento faz parte da criptografia** — campos não autorizados são descartados antes de encriptar, não depois.

---

## Segurança

### Protocolo híbrido pós-quântico

O Shield usa um protocolo de duas camadas que resiste tanto a adversários clássicos quanto a futuros computadores quânticos.

**Camada de transporte da chave — ECDH-P256 + Kyber-768 → HKDF-SHA256:**

```
ecSecret    = ECDH(ephemeral_P256_priv, receptor_ec_pub)     → 32 bytes
kyberSecret = Kyber768.encapsulate(receptor_kyber_pub)       → 32 bytes
sessionKey  = HKDF-SHA256(ecSecret ‖ kyberSecret,
                           salt = requestId,
                           info = "shield-hybrid-pq-v1")     → 32 bytes
```

A chave final é comprometida somente se **ambos** os algoritmos forem quebrados simultaneamente. ECDH-P256 é vulnerável ao algoritmo de Shor em computador quântico. Kyber-768 (NIST FIPS 203 / ML-KEM-768) não é. A combinação garante proteção contra *harvest now, decrypt later* — onde um adversário captura dados hoje para decriptar quando tiver capacidade quântica.

**Camada de payload — AES-256-GCM ou ChaCha20-Poly1305:**

O payload é encriptado com a `sessionKey`. O AAD `requestId|recipientId` é passado para `Cipher.updateAAD()` — o GCM autentica o contexto junto com o ciphertext. Mover o ciphertext para outro envelope ou alterar o `recipientId` invalida a tag.

**Assinatura — ECDSA SHA256withECDSA (ou Dilithium3):**

Ciphertext + metadata sorted canonicamente é assinado com ECDSA. A chave pública do assinante viaja no envelope — verificação funciona offline, sem estado, em qualquer sessão. Dilithium3 (NIST FIPS 204 / ML-DSA-65) está disponível como alternativa totalmente pós-quântica para a assinatura.

### Garantias do envelope

| Propriedade | Mecanismo | O que detecta |
|---|---|---|
| **Confidencialidade** | AES-256-GCM / ChaCha20-Poly1305 | Leitura por terceiros |
| **Integridade do payload** | Tag GCM 128 bits | Qualquer alteração no ciphertext |
| **Binding de contexto** | AAD `requestId\|recipientId` | Envelope movido para outro receptor |
| **Autenticidade** | ECDSA sobre ciphertext + metadata | Forja de envelope |
| **Integridade do metadata** | Assinatura cobre metadata sorted | Adulteração de `expiresAt`, `legalBasis` |
| **Anti-replay** | `ReplayGuard` com janela de 1h | Reenvio do mesmo envelope |
| **Resistência quântica (KEM)** | Kyber-768 + ECDH-P256 via HKDF | Adversário com computador quântico |
| **Resistência quântica (assinatura)** | Dilithium3 (opcional) | Forja via algoritmo de Shor |

### O que um atacante encontra

| Tentativa | Resultado |
|---|---|
| Interceptar o envelope | Ciphertext opaco — sem chave Kyber privada, a `sessionKey` não pode ser derivada |
| Alterar qualquer byte do ciphertext | `AEADBadTagException` — tag GCM inválida |
| Alterar `recipientId` | `AEADBadTagException` — AAD diferente do momento da criação |
| Alterar `expiresAt` no metadata | ECDSA inválida — metadata faz parte do material assinado |
| Reenviar o mesmo envelope | `SecurityException` — `ReplayGuard` registrou o `requestId` |
| Chave de decriptografia errada | `SecurityException` — checksum falha antes de tentar GCM |
| Par Kyber errado no decrypt | GCM falha — `sessionKey` diferente produz ciphertext indecifrável |

### Gerenciamento de memória

Materiais criptográficos são zerados imediatamente após o uso:

- `ecSecret.fill(0)` e `kyberSecret.fill(0)` em bloco `finally` — garantido mesmo em exceção
- `sessionKey.fill(0)` em `finally` no `decryptEnvelopePQ`
- `payloadBytes.fill(0)` após encriptar
- `decryptedBytes.fill(0)` após deserializar

---

## O Envelope

O `SecureDataEnvelope` é a unidade de troca. É um `data class` serializável — pode ser transmitido por HTTP, fila, Bluetooth, NFC, arquivo ou qualquer canal. Nenhum intermediário precisa entender sua estrutura para transportá-lo.

```
SecureDataEnvelope
├── requestId                      UUID único — salt do HKDF e do anti-replay
├── recipientId                    Identificador do receptor — parte do AAD
├── createdAtEpochSeconds          Timestamp único de criação (capturado uma vez)
├── identityKeyFingerprint         SHA-256 da chave pública ECDSA do emissor
├── deviceBindingFingerprint       SHA-256("device|" + identityFingerprint)
├── selectedFields                 Campos consentidos — verificados vs payload no decrypt
│
├── sealedPayload
│   ├── dataKeyVersion             Versão da chave (suporte a rotação)
│   ├── dataKeyChecksum            SHA-256(sessionKey)[0..8] — verificado antes do decrypt
│   ├── createdAt                  Mesmo valor de createdAtEpochSeconds
│   ├── associatedDataDigest       SHA-256(requestId|recipientId) — observabilidade
│   └── payload
│       ├── iv                     12 bytes aleatórios (SecureRandom por envelope)
│       └── ciphertext             AES-256-GCM(json, sessionKey, aad=requestId|recipientId)
│
├── userSignatureBase64            ECDSA(ciphertext ‖ "||" ‖ metadata_sorted)
├── signerPublicKeyBase64          Chave pública X.509 DER — verificação offline
│
├── encryptedDataKeyBase64         RSA-OAEP(sessionKey) — modo clássico (null no PQ)
│
├── kemEncapsulation               Materiais públicos do KEM — modo PQ
│   ├── ecEphemeralPublicKeyBytes  Chave pública EC efêmera P-256 (X.509 DER)
│   ├── kyberCiphertextBytes       Ciphertext Kyber-768 (1088 bytes)
│   └── kyberParameterSet          "kyber768"
│
└── metadata                       Público, auditável e assinado
    ├── consentPurpose
    ├── legalBasis
    ├── expiresAt
    ├── protocolVersion            "1.1"
    ├── encryptionAlgorithm        "AES-256-GCM" ou "ChaCha20-Poly1305"
    ├── signatureAlgorithm         "SHA256withECDSA"
    └── kemAlgorithm               "ECDH-P256+Kyber768-HKDF-SHA256"
```

Nenhum dado do usuário aparece fora de `sealedPayload.payload.ciphertext`. O `metadata` é público, auditável e assinado — qualquer adulteração invalida o ECDSA.

---

## Instalação

```kotlin
// build.gradle.kts
dependencies {
    implementation("io.Shield:Shield-sdk:1.0.0")
}
```

```xml
<!-- pom.xml -->
<dependency>
    <groupId>io.Shield</groupId>
    <artifactId>Shield-sdk</artifactId>
    <version>1.0.0</version>
</dependency>
```

**Requisitos:** JVM 17+, Kotlin 1.9.22+. Android API 24+. BouncyCastle 1.77 incluído via Maven Central.

### Build e testes

```bash
# Clonar e rodar os testes (requer Java 17+ e internet na primeira execução)
git clone https://github.com/luangabriel/shield-sdk
cd shield-sdk
./run-tests.sh          # testes completos
./run-verify.sh         # testes + relatório de cobertura
```

Relatórios em `shared-models/build/reports/tests/test/index.html`.

---

## Uso

### Modo recomendado — protocolo híbrido PQ

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
    recipientKey = recipientKp.publicKey   // só a chave pública — emissor nunca toca a privada
)
// envelope é serializável — envie por qualquer canal

// ── Receptor valida e decripta ────────────────────────────────────────────
sdk.validateAndConsumeEnvelope(envelope)   // valida + registra no anti-replay

val data = sdk.decryptEnvelopePQ(envelope, recipientKp)
// data = {"name" to "Ana Costa", "cpf" to "123.456.789-00"}
// Somente campos consentidos, em lowercase, sem exceção
```

### DSL — sintaxe fluente

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

### Configuração completa

```kotlin
import io.Shield.audit.FileAuditLogger
import io.Shield.security.EmissionRateLimiter
import java.io.File

val sdk = ShieldSDK.initialize(
    SDKConfigBuilder()
        .encryptionStrategy("hybrid-pq")           // ou "chacha20" para hardware sem AES-NI
        .defaultExpirySeconds(3600)
        .enableAuditLogging(true)
        .auditLogger(FileAuditLogger(File("/var/log/shield")))
        .emissionRateLimiter(EmissionRateLimiter(  // rate limiting por identidade
            maxPerWindow  = 100,
            windowSeconds = 60
        ))
        .build()
)
```

---

## Adaptadores de plataforma

### Android

```kotlin
val adapter = AndroidAdapter.create(applicationContext)
val sdk     = adapter.initializeSDK()
val kp      = sdk.generateRecipientKeyPair()

// Gate biométrico + envelope PQ em uma chamada
val envelope = adapter.createEnvelopePQWithBiometricGate(
    activity       = this,
    sdk            = sdk,
    userData       = userData,
    consent        = consent,
    recipientId    = "parceiro",
    recipientKey   = kp.publicKey,
    biometricTitle = "Confirmar compartilhamento seguro"
)

// Key Attestation — prova criptográfica de hardware binding
val attestation = KeyAttestationHelper().generateAttestedKeyPair(
    keyAlias  = "shield_signer_v1",
    challenge = serverChallenge        // nonce fresco do servidor
)
// attestation.certificateChainBase64 → enviar ao servidor para verificação
```

### Spring Boot

```yaml
shield:
  encryption.strategy: hybrid-pq
  default.expiry.seconds: 3600
  audit.logging.enabled: true
```

```kotlin
@Service
class DocumentoService(private val shieldService: ShieldService) {

    fun compartilhar(dados: Map<String, String>, recipientKey: HybridRecipientPublicKey) =
        shieldService.createSecureEnvelopePQ(dados, consent, "receptor", recipientKey)

    fun receber(envelope: SecureDataEnvelope, kp: HybridRecipientKeyPair) =
        shieldService.decryptEnvelopePQ(envelope, kp)
}
```

### Ktor

```kotlin
fun Application.module() {
    installShield { encryptionStrategy = "hybrid-pq" }

    routing {
        post("/compartilhar") {
            val envelope = call.createSecureEnvelopePQ(dados, consent, "dest", recipientKey)
            call.respond(envelope)
        }
        post("/receber") {
            val data = call.decryptEnvelopePQ(envelope, recipientKp)
            call.respond(data)
        }
    }
}
```

---

## Camadas de segurança

### Camada 1 — Fundação

| Correção | O que resolve |
|---|---|
| Timestamp único por envelope | `createdAt` e `createdAtEpochSeconds` do mesmo `nowEpoch` — sem race condition |
| Comparação constant-time | `MessageDigest.isEqual()` no checksum — fecha timing attack |
| Metadata assinado | `sign(ciphertext ‖ metadata_sorted)` — adulteração de `expiresAt` invalida ECDSA |
| Limite de 64KB no payload | `require(payloadBytes.size <= 65536)` — protege receptor contra OOM |

### Camada 2 — Robustez

| Correção | O que resolve |
|---|---|
| `SecureRandom.getInstanceStrong()` no ECDSA | Nonce efêmero com entropia máxima da plataforma |
| `selectedFields` verificado vs payload | Adulteração da lista de campos declarados é detectada no decrypt |
| `normalizeKey` fail-fast | Chave de tamanho errado lança `IllegalArgumentException` imediato |
| Expiração mínima de 60s | `expiresAt` deve ser no futuro com folga — receptor tem tempo para validar |

### Camada 3 — Profundidade

| Componente | Função |
|---|---|
| `SigningKeyRotationManager` | Rotação atômica de par ECDSA com janela de transição configurável |
| `DilithiumSignatureService` | Assinatura Dilithium3 (NIST FIPS 204) — fecha o ponto ECDSA vulnerável ao Shor |
| `EmissionRateLimiter` | Janela deslizante por identidade — bloqueia emissão em loop |
| `KeyAttestationHelper` | Android Key Attestation — prova de hardware binding via TEE/StrongBox |

---

## Auditoria

```kotlin
val logger = InMemoryAuditLogger()
val sdk    = ShieldSDK.initialize(SDKConfigBuilder().auditLogger(logger).build())

sdk.createSecureEnvelope(...)
sdk.validateEnvelope(...)

logger.events.forEach { println("${it.type} | req=${it.requestId.take(8)} | ${it.success}") }
// ENVELOPE_CREATED | req=a3f8b1c2 | true
// ENVELOPE_VALIDATED | req=a3f8b1c2 | true
```

| Implementação | Comportamento |
|---|---|
| `ConsoleAuditLogger` | stdout com timestamp ISO-8601 |
| `FileAuditLogger` | `shield-audit-YYYY-MM-DD.log`, rotacionado por dia |
| `NoOpAuditLogger` | Descarta tudo — padrão sem configuração |
| `InMemoryAuditLogger` | Acumula em memória — para testes |

---

## Conformidade regulatória

| Requisito | Como o Shield atende |
|---|---|
| LGPD Art. 46 — medidas de segurança | AES-256-GCM + Kyber-768, acima dos mínimos |
| LGPD Art. 7 — consentimento | `ShareSelection` com campos, propósito, base legal e expiração |
| GDPR Art. 32 — segurança do tratamento | Criptografia forte, minimização, auditoria |
| GDPR Art. 17 — direito ao esquecimento | Expiração configrável por envelope |
| PCI DSS Req. 3-4 — proteção de dados | Criptografia em trânsito e controle de acesso |

---

## Precisa de servidor?

Não. O SDK funciona completamente offline — emissor e receptor derivam a chave de sessão independentemente a partir do `KemEncapsulation` público no envelope. Nenhuma chamada de rede acontece durante criação ou decriptografia.

O que um servidor pode adicionar opcionalmente: registro de chaves públicas para descoberta, transporte de envelopes opacos, verificação server-side de Key Attestation.

---

## Precisa ser open source para usar?

**Não.** A licença Apache 2.0 permite uso comercial, modificação e distribuição proprietária sem nenhuma obrigação de abrir o código do seu produto. As únicas exigências são manter os avisos de copyright do Shield SDK e não usar os nomes dos autores para endossar produtos derivados.

Você pode incluir o Shield SDK num app comercial fechado, SaaS, solução enterprise ou qualquer produto proprietário — sem abrir uma linha do seu código. O que é open source é o SDK em si.

---

## Exemplos por setor

| Setor | Casos |
|---|---|
| [`exemplos/Financeiro/`](exemplos/Financeiro/) | Open Banking, análise de crédito, declaração IR |
| [`exemplos/Saúde/`](exemplos/Saúde/) | Prontuário eletrônico, encaminhamento, plano de saúde |
| [`exemplos/Governo/`](exemplos/Governo/) | Benefício social, IR, TSE, matrícula escolar |
| [`exemplos/Java/`](exemplos/Java/) | Interoperabilidade Java completa |

---

## Documentação

| Documento | Descrição |
|---|---|
| [Visão Geral](docs/visao-geral.md) | Arquitetura e objetivos |
| [Configuração](docs/configuracao.md) | Todas as opções do `SDKConfig` |
| [Guia de Uso](docs/guia-uso.md) | Fluxos principais passo a passo |
| [Segurança e Conformidade](docs/seguranca-conformidade.md) | LGPD, GDPR, PCI DSS |
| [API Reference](docs/api-reference.md) | Referência completa da API |
| [Módulos](docs/modulos/) | Documentação interna de cada módulo |

---

## Licença

Copyright 2026 Luan Gabriel Machado. Licenciado sob [Apache License 2.0](LICENSE).

> Apache 2.0 permite uso comercial, modificação e distribuição sem obrigação de open source no produto final.
