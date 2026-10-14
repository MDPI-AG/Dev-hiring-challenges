# MDPI Developer Hiring Challenges

This repository collects the take-home assessments used by MDPI engineering teams during technical hiring.

Each open role has its own folder containing a self-contained assignment: context, requirements, deliverables, and evaluation notes. Candidates receive a link to the folder that matches the position they applied for.

## Challenges

| Folder | Role | Position |
| --- | --- | --- |
| [`Python developer/`](./Python%20developer) | Senior Python Backend Engineer | [Backend Engineer (Python)](https://careers.srb.mdpi.com/jobs/8331526-backend-engineer-python) |

More challenges are added here as new roles open. Each folder is independent: nothing outside it is required to complete an assignment.

## How the process works

1. You receive the link to the challenge folder for your role.
2. You have **7 calendar days** from receiving the assignment to submit.
3. Expected effort is **about 8 focused hours**. The deadline is deliberately longer than the effort so you can fit the work around your schedule.
4. You build your solution in **your own GitHub repository** (public, or private with read access granted to the MDPI accounts we provide). Do not fork or open pull requests against this repository.
5. You send the repository URL to your MDPI contact before the deadline, together with any setup notes reviewers need.
6. Shortlisted candidates are invited to a technical interview built around their submission.

Please do not rewrite or force-push the submitted history after the deadline unless MDPI asks you to.

## Rules that apply to every challenge

**Scope.** Assignments are intentionally open-ended. We care more about a complete, reliable core workflow than about the number of features. A focused implementation that works consistently beats a large solution with unfinished parts.

**Use of AI tools.** You may use AI assistants. Their use is never evaluated negatively. You remain responsible for the submitted solution and must be able to explain, modify, and troubleshoot every part of it during the interview. In your README, briefly state which tools you used, what you used them for, and how you reviewed or validated their output.

**Secrets.** Never commit credentials, API keys, or tokens. Never send them to us. If your solution depends on an external service, document the setup and provide a practical way for a reviewer to run the project and the tests without paid access.

**Reproducibility.** A reviewer should be able to clone your repository and run the project by following your README. Pin your dependencies. Containerization and CI are welcome but not required.

**Git history.** Commit as you work. A readable history tells us how you think; a single squashed commit tells us nothing.

## What we evaluate

- Whether the required workflow actually works, end to end.
- How responsibilities are separated and how the project is structured.
- Correctness and error handling, including external failures and invalid input.
- Tests chosen by risk, independent of live third-party services.
- Documentation: setup, architecture, technical decisions, trade-offs, known limitations.
- Engineering judgment, especially the reasoning behind the choices you made and the ones you rejected.

We do not expect a perfect production system. We expect a working solution and a clear understanding of the code you submit.

## Questions

If anything in an assignment is ambiguous, make a reasonable assumption, document it in your README, and move on. If something is genuinely blocking, contact your MDPI recruiting contact.

## License

The content of this repository is proprietary to MDPI AG. See [LICENSE.md](./LICENSE.md). Candidates invited to an assessment may use the relevant challenge text to prepare their own submission; republishing or redistributing the challenge texts is not permitted.
