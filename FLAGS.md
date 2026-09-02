# FLAGS

Improvement register for this repository. Documentation handover only - do not treat Open rows as bugs fixed in the docs PR.

Status: **Open** (actionable later) or **Accepted** (known limitation).

| ID | Severity | Finding | Evidence | Suggested next step | Status |
| --- | --- | --- | --- | --- | --- |
| F1 | High | Must shut down cloud resources after the lab to avoid ongoing cost. | [README.md](README.md) REQUIRED shutdown section | Run teardown commands (or delete the project) after every workshop deploy. | Open |
| F2 | Low | Guide assumes Google Cloud Shell, not local PowerShell. | [README.md](README.md) Operator Notes | Follow Cloud Shell path in [docs/deploy_instructions.md](docs/deploy_instructions.md). | Accepted |
