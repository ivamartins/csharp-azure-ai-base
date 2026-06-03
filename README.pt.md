# csharp-azure-ai-base (Português)

Base funcional mínima em Azure Functions (C#) + integração com LLMs/IA.

**Este é um exemplo de framework principal para backends de alto volume + integrações com IA no Azure (C# / .NET).**

## Por que esta base?
- Suporta diretamente a experiência Quartile (EUA): "backends de alto volume em C# e Python sobre Azure Functions, incluindo integrações assíncronas com Azure Service Bus e integrações avançadas com APIs de IA (Claude + ChatGPT) em produção".
- Ponto de partida funcional para:
  - Backends serverless no Azure
  - Assíncrono com Service Bus / Event Hubs
  - Enriquecimento com LLM (Claude, Grok, ChatGPT) para dados legados ou workflows
  - Combinação com event-driven (Kafka/Flink) ou outras bases

## Início Rápido / Como rodar a aplicação

**Pré-requisitos:** .NET 8+ SDK e Azure Functions Core Tools (`func`).

**Passo a passo (local):**

1. Restore e build:
   ```bash
   dotnet restore
   dotnet build
   ```

2. Inicie a function localmente:
   ```bash
   func start
   ```

3. A função de exemplo processa mensagens e enriquece com LLM (mock ou real via chave de API).

Veja o código em `Function1.cs.example` (estrutura de exemplo). Quando transformar os exemplos em um projeto real, os comandos acima funcionarão.

## Executando os testes

## Executando os testes

Depois de criar o projeto real (.csproj + testes, recomendado xUnit):

```bash
dotnet restore
dotnet test
```

Arquivo de exemplo de teste incluído: `SampleServiceTest.cs.example` (teste xUnit básico para função de enriquecimento). Converta o `.example` em arquivos reais de teste ao estruturar o projeto.

## Estenda para Uso Real

- Substitua a chamada mock LLM por SDK real Azure OpenAI / xAI / Anthropic.
- Adicione trigger/output Service Bus para pipelines assíncronos.
- Integre com sistemas legados (chamadas HTTP para Java/Play antigo, queries DB).
- Combine com padrão de agentes IA (veja whatsapp-grok-bot).
- Deploy no Azure: `func azure functionapp publish <seu-app>`

## Mapeamento de Portfólio

Esta base comprova experiência prática com C#/.NET + Azure + integração IA, frequentemente usada para modernizar ou estender plataformas legadas financeiras/varejo.

Veja o portfólio completo e outras bases (Quarkus, Play, Flink, Akka, ES, Agentes IA):
https://ivamartins.github.io/code-solutions-site/

Empresa LinkedIn: https://www.linkedin.com/company/code-solutions-it/

Clone, adicione suas chamadas reais de LLM e integrações com legados. Pronto para workloads serverless + IA em produção.

## Estrutura de Exemplo (pseudo para a base)

```csharp
// Function1.cs
[Function("LegacyEnrich")]
public async Task<IActionResult> Run([ServiceBusTrigger("legacy-queue")] string message)
{
    // EN: Call LLM for enrichment (Claude/Grok/ChatGPT)
    // PT: Chama LLM para enriquecimento
    var enriched = await CallLlmAsync(message); 
    // ... persist or forward
    return new OkObjectResult(enriched);
}
```

Adicione SDKs reais, tratamento de erros, etc.
