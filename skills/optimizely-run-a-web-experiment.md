---
name: optimizely-run-a-web-experiment
description: Stand up an Optimizely Web Experimentation A/B test — project, audience, page, experiment — and read its results.
api: openapi/_original/optimizely-web-experimentation-optimizely-api-openapi.json
base_url: https://api.optimizely.com/v2
operations: [list_projects, get_project, list_audiences, create_audience, list_pages, create_page, create_in_page_event, list_experiments, create_experiment, get_experiment, update_experiment, get_experiment_results, get_experiment_report, get_experiment_results_share_link, get_experiment_results_csv]
generated: '2026-08-13'
method: generated
source: openapi/_original/optimizely-web-experimentation-optimizely-api-openapi.json
---

# Run an Optimizely Web Experimentation A/B test

Use the Optimizely REST API v2 at `https://api.optimizely.com/v2`. Every operationId below
was verified verbatim in the harvested spec.

## Authentication

`Authorization: Bearer <token>`. The spec declares `OAuth2` (authorization code;
authorize `https://app.optimizely.com/oauth2/authorize`, token
`https://app.optimizely.com/oauth2/token`; single scope `all` = full access to the account)
and `apiKey` (http/bearer) for a personal access token. There is no read-only scope — a
token that can read experiments can also start them.

## Steps

1. **Resolve the project.** `list_projects` — `GET /projects`; or `get_project` —
   `GET /projects/{project_id}` when you already have the id. Every subsequent call is
   scoped by `project_id`.
2. **Find or create the targeting audience.** `list_audiences` — `GET /audiences`, then
   `create_audience` — `POST /audiences` if none matches. Audiences are reusable across
   experiments; prefer reuse over creating near-duplicates.
3. **Make sure the page is defined.** `list_pages` — `GET /pages`, then `create_page` —
   `POST /pages` with the URL-matching conditions. Add conversion events on that page with
   `create_in_page_event` — `POST /pages/{page_id}/events`.
4. **Create the experiment.** `create_experiment` — `POST /experiments` with `project_id`,
   `name`, the variations and their traffic allocation, `audience_conditions`, and the
   metrics referencing the events from step 3. It is created paused.
5. **Start it.** `update_experiment` — `PATCH /experiments/{experiment_id}` setting
   `status` to running. This is the live-traffic change; confirm the project with the
   operator first.
6. **Read results.** `get_experiment_results` —
   `GET /experiments/{experiment_id}/results` for the statistical results,
   `get_experiment_report` — `GET /experiments/{experiment_id}/report`, and
   `get_experiment_timeseries` for the trend. `get_experiment_results_csv`
   (`GET /export/experiments/{experiment_id}/results/csv`) exports them, and
   `get_experiment_results_share_link` produces a shareable read-only link.

## Rules an agent must follow

- **Stopping the experiment is `update_experiment`, not `delete_experiment`.** Deleting
  discards the experiment; pausing preserves the collected results.
- **Do not interpret a result the Stats Engine has not called.** Optimizely's Stats Engine
  reports statistical significance in the results payload; report what it returns rather
  than recomputing significance from the raw counts.
- **Pagination.** Collection endpoints take `page` and `per_page` query parameters. Page
  through to completion before asserting that something does not exist.
- **`PATCH` is a partial update** on this API — send only the fields you are changing.
- See `conventions/optimizely-conventions.yml` for pagination, error envelope and
  versioning, and `errors/optimizely-problem-types.yml` for the status codes.
