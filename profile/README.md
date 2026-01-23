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

---

# **Genum is Cursor for Prompts — with CI/CD, Versioning, Execution, Integrations, and FinOps**

**Genum is an open-source PromptOps platform that lets teams develop, test, version, deploy, and run GenAI instructions the same way they ship production code.**

Think:

**Genum = Cursor + GitHub + CI/CD + Execution + FinOps — for prompts**

| Genum Layer | What it does |
|------|--------------|
| Prompt IDE | Write & refine instructions |
| Testing | Test-First approach, Strict + semantic regression tests |
| Versioning | Git-style history & releases |
| CI/CD | Block deployments on failures |
| Execution & Integration | APIs & Custon Nodes |
| FinOps | Cost, latency, usage visibility |

If prompts are business logic, Genum is the system that makes them **testable, reproducible, and safe to deploy**.

<p align="center">
  <img src="https://cdn.genum.ai/images/github_gif.gif" alt="Genum GitHub GIF" width="100%" />
</p>

---

## Why Genum exists

Most GenAI systems fail in enterprise automation for one simple reason:

**prompts are not treated like code.**

In real systems, prompts are often:
- edited manually
- validated ad-hoc
- deployed without regression tests
- trusted because they “seem to work”

This leads to:
- silent behavior drift  
- broken automations  
- unpredictable downstream effects  

Genum exists to bring **software delivery discipline** to GenAI instructions.

---

## Core rule: test-first AI delivery

> **Nothing is deployed unless it passes tests defined by the operator.**

Genum:
- does **not** enforce runtime policies
- does **not** make autonomous decisions
- does **not** run “AI controlling AI”

All validation happens **before deployment** using:
- synthetic datasets
- real historical inputs
- explicit expected outputs

Production only executes **already verified logic**.

---

## What Genum actually is

Genum provides a full **PromptOps lifecycle**:

1. Write a prompt instruction + output schema  
2. Define a test suite (strict + semantic)  
3. Run tests locally or in CI  
4. Commit only if all tests pass  
5. Deploy a locked, versioned instruction  
6. Execute it via API or integration nodes  

Prompts become **first-class, versioned artifacts** — not inline text inside apps, agents, or workflows.

<p align="center">
  <img
    src="https://cdn.genum.ai/images/github_cicd.png"
    alt="Genum Prompt CI/CD Lifecycle"
    width="900"
  />
</p>

---

## Tests define correctness

In Genum, **tests are the source of truth**.

A test includes:
- input (text, context, tool state)
- expected outcome
- validation method

Validation types:
- **Strict** — schema, exact match, flags
- **Semantic** — LLM-based judge used only as a test assertion

Semantic judges are **never runtime authorities**.

They answer one question only:

> *Does the output satisfy the expectation defined by the operator?*

---

## Example: Unstructured → Structured extraction

**Instruction**  
Extract order-related signals from emails.

**Test input**
```text
"Please cancel order 45821. We no longer need delivery."
````

**Expected output**

```json
{
  "order_cancelled": true,
  "order_id": 45821
}
```

Deployment is blocked unless:

* schema is valid
* values match expectations
* or a semantic assertion confirms equivalence

---

## Example: Chatbot with tools

For a support bot, tests can assert:

* which tool must be called
* required arguments
* call order
* whether the bot must *not* answer directly

Example semantic rule:

> “The bot must not provide an answer without calling `order_status`.”

If violated, the instruction cannot be deployed.

---

## What Genum is NOT

Genum is **not**:

* a runtime policy engine
* an agent framework
* an autonomous decision system
* a creative prompt playground

Genum is **delivery infrastructure** for GenAI business logic.

---

## Decoupling & delivery

Genum keeps GenAI logic **separate from runtime orchestration**.

You:

* develop & validate logic in Genum
* inject a **specific, versioned release** into runtime systems

Delivery options:

* **Public API** — retrieve pinned versions of verified logic
* **Genum Nodes** — connect verified logic to automation platforms

Runtime stays stable.
AI logic evolves safely through releases.

---

## Cross-Vendor with Support for Custom LLMs

Genum keeps your business-logic **vendor-agnostic**. 
Out-of-the-box-Support for major commercial providers, plus support for custom LLMs.

### Custom LLMs

<p align="center">
  <img src="https://cdn.genum.ai/images/github_gif.gif" alt="Genum custom LLM Support" width="100%" />
</p>


---

## FinOps: cost & latency visibility

Genum includes a FinOps layer that tracks:

* usage per prompt, model, and version
* latency characteristics
* cost per execution

This enables:

* model comparisons
* cost-quality trade-offs
* predictable AI operating costs

---

## Who Genum is for

**Best fit**

* platform & backend engineers
* automation & integration teams
* organizations deploying GenAI into production
* teams that treat AI behavior as code

**Probably not for**

* creative prompting
* live experimentation
* agent demos without test discipline

---

## Quickstart

```bash
git clone https://github.com/genumai/genum.git
cd genum
docker-compose up -d
```

Docs: [https://docs.genum.ai](https://docs.genum.ai)

---

## Philosophy

Genum does not try to make AI *smarter*.

It makes AI **testable**.

If behavior cannot be tested, it should not be deployed.

---

## License & Community

Genum is open source.

* Website: [https://genum.ai](https://genum.ai)
* Docs: [https://docs.genum.ai](https://docs.genum.ai)
* Community: [https://community.genum.ai](https://community.genum.ai)

Contributions and critical feedback are welcome.

