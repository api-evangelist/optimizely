---
name: optimizely-create-flag-and-roll-out
description: Create an Optimizely Feature Experimentation flag with variables and variations, then enable a targeted rollout in one environment.
api: openapi/_original/optimizely-feature-experimentation-optimizely-feature-experimentation-api-openapi.json
base_url: https://api.optimizely.com/flags/v1
operations: [list_flags, create_flag, fetch_flag, create_variable_definition, list_variable_definitions, create_variation, list_variations, fetch_ruleset, update_ruleset, enable_ruleset, disable_ruleset, archive_flags]
generated: '2026-08-13'
method: generated
source: openapi/_original/optimizely-feature-experimentation-optimizely-feature-experimentation-api-openapi.json
---

# Create an Optimizely feature flag and roll it out

Use the Feature Experimentation Flags v1 API at `https://api.optimizely.com/flags/v1`.
Every operationId below was verified verbatim in the harvested spec.

## Authentication

Send a bearer token: `Authorization: Bearer <token>`.
The spec declares `BearerAuth` (http/bearer) and `OAuth2` (authorization code, authorize
`https://app.optimizely.com/oauth2/authorize`, token `https://app.optimizely.com/oauth2/token`,
scope `all`). A personal access token from the Optimizely app works as the bearer value.
See `authentication/optimizely-authentication.yml`.

## Steps

1. **Check whether the flag already exists.** `list_flags` —
   `GET /projects/{project_id}/flags`. There is no idempotency key on this API, so a
   read-before-write is the only way to avoid creating a duplicate flag. Filter the result
   on the `key` you intend to use.
2. **Create the flag.** `create_flag` — `POST /projects/{project_id}/flags`. Supply `key`,
   `name` and `description`. The `key` is the identifier your SDK code will reference and
   cannot be changed later.
3. **Define the variables the flag carries.** `create_variable_definition` —
   `POST /projects/{project_id}/flags/{flag_key}/variable_definitions`, one call per
   variable. Confirm with `list_variable_definitions`.
4. **Create the variations.** `create_variation` —
   `POST /projects/{project_id}/flags/{flag_key}/variations`, one call per variation, each
   supplying values for the variables defined in step 3. Confirm with `list_variations`.
5. **Read the environment's ruleset before changing it.** `fetch_ruleset` —
   `GET /projects/{project_id}/flags/{flag_key}/environments/{environment_key}/ruleset`.
   Rulesets are environment-scoped; `production` and `development` are separate objects.
6. **Write the rollout rule.** `update_ruleset` — `PATCH` on the same path. PATCH replaces
   the rules you send, so send the full rule list you read in step 5 plus your change.
7. **Turn it on.** `enable_ruleset` —
   `POST /projects/{project_id}/flags/{flag_key}/environments/{environment_key}/ruleset/enabled`.
   `disable_ruleset` on `/ruleset/disabled` is the immediate kill switch and is the correct
   rollback for every step after this one.

## Rules an agent must follow

- **Confirm project and environment before any write.** `project_id` and `environment_key`
  are both path parameters, and the same `flag_key` exists independently in every
  environment. Enabling a ruleset in `production` is a live traffic change.
- **No idempotency key exists on this API.** Retrying a failed `create_flag` can create a
  second flag. Retry only after a `list_flags` read confirms the first attempt did not land.
- **Archive, do not delete.** `archive_flags` (`POST /projects/{project_id}/flags/archived`)
  is reversible via `unarchive_flags`; `delete_flag` is not.
- **Errors.** The API does not use RFC 9457 `application/problem+json`; it returns a JSON
  error body with a `message`. See `errors/optimizely-problem-types.yml`.
- **Rate limits.** No `X-RateLimit-*` headers are declared in the spec or documented for
  this API. Back off on any 429 and re-read rather than replaying writes. See
  `rate-limits/optimizely-rate-limits.yml`.
