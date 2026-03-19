# SDK Core

O módulo SDK Core é o ponto central do Shield SDK, fornecendo a interface principal para os desenvolvedores. Ele coordena os outros módulos e fornece uma API simples e poderosa para criar, validar e gerenciar envelopes de dados seguros.

## Componentes

### ShieldSDK

Classe principal do SDK que fornece a interface para todas as funcionalidades:

- `initialize(config: SDKConfig)`: Inicializa o SDK com a configuração especificada
- `getInstance()`: Obtém a instância singleton do SDK
- `createSecureEnvelope(...)`: Cria um envelope de dados seguro
- `validateEnvelope(...)`: Valida um envelope de dados recebido
- `decryptEnvelope(...)`: Decodifica e descriptografa os dados de um envelope seguro
- `createKeyHierarchySnapshot(...)`: Cria um snapshot da hierarquia de chaves para auditoria

## Arquitetura

### Padrão Singleton Thread-Safe

```kotlin
class ShieldSDK private constructor(
    private val config: SDKConfig,
    private val encryptionService: EncryptionService,
    private val sessionManager: SessionManager
) {
    companion object {
        @Volatile
        private var INSTANCE: ShieldSDK? = null

        private val LOCK = Any()

        fun initialize(config: SDKConfig): ShieldSDK {
            return INSTANCE ?: synchronized(LOCK) {
                INSTANCE ?: ShieldSDK(
                    config = config,
                    encryptionService = HybridEncryptionService(),
                    sessionManager = SessionManager(HybridEncryptionService())
                ).also { INSTANCE = it }
            }
        }

        fun getInstance(): ShieldSDK {
            return INSTANCE ?: throw IllegalStateException(
                "SDK não foi inicializado. Chame initialize() primeiro."
            )
        }
    }
}
```

## Uso

### Inicialização do SDK

```kotlin
import io.Shield.config.SDKConfigBuilder
import io.Shield.sdk.ShieldSDK

// 1. Criar configuração
val config = SDKConfigBuilder()
    .encryptionStrategy("hybrid-pq")
    .defaultExpirySeconds(3600)
    .enableAuditLogging(true)
    .timeoutMilliseconds(30000)
    .build()

// 2. Inicializar o SDK
val sdk = ShieldSDK.initialize(config)

// 3. Obter instância (opcional, já que initialize retorna a instância)
val secureSdk = ShieldSDK.getInstance()
```

### Criação de Envelope Seguro

```kotlin
import io.Shield.models.share.ShareSelection

// Dados do usuário
val userData = mapOf(
    "name" to "João Silva",
    "email" to "joao.silva@example.com",
    "cpf" to "12345678900"
)

// Consentimento do usuário
val consent = ShareSelection(
    fields = listOf("name", "email"),
    contextId = "empresa-parceira-123",
    purpose = "verificacao-conta",
    legalBasis = "consentimento"
)

// Criar envelope seguro
val envelope = secureSdk.createSecureEnvelope(
    userData = userData,
    consent = consent,
    recipientId = "empresa-parceira-123"
)

println("Envelope criado com ID: ${envelope.requestId}")
```

### Validação de Envelope

```kotlin
// Validar envelope recebido
val isValid = secureSdk.validateEnvelope(envelope)

if (isValid) {
    println("Envelope é válido e pode ser processado com segurança")
} else {
    println("Envelope inválido - não deve ser processado")
}
```

### Descriptografia de Dados

```kotlin
// Supondo que você tenha a chave de descriptografia
val decryptionKey = getDecryptionKey() // Função que obtém a chave

try {
    val decryptedData = secureSdk.decryptEnvelope(envelope, decryptionKey)
    println("Dados descriptografados: $decryptedData")
} catch (e: Exception) {
    println("Falha ao descriptografar envelope: ${e.message}")
}
```

## Integração com Outros Módulos

### Com o Módulo Config

```kotlin
class ShieldSDK(
    private val config: SDKConfig, // Recebe configuração do módulo Config
    private val encryptionService: EncryptionService,
    private val sessionManager: SessionManager
) {
    // Usa configurações para determinar comportamento
    fun createSecureEnvelope(...): SecureDataEnvelope {
        // Usa configurações como tempo de expiração padrão
        val expiryTime = config.defaultExpirySeconds
        // ...
    }
}
```

### Com o Módulo Crypto

```kotlin
class ShieldSDK(
    private val config: SDKConfig,
    private val encryptionService: EncryptionService, // Do módulo Crypto
    private val sessionManager: SessionManager
) {
    // Usa serviços de criptografia para operações seguras
}
```

### Com o Módulo Protocols

```kotlin
class ShieldSDK(
    private val config: SDKConfig,
    private val encryptionService: EncryptionService,
    private val sessionManager: SessionManager // Do módulo Protocols
) {
    // Delega operações de sessão para o SessionManager
    fun createSecureEnvelope(...) = sessionManager.createSecureSession(...)
    fun validateEnvelope(...) = sessionManager.validateSession(...)
    fun decryptEnvelope(...) = sessionManager.decryptEnvelope(...)
}
```

### Com o Módulo Models

```kotlin
import io.Shield.models.share.ShareSelection
import io.Shield.models.share.SecureDataEnvelope
import io.Shield.models.key.KeyHierarchySnapshot

// O SDK Core trabalha com os modelos de dados definidos no módulo Models
```

## Padrões de Projeto Implementados

### Singleton Thread-Safe

```kotlin
companion object {
    @Volatile
    private var INSTANCE: ShieldSDK? = null

    private val LOCK = Any()

    fun initialize(config: SDKConfig): ShieldSDK {
        return INSTANCE ?: synchronized(LOCK) {
            INSTANCE ?: createInstance(config).also { INSTANCE = it }
        }
    }

    private fun createInstance(config: SDKConfig): ShieldSDK {
        val encryptionService = when (config.encryptionStrategy) {
            "chacha20" -> ChaCha20EncryptionService()
            else -> HybridEncryptionService()
        }
        return ShieldSDK(
            config = config,
            encryptionService = encryptionService,
            sessionManager = SessionManager(encryptionService)
        )
    }
}
```

### Injeção de Dependências

```kotlin
class ShieldSDK(
    private val config: SDKConfig,
    private val encryptionService: EncryptionService,
    private val sessionManager: SessionManager
) {
    // Dependências injetadas no construtor
}
```

## Segurança

### Inicialização Segura

```kotlin
fun initialize(config: SDKConfig): ShieldSDK {
    // Validar configuração antes de criar instância
    config.validate()

    return INSTANCE ?: synchronized(LOCK) {
        INSTANCE ?: ShieldSDK(
            config = config,
            encryptionService = createEncryptionService(config.encryptionStrategy),
            sessionManager = SessionManager(createEncryptionService(config.encryptionStrategy))
        ).also { INSTANCE = it }
    }
}

private fun createEncryptionService(strategy: String): EncryptionService {
    return when (strategy) {
        "chacha20" -> ChaCha20EncryptionService()
        "hybrid-pq" -> HybridEncryptionService()
        else -> HybridEncryptionService() // Padrão seguro
    }
}
```

### Tratamento de Erros Seguro

```kotlin
fun createSecureEnvelope(
    userData: Map<String, String>,
    consent: ShareSelection,
    recipientId: String
): SecureDataEnvelope {
    try {
        // Validar entradas
        validateInputs(userData, consent, recipientId)

        // Criar envelope
        return sessionManager.createSecureSession(
            userData = userData,
            consent = consent,
            recipientId = recipientId,
            identityKeyFingerprint = generateIdentityKeyFingerprint(),
            deviceBindingFingerprint = generateDeviceBindingFingerprint()
        )
    } catch (e: SecurityException) {
        // Não expor detalhes sensíveis
        throw SecurityException("Falha na criação do envelope seguro")
    } catch (e: Exception) {
        // Logar erro sem expor dados sensíveis
        logError("Erro ao criar envelope: ${e.javaClass.simpleName}")
        throw e
    }
}

private fun validateInputs(
    userData: Map<String, String>,
    consent: ShareSelection,
    recipientId: String
) {
    require(userData.isNotEmpty()) { "Dados do usuário não podem estar vazios" }
    require(consent.fields.isNotEmpty()) { "Campos de consentimento não podem estar vazios" }
    require(recipientId.isNotBlank()) { "ID do destinatário não pode estar vazio" }
}
```

## Desempenho

### Cache de Instâncias

```kotlin
class ShieldSDK(
    private val config: SDKConfig,
    private val encryptionService: EncryptionService,
    private val sessionManager: SessionManager
) {
    // Instâncias são criadas uma vez e reutilizadas
    // Isso melhora o desempenho em operações repetidas
}
```

### Operações Assíncronas (quando apropriado)

```kotlin
// Exemplo de extensão para operações assíncronas
suspend fun createSecureEnvelopeAsync(
    userData: Map<String, String>,
    consent: ShareSelection,
    recipientId: String
): SecureDataEnvelope = withContext(Dispatchers.Default) {
    createSecureEnvelope(userData, consent, recipientId)
}
```

## Extensibilidade

### Interface Clara para Extensão

```kotlin
// O SDK Core fornece uma interface clara que pode ser estendida
interface SDKOperations {
    fun createSecureEnvelope(
        userData: Map<String, String>,
        consent: ShareSelection,
        recipientId: String
    ): SecureDataEnvelope

    fun validateEnvelope(envelope: SecureDataEnvelope): Boolean

    fun decryptEnvelope(
        envelope: SecureDataEnvelope,
        decryptionKey: ByteArray
    ): Map<String, String>
}

class ShieldSDK(
    private val config: SDKConfig,
    private val encryptionService: EncryptionService,
    private val sessionManager: SessionManager
) : SDKOperations {
    // Implementação dos métodos
}
```

## Configuração Dinâmica

### Atualização de Configuração (onde suportado)

```kotlin
class ShieldSDK(
    private val config: SDKConfig,
    private val encryptionService: EncryptionService,
    private val sessionManager: SessionManager
) {
    // Método para atualizar configurações em tempo de execução (se necessário)
    fun updateConfig(newConfig: SDKConfig) {
        // Validar nova configuração
        newConfig.validate()

        // Atualizar configuração (implementação específica)
        // Isso pode exigir recreação de alguns componentes
    }
}
```

## Melhores Práticas

### 1. Inicialização Única

```kotlin
class MyApp : Application() {
    override fun onCreate() {
        super.onCreate()

        // Inicializar SDK uma vez durante o ciclo de vida do aplicativo
        val config = SDKConfigBuilder()
            .encryptionStrategy("hybrid-pq")
            .enableAuditLogging(true)
            .build()

        ShieldSDK.initialize(config)
    }
}
```

### 2. Tratamento de Erros Adequado

```kotlin
class ServiceUsingSDK {
    private val sdk = ShieldSDK.getInstance()

    fun safeCreateEnvelope(userData: Map<String, String>, consent: ShareSelection): Result<String> {
        return try {
            val envelope = sdk.createSecureEnvelope(
                userData = userData,
                consent = consent,
                recipientId = "default-recipient"
            )
            Result.success(envelope.requestId)
        } catch (e: IllegalStateException) {
            // SDK não inicializado
            Result.failure(e)
        } catch (e: SecurityException) {
            // Erro de segurança
            Result.failure(e)
        } catch (e: Exception) {
            // Outros erros
            Result.failure(e)
        }
    }
}
```

### 3. Uso de Recursos de Forma Eficiente

```kotlin
class EfficientSDKUsage {
    // Obter instância uma vez e reutilizar
    private val sdk = ShieldSDK.getInstance()

    fun processMultipleRequests(requests: List<RequestData>): List<String> {
        return requests.map { request ->
            sdk.createSecureEnvelope(
                userData = request.userData,
                consent = request.consent,
                recipientId = request.recipientId
            ).requestId
        }
    }
}
```

## Considerações de Segurança

### Proteção Contra Uso Improcedente

```kotlin
class ShieldSDK(
    private val config: SDKConfig,
    private val encryptionService: EncryptionService,
    private val sessionManager: SessionManager
) {
    init {
        // Garantir que o SDK foi inicializado corretamente
        require(config.encryptionStrategy.isNotBlank()) { "Estratégia de criptografia não pode estar vazia" }
    }

    companion object {
        fun getInstance(): ShieldSDK {
            return INSTANCE ?: throw IllegalStateException(
                "SDK não foi inicializado. Chame initialize() primeiro." +
                "Certifique-se de inicializar o SDK antes de tentar obter a instância."
            )
        }
    }
}
```

### Auditoria de Uso

```kotlin
class ShieldSDK(
    private val config: SDKConfig,
    private val encryptionService: EncryptionService,
    private val sessionManager: SessionManager
) {
    init {
        if (config.enableAuditLogging) {
            logInitialization()
        }
    }

    private fun logInitialization() {
        // Registrar inicialização para fins de auditoria
        println("[AUDIT] SDK inicializado com configuração: ${config.encryptionStrategy}")
    }

    fun createSecureEnvelope(...): SecureDataEnvelope {
        if (config.enableAuditLogging) {
            logEnvelopeCreation()
        }
        // ...
    }
}
```

# 

O módulo SDK Core é o coração do Shield SDK, fornecendo uma interface limpa e poderosa para todas as funcionalidades do sistema. Sua arquitetura cuidadosamente projetada garante segurança, desempenho e extensibilidade, enquanto mantém a simplicidade de uso para os desenvolvedores. A integração harmoniosa com outros módulos permite que o SDK funcione como uma unidade coesa para proteção de dados e conformidade regulatória.
