# AI build record

The prompts, harness details, token usage, and change measurements recorded when this implementation was generated with AI. They moved here from the [README](../README.md) on 2026-10-19 unchanged, except that local setup details in the prompts are marked as omitted and relative links now point from this folder.

## Implementation analysis

### Scope and checks

- Five Rust services, one shared Rust crate, a React 19.3 application, PostgreSQL migrations, Docker Compose, and Kind manifests.
- Kind verification: all six deployments were ready at 2/2 replicas; PostgreSQL was ready at 1/1.
- Rust test suite: 34 tests passed across the six packages.
- Frontend: `npm run check`, `npm run test:coverage` (19 tests), and `npm run build` passed. Vitest reported 96.44% line coverage; SonarCloud's configured frontend source scope reports 91.8%.
- Lighthouse: all five categories scored 100 on both desktop and mobile.
- Source/configuration size: **6,839 nonblank LOC across 56 files**, counted on 2026-09-28. The count includes `.rs`, `.ts`, `.tsx`, `.css`, `.html`, `.sql`, `.sh`, `.toml`, `.yaml`, `.yml`, `.json`, `.conf`, and `.svg` files; excludes lockfiles, generated/build/dependency directories, and the OpenDesign prototype/assets.

### Harness and token usage

Harness for this task: **Codex, GPT-6 Luna, max effort**. The Codex session log and cache were empty before work began. The final session counters from the Codex JSONL log are:

| Counter | Tokens | Notes |
| --- | ---: | --- |
| Input | 64,359,785 | Includes cached input below |
| Cached input | 62,662,400 | Subset of input |
| Uncached input | 1,697,385 | Input less cached input |
| Output | 356,024 | Includes reasoning below |
| Reasoning | 205,900 | Subset of output, not added again |
| Total input + output | 64,715,809 | |

Worked for 2h 32m 55s

Using the [official GPT-6 Luna model pricing](https://developers.openai.com/api/docs/models/gpt-6-luna) and [OpenAI API pricing](https://developers.openai.com/api/docs/pricing?tab=suite) consulted on 2026-09-28 (uncached input $0.10/M tokens, cached input $0.01/M, output $0.50/M), the API-equivalent estimate is **$0.97437450 USD** (about **$0.97**). Reasoning tokens use the output rate and are already included in output. This is a token-based API equivalent, not the Codex subscription charge.

OpenDesign's local telemetry separately recorded 8,089,760 effective-input counters across its GPT-6 Luna handoff/dev-loop runs. Its database does not provide a complete cached-input/output/reasoning breakdown, so those counters are disclosed separately and are not included in the priced Codex estimate.

### Original request

<details>
<summary>Expand the full task prompt</summary>

```text
Implement https://bytebytego.com/courses/system-design-interview/hotel-reservation-system in Rust, React 19.3 (handoff from OpenDesign [local launch details omitted]), PostgreSQL, and Kubernetes via local Kind (2 replicas for each microservice). Use SonarQube Cloud via Chrome (https://sonarcloud.io/organizations/marcelomiyake/) to create and manage these monorepo projects, and complete this job with zero SonarQube issues and test coverage above 80%. If you need to run the scanner from the command line, [local token setup omitted]. Still, you can also use GitHub Actions and push commits in a loop until the issues are clean (the problem is that Rust is not supported for automatic analysis (https://docs.sonarsource.com/sonarqube-cloud/analyzing-source-code/automatic-analysis#supported-languages), so use another approach to consider Rust code in SonarQube Cloud (https://docs.sonarsource.com/sonarqube-server/analyzing-source-code/languages/rust); if you generate another SONAR_KEY, update it in the GitHub project or [local configuration omitted]. The frontend should have a perfect Lighthouse grade and good SEO META in 1 Click. Finally, update the README.md with a screenshot and an analysis that includes this prompt, the harness used here (Codex, GPT-6 Luna with max effort), and the token costs from the sessions to complete this task (input tokens, cache tokens, reasoning tokens, output tokens) and LOC. The cache and sessions were empty just before starting this session. Consult the OpenAI official documentation for token prices to estimate total costs.
```

</details>

## Reservation abandonment analytics

### Change and quality statistics

The analytics implementation commit, [`c747869`](https://github.com/marcelomiyake/hotel-rust/commit/c747869746c8b321ce23d9180d80599c7447242b), changed seven files: one SQL migration was created, six existing code, configuration, and test files were changed, and no files were deleted. Its Git diff contains **476 inserted lines and 27 removed lines** (net +449). The new migration creates two tables, two indexes, and the abandonment view.

The web performance pass adds prerendered HTML for the home page, embeds its stylesheet in the page, and loads the trips and host tools on demand. It creates four source files and changes three existing files, with no file deletions.

Across the analytics implementation, web performance pass, and this README report, the diff changes **14 files**: five created, nine modified, and none deleted, with **740 inserted lines and 177 removed lines** (net +563).

The current source/configuration inventory is **7,306 nonblank LOC across 61 files**, excluding this README, lockfiles, generated/build/dependency directories, and the OpenDesign prototype/assets. The count covers `.rs`, `.ts`, `.tsx`, `.mjs`, `.css`, `.html`, `.sql`, `.sh`, `.toml`, `.yaml`, `.yml`, `.json`, `.conf`, and `.svg` files.

| Check | Result |
| --- | ---: |
| Rust workspace tests | 34 passed |
| Frontend tests | 19 passed |
| Frontend Vitest line coverage | 96.42% |
| Frontend SonarCloud coverage | 91.8% |
| Reservation service SonarCloud coverage | 96.5% |
| SonarCloud open issues across all seven projects | 0 |
| SonarCloud bugs, vulnerabilities, and code smells across all seven projects | 0 |
| SonarCloud quality gates | 7 passed |

All six Rust packages passed the repository's `cargo llvm-cov --fail-under-lines 80` checks. The TypeScript check, frontend coverage run, and production build passed. The live Compose smoke check confirmed that Nginx forwards journey events and that a `payment` screen checkpoint is stored in PostgreSQL.

Lighthouse 13.5.0 on the Compose deployment scored **100 in all five categories** on desktop and mobile, including Performance, Accessibility, Best Practices, SEO, and Agentic Browsing. The page's SEO META checks scored 100 on both form factors. Repeated mobile runs scored 100 Performance; Lighthouse reported no browser-console errors. The homepage is prerendered into HTML, its CSS is inline to remove the render-blocking stylesheet request, and the trips and host screens load as separate on-demand chunks.

### Harness and token cost for this feature session

Harness: **Codex, GPT-6 Luna (`gpt-6-luna`), max effort**. The session and cache were empty before the task began, as specified in the prompt. These are cumulative Codex session-log counters captured at 2026-10-01 18:20 UTC before final README editing and the final Git operations; cached input is included in input, and reasoning is included in output.

Worked for **1h 13m 39s**.

| Counter | Tokens | Notes |
| --- | ---: | --- |
| Input | 20,495,593 | Includes cached input below |
| Cached input | 20,061,184 | Subset of input |
| Uncached input | 434,409 | Input less cached input |
| Output | 142,242 | Includes reasoning below |
| Reasoning | 100,798 | Subset of output; not counted twice |
| Total input + output | 20,637,835 | |
| Cache writes | 0 | |

The [official GPT-6 Luna model page](https://developers.openai.com/api/docs/models/gpt-6-luna) and [OpenAI API pricing](https://developers.openai.com/api/docs/pricing?tab=suite), checked on 2026-10-01, list standard rates of $0.10/M uncached input, $0.01/M cached input, and $0.50/M output tokens. Using those rates, the API-equivalent estimate is **$0.31517374 USD** (about **$0.32**): $0.04344090 uncached input + $0.20061184 cached input + $0.07112100 output. Reasoning tokens use the output rate and are already included in output. This is a token-based API equivalent, not the Codex subscription charge.

<details>
<summary>Full prompt analyzed for this feature</summary>

```text
I want you to implement a new feature that identifies when a user starts a reservation but abandons it before paying. I want us to track which screen the user stopped at before abandoning the reservation. No administrative frontend implementation is needed; I want the data stored in the database (it doesn't need to be the same existing relational database) so we can use it later to improve the system. So it's not necessary to change the frontend features for the user, but you can change the structure to track user events. In this case, if you change it, the frontend should have a perfect Lighthouse grade and good SEO META in 1 Click. Complete this job with zero SonarQube issues (not only new, but zero in total) and test coverage above 80%. I also want to add a new section to README.md with statistics for this new feature. Include the number of changes (how much was deleted, created, changed, etc.), an analysis that includes this prompt, the harness used here (Codex, GPT-6 Luna with max effort), and the token costs from the sessions to complete this task (input tokens, cache tokens, reasoning tokens, output tokens), plus LOC. The cache and sessions were empty just before starting this session. Consult the OpenAI official documentation for token prices to estimate total costs. Commit following https://www.conventionalcommits.org/and push to GitHub after all.
```

</details>
