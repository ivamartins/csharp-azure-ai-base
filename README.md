# csharp-azure-ai-base

Minimal, functional Azure Functions (C#) + LLM integration base.

**This is a core framework example for high-volume backend + AI integrations on Azure (C# / .NET).**

## Why this base?
- Directly supports the Quartile (USA) experience: "backends de alto volume em C# e Python sobre Azure Functions, incluindo integrações assíncronas com Azure Service Bus e integrações avançadas com APIs de IA (Claude + ChatGPT) em produção".
- Functional starting point for:
  - Serverless backends on Azure
  - Async with Service Bus / Event Hubs
  - LLM enrichment (Claude, Grok, ChatGPT) for legacy data or workflows
  - Combining with event-driven (Kafka/Flink) or other bases

## Quick Start / How to run the application

**Prerequisites:** .NET 8+ SDK and Azure Functions Core Tools (`func`).

**Step by step (local):**

1. Restore and build:
   ```bash
   dotnet restore
   dotnet build
   ```

2. Start the function locally:
   ```bash
   func start
   ```

3. The example function can process messages and enrich with LLM (mocked or real via API key).

See code in `Function1.cs.example` (example structure). Once you turn the examples into a real project, the commands above will work.

## Running the tests

## Running the tests

Once you have a real .csproj / test project set up (xUnit recommended):

```bash
dotnet restore
dotnet test
```

Example test file included: `SampleServiceTest.cs.example` (basic xUnit test for an enrichment function). Convert the `.example` into real test files when scaffolding the project.

**Português:** Após criar o projeto real com `dotnet new`, rode `dotnet test`. O exemplo de teste unitário básico (xUnit) está em `SampleServiceTest.cs.example`.

## Extend for Real Use

- Replace mock LLM call with real Azure OpenAI / xAI / Anthropic SDK.
- Add Service Bus trigger/output for async pipelines.
- Integrate with legacy systems (HTTP calls to old Java/Play, DB queries).
- Combine with AI agents pattern (see whatsapp-grok-bot).
- Deploy to Azure: `func azure functionapp publish <your-app>`

## Portfolio Mapping

This base proves practical C#/.NET + Azure + AI integration experience, often used for modernizing or extending legacy financial/retail platforms.

See the complete portfolio and other bases (Quarkus, Play, Flink, Akka, ES, AI Agents):
https://ivamartins.github.io/code-solutions-site/

Company LinkedIn: https://www.linkedin.com/company/code-solutions-it/

Clone, add your real LLM calls and legacy integrations. Ready for production serverless + AI workloads.

## Example Structure (pseudo for the base)

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

Add real SDKs, error handling, etc.
