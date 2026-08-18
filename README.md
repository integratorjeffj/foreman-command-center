# Foreman Command Center

**A single-screen command center for the project manager on a complex construction job, pulling schedule, budget, tasks, risks, decisions, and activity into one place so the next thing needing attention is visible without opening five systems.**

[**Live Demo →**](https://integratorjeffj.github.io/foreman-command-center/) · [How it works](#how-it-works) · [Responsible AI and human controls](#responsible-ai-and-human-controls) · [Limitations](#limitations)

`HTML5` `CSS` `vanilla JavaScript` `no build step` `no dependencies` `single-file frontend`

Complex projects scatter critical information across email, spreadsheets, task lists, meeting notes, and the heads of individual managers, which makes basic questions slow to answer: what is at risk right now, which decisions are blocking progress, what is behind schedule, and what should be looked at next. Foreman is a frontend prototype that consolidates those signals into one operating environment, built around a fictional construction project.

## See it in 60 seconds

1. **Click Decisions in the left rail.** The rail carries live badge counts driven by the data, not hard-coded. The first decision asks whether to approve an alternate steel delivery sequence, and states the tradeoff plainly: a 9 day slip instead of a projected 3 week slip if it goes unresolved. Every decision names its approver, its deadline, the risk if delayed, and the related milestone, risk, and subcontractor records.
2. **Open a decision row to expand the detail drawer, then use Approve or Draft memo.** The action confirms and closes. Nothing persists, which is the point: this demonstrates the decision workflow and the information a manager needs at the moment of choosing, not a system of record.
3. **Press Generate Owner Update in the header.** It switches to the Intelligence workspace and produces a simulated weekly owner update, timestamped and labeled with its source. No AI model is called, and the interface says so.

All project information is fictional and simulated. No live customer systems, production databases, backend services, or AI APIs are connected.

## What the demo covers

Twelve workspaces reachable from the left rail: Overview, Schedule, Budget, Tasks, Contacts, RFIs, Change Orders, Inspections, Risks, Decisions, Activity, and Intelligence.

Overdue tasks, overdue RFIs, high-severity risks, and open decisions surface as computed badges on the rail so the queue is visible before any record is opened. Records filter in place through chips rather than separate screens, and detail opens in a drawer over the current context instead of navigating away.

## Who it is for

A project manager coordinating many interdependent workstreams and stakeholders, with the goal of cutting the time spent reconstructing project status from disconnected sources.

## How it works

The prototype intentionally uses a simple architecture:

```text
Browser
  |
  v
index.html
  |-- HTML interface
  |-- CSS presentation layer
  |-- JavaScript interaction logic
  |-- fictional in-memory project data
  |-- simulated AI outputs
```

There is currently:

- no backend
- no database
- no authentication layer
- no live project-management integration
- no production AI service

This keeps the prototype easy to inspect while allowing the product concept and interaction model to be demonstrated. The entire application is one file, [`index.html`](index.html), readable end to end.

## Key Design Decisions

### One operational workspace instead of disconnected screens

The interface groups related project information into a common command-center experience. The intent is to help a manager move between executive status and operational detail without reconstructing context from several applications.

### Operational signals should be visible before raw records

Priority indicators, project health, risk states, and decision queues are designed to direct attention before the user begins reviewing individual records.

### AI is treated as an assistant, not the system of record

The AI Intelligence workspace is explicitly labeled as simulated output and requires human review. In a production design, AI would be appropriate for synthesis, summarization, drafting, and pattern identification, while project facts, approvals, permissions, and financial calculations should remain grounded in deterministic systems and authorized data.

### Prototype simplicity over premature infrastructure

A single-page frontend was appropriate for validating the information architecture and management experience before introducing a backend, database, identity, APIs, or deployment complexity.

## Responsible AI and Human Controls

Foreman does not currently call an AI model.

The prototype includes an **AI Intelligence Workspace** to demonstrate where AI-assisted capabilities could eventually appear in the workflow. The interface labels these results as simulated and states that human review is required.

A production implementation should maintain several boundaries:

| Capability | Preferred Control |
|---|---|
| Schedule and budget calculations | Deterministic logic and source-system data |
| Permissions and authorization | Identity and role-based access controls |
| Project status records | System-of-record data |
| AI summaries | Grounded source data plus human review |
| Draft communications | AI-assisted, reviewed before sending |
| Recommendations | Advisory only unless explicitly authorized |
| External write actions | Authentication, authorization, audit logging, and approval |

## Demonstration Data

The application uses a fictional project named **Meridian Heights Residences**.

The data exists only to make the interface and workflows understandable. It must not be interpreted as a real customer deployment, production project, or live operational record.

## How this was checked

The current validation goal is product and interaction validation rather than production-system validation. There is no automated test suite in this repository, and this README does not claim one. Checking is manual, against:

- navigation between workspaces
- filtering and interactive controls
- readable project-status presentation
- consistent risk and status indicators
- clear labeling of simulated AI functionality
- responsive presentation across reasonable browser sizes

Automated testing belongs in a later version, once the architecture is complex enough to justify it. See [Roadmap](#roadmap).

## Security Considerations

Because this is a static frontend demonstration, it intentionally contains no credentials, API tokens, customer information, private configurations, or production-system access.

A production architecture would need to address:

- authentication
- role-based access control
- project-level authorization
- API credential and secret management
- encryption in transit and at rest
- audit logging
- data retention
- customer and employee information
- authorization for external write actions
- prompt-injection risk when AI processes external project content

## What I Owned

I directed the product concept and workflow design around the operational problem of helping a project manager see what requires attention across a complex project.

My contribution includes:

- business problem framing
- workflow and information architecture
- operational UX direction
- feature definition
- responsible AI boundaries
- testing and validation of the resulting prototype
- AI-assisted application development

This repository does not claim that every line was manually authored without AI assistance.

## What I Learned

This project reinforced several principles that apply beyond project management:

1. A dashboard should help someone decide what to do, not simply display more information.
2. Operational systems need clear status, ownership, dependencies, and exception visibility.
3. AI is most useful when placed inside a well-defined workflow rather than treated as the workflow itself.
4. Product architecture should become more complex only when the business requirement justifies it.
5. A strong prototype can validate workflow and user experience before production integrations are introduced.

## Limitations

Foreman is a **frontend portfolio demonstration**, not a production project-management platform.

Current limitations include:

- fictional data only
- no persistence
- no multi-user support
- no authentication
- no role-based permissions
- no backend services
- no live API integrations
- no notification service
- no real AI model integration
- no production audit trail

## Production Considerations

A production implementation would likely require:

- authenticated users and role-based permissions
- persistent database storage
- project and organization tenancy boundaries
- integrations with source systems
- structured API layer
- notification workflows
- secure secret management
- audit history
- observability and error monitoring
- automated testing
- deployment pipeline
- AI grounding and evaluation if AI features are enabled
- explicit controls around any external write action

A production architecture should also determine which platform is the authoritative system of record rather than attempting to duplicate every project-management function.

## Roadmap

Potential future work, prioritized by portfolio and architectural value:

1. Document the conceptual data model and system boundaries.
2. Add an architecture diagram showing a production-minded version.
3. Separate demonstration data from presentation logic.
4. Introduce automated validation for deterministic project-health calculations.
5. Add one safe read-only external integration or mock adapter.
6. Add authentication and role-based views in a future full-stack version.
7. Replace simulated AI outputs with grounded AI assistance only where it provides clear workflow value.

## Portfolio Context

Foreman is part of my public portfolio focused on **AI integration, business systems, workflow automation, AI adoption, and operational transformation**.

It is intended to demonstrate how I approach a business problem as an operator and integrator: understand the workflow first, make the important decisions visible, introduce technology deliberately, and keep human accountability clear.

---

[View my GitHub profile](https://github.com/integratorjeffj) · [LinkedIn](https://www.linkedin.com/in/integratorjeffj/)
