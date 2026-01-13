<p align="center">
  <img src="https://cdn.genum.ai/images/github_banner.png" alt="Genum GitHub Banner" />
</p>

<div align="center">

###  
<a href="https://genum.ai"><strong>Website</strong></a> ·
<a href="https://docs.genum.ai"><strong>Docs</strong></a> ·
<a href="https://community.genum.ai"><strong>Community</strong></a>

</div>

<br/>

<p align="center">
  <img src="https://img.shields.io/github/stars/genumai/genum" />
  <img src="https://img.shields.io/github/commit-activity/m/genumai/genum" />
  <img src="https://img.shields.io/docker/pulls/genum/core" />
</p>

# Genum


**Test AI behavior before deployment — the same way you test code.**

  

Genum is an open-source system that applies a **test-first CI/CD workflow to LLM instructions**.

  

Teams define prompts, schemas, and expected behavior — then verify them through structured and semantic tests **before anything reaches production**.

  

## Why Genum exists

<p align="center">
  <img src="https://cdn.genum.ai/images/github_gif.gif" alt="Genum GitHub GIF" width="100%" />
</p>

LLM-based systems are often deployed with one critical gap:

  

**they are not tested like production code.**

  

Prompts are:

- changed manually
- validated ad-hoc
- deployed without regression coverage
- trusted based on “seems to work”

  

This makes production behavior fragile and unpredictable.

Genum exists to bring **software delivery discipline** to LLM instructions.

  

## Core principle: test-first AI development

<p align="center">
  <img
    src="https://cdn.genum.ai/images/github_cicd.png"
    alt="Genum Prompt CI/CD Lifecycle"
    width="900"
  />
</p>

Genum follows a strict rule:

>  **Nothing is deployed unless it passes tests defined by the operator.**

  

There is:

- no runtime policy enforcement
- no autonomous decision-making
- no “AI controlling AI” in production

  

All validation happens **before deployment**, using:

- synthetic datasets
- real historical inputs
- explicit expected outputs

  

Production only executes **already verified logic**.

  
  

## What Genum actually does

Genum provides CI/CD for LLM instructions.

Instead of embedding prompts directly into applications or agents, you:
1. Write a prompt instruction and output schema
2. Define a **test suite** for that instruction
3. Run tests locally or in CI
4. Commit only if all tests pass
5. Deploy a locked, versioned instruction

This makes LLM behavior reproducible and change-safe.
  

## Tests are the source of truth

In Genum, **tests define correctness**.
A test consists of:
- input (text, context, tool state)
- expected outcome
- validation method

Validation can be:
-  **strict** (exact match, schema, flags)
-  **semantic** (LLM-based judge comparing output to expectation)

Semantic judges are **part of the test**, not a runtime authority.

They answer one question only:

>  *Does the output satisfy the expectation defined by the operator?*


## Example: Unstructured → Structured extraction

**Instruction:** extract order-related signals from emails.

**Test input:**

```
"Please cancel order 45821. We no longer need delivery."
```


**Expected output (defined in test):**

```json
{
	"order_cancelled": true,
	"order_id": 45821
}
```

  

The test passes if:

- schema is valid
- values match expectation
- or semantic assertion confirms equivalence

If the test fails, deployment is blocked.

## Example: GenAI ChatBot with tools

  

For a support bot with tools and a knowledge base, tests may assert:
- which tool must be called
- required arguments
- call order
- whether clarification is required
- whether the bot must *not* answer directly

Example semantic test:

> “The bot must not provide an answer without calling the `order_status` tool.”

If the behavior violates the test, the instruction cannot be deployed.


## What Genum is NOT

Genum is **not**:

- a runtime policy engine
- an agent framework
- an autonomous decision system

Genum does **not** enforce behavior at runtime.

It ensures that **only pre-validated behavior can reach runtime**.


## Decoupling & delivery into runtime systems


Genum keeps GenAI business logic **separate** from runtime orchestration.

You develop and validate logic in Genum (tests → regression → commit), then **inject a specific, versioned release** into runtime systems:
-  **Public API**: retrieve and execute pinned versions of verified logic
-  **Genum Nodes**: connect verified logic to automation runtimes without copying prompts into workflows


This makes runtime orchestration stable, while GenAI logic evolves safely through the same release discipline as code.

  

## Why CI/CD for LLM instructions

  

LLM instructions are business logic.

Changing them without tests is equivalent to deploying untested code.


Genum provides:
- versioning
- regression testing
- reproducible deployments
- auditable changes
  
So teams can evolve AI logic without breaking production.


## Current capabilities

  

- **Versioned LLM instructions** (prompts) and output schemas
- **Test suites** (strict + semantic) and regression testing
- **Test-first CI/CD workflow** for AI business logic (commit only after tests pass)
- **Decoupling of GenAI business logic from automation runtimes**
- treat AI logic as an independent, testable artifact
- avoid embedding prompts directly into orchestrators, agents, or application code
- **Injection of tested, versioned GenAI logic into automation runtimes**
- via **Public API** (version pinning / idempotent writes where applicable)
- via **Genum Nodes** (connectors for orchestration environments)
- Vendor-agnostic execution (cross-model compatible workflow)
- Self-hosted, open-source deployment
  

## Roadmap
  

Genum is the foundation for higher-level tooling:

- reusable instruction patterns
- assistants that help generate tests
- human-language → testable instructions
- voice-driven definition of business logic

  
The invariant remains the same:

**tests always come first.**

  
  

## Who Genum is for

Best fit:
- platform and backend engineers
- automation and integration teams
- teams deploying LLM logic into production systems
- organizations that treat AI behavior as code

Probably not for:
- creative prompting
- runtime experimentation
- agent demos without test discipline

## Quickstart

```bash
git clone https://github.com/genumai/genum.git
cd genum

docker-compose up -d
```

  

Documentation: [https://docs.genum.ai](https://docs.genum.ai)

  
  
  

## Philosophy

  

Genum does not try to make AI “smart”.

It makes AI **testable**.

If behavior cannot be tested, it should not be deployed.

  

----------

  

## License & Community

  

Genum is open source.

  

- Website: [https://genum.ai](https://genum.ai/)
- Docs: [https://docs.genum.ai](https://docs.genum.ai)
- Community: [https://community.genum.ai](https://community.genum.ai)


Contributions and critical feedback are welcome.
