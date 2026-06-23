<!-- gjalla-start -->
## gjalla System-level Version Control

This project uses gjalla for context management, agent orchestration, spec management, and rule enforcement. Project ID: 61

### Setup
Ensure gjalla CLI is installed: `pip install gjalla` (or `pipx install gjalla`), then you can use `gjalla setup` to get going. If there's already a .gjalla dir and a config.yaml, setup may have already been successfully run. You'll know for sure by checking that gjalla is represented in precommit hooks.

### System-level Context                                                                                                                                                                                                               
Gjalla is the persistent architectural memory layer for this codebase. It tracks architecture, rules, capabilities, data flows, tech stack, and any custom context that you need to know to operate on this team — and records how they change over time. Use it to ground your work in the actual system state and the expectations of your team before writing code, and to keep the record accurate after you commit.

Institutional knowledge and helpful context are in .gjalla/guidance if available. The gjalla CLI is the fastest, most reliable way to get context about architecture and behavior. Use these resources during planning and as you implement to understand the intended architecture, rules, and system constraints. The CLI is best for local project context, and the MCP is best if you need gjalla changelogs, findings history, or system-wide context (your whole team works on these and the centralized storage is remote).

Key commands:
- `gjalla state show` — current system state (elements, rules, capabilities, etc.)
- `gjalla rules list` — constraints and ADRs you must follow
- `gjalla log [--since 7d] [--type ...]` — semantic change history for the project
- `gjalla context show` — agent-ready context bundle for this project
- `gjalla spec new <slug>` — scaffold a change spec before implementing

Fetch relevant context via gjalla to orient your design. Prefer doing things the right way — in alignment with the project's architecture, rules, and best practices — over expedient shortcuts. The goal should be clean, organized implementations that are not over-complicated, don't cause collateral effects, and are easy to understand and maintain. When we do this right, our implementations are usually simpler to implement, test, and maintain, since they align with the source of truth.

### Planning, Implementing, and Preparing for Commit                             
Source-of-truth specs can be fetched with gjalla. If your change affects any system primitive (architecture, capabilities, data model, surface area, data flows, external services, rules, or tech stack), create a change spec. gjalla also has helpful skills to help you construct specs, review and harden specs, breakdown your tasks, audit your test system, and other helpful steps as you proceed through the SDLC.

### Committing
To help your team understand and track your changes, you must attest to all of your changes and guardrail adherence via a gjalla attestation. You must review all your changes for adherence to gjalla rules, fixing important violations and flagging any that need human review. You will also be required to report how the staged code changes the system and the provenance of your work. `gjalla attest --example` has all the fields, view the output in full. Focus only on staged code only even if you're worked on other changes in this session.
Your attestation will be externally validated, so ensure you're accurate and complete.

### Windows Note
On Windows, Git for Windows includes its own POSIX shell (MSYS2), so the shell commands above (e.g. `shasum`, `cut`) work inside git hooks and Git Bash. You do not need WSL or a separate Unix environment.
<!-- gjalla-end -->
