---
name: optimizely-sync-customer-data-to-odp
description: Push customer profiles, events and catalog objects into the Optimizely Data Platform (ODP), then read segments and recommendations back out.
api: openapi/_original/optimizely-data-platform-customers-openapi.json
base_url: https://api.us1.odp.optimizely.com/v3
operations: [createupdate-customers, get-customer-information, upload-events, update-object, update-products, list-objects, get-object, create-field, list-fields, get-lists, subscribeunsubscribe, get-subscription-status, update-consent, get-consent, RealtimeSegments_ListSegments, RealtimeSegments_GetSegment, get-recommended-products, export, getExportJobStatus, gdpr-delete, gdpr-status]
generated: '2026-08-13'
method: generated
source: openapi/_original/optimizely-data-platform-*.json
---

# Sync customer data into Optimizely Data Platform (ODP)

ODP v3 is region-pinned. Pick the region that matches the account and use it consistently:

- `https://api.us1.odp.optimizely.com/v3`
- `https://api.eu1.odp.optimizely.com/v3`
- `https://api.au1.odp.optimizely.com/v3`

Every operationId below was verified verbatim in the harvested ODP specs.

## Authentication

A private API key in the `x-api-key` request header (spec scheme `x-api-key` /
`ApiKeyAuth`, `apiKey` in `header`). There is no OAuth flow on ODP. Keys are per-account
and per-region — a US key does not work against the EU host.

## Steps

1. **Confirm the schema can hold your data.** `list-objects` — `GET /schema/objects`,
   `get-object` — `GET /schema/objects/{object_name}`, `list-fields` —
   `GET /schema/objects/{object_name}/fields`. Add missing fields with `create-field` —
   `POST /schema/objects/{object_name}/fields` before sending data; ODP rejects unknown
   fields rather than creating them implicitly.
2. **Upsert customer profiles.** `createupdate-customers` — `POST /profiles`. Batch up to
   500 distinct objects per request; the provider's rate-limit page is explicit that bulk
   loads must be batched.
3. **Send behavioural events.** `upload-events` — `POST /events`. Order returns and refunds
   use the same endpoint (`order-returnrefund`).
4. **Update catalog objects.** `update-products` — `POST /objects/products`, or
   `update-object` — `POST /objects/{object_name}` for any custom object.
5. **Manage subscriptions and consent.** `get-lists` — `GET /lists`,
   `subscribeunsubscribe` — `POST /lists/subscriptions`, `get-subscription-status` —
   `GET /lists/subscriptions`, and `update-consent` / `get-consent` on `/consent`.
6. **Read segments and recommendations back.** `RealtimeSegments_ListSegments` —
   `GET /segments`, `RealtimeSegments_GetSegment` — `GET /segments/{segment_id}`,
   `get-recommended-products` — `GET /recommendations/products`.
7. **Export.** `export` — `POST /exports` starts a job; poll `getExportJobStatus` —
   `GET /exports/{exportJobId}`. Exports are asynchronous — never block on the POST.

## Rules an agent must follow

- **Respect the published rate limits** (`rate-limits/optimizely-rate-limits.yml`):
  Lists 10 req/s, Profiles 10 req/s, Recommendations 100 req/s, On-Site GraphQL 500 req/s;
  Events and Objects have no documented limit. Batch (500 objects per request) rather than
  looping single writes.
- **Privacy operations are destructive and asynchronous.** `gdpr-delete`
  (`POST /compliance/gdpr/delete`), `ccpa-delete`, `ccpa-optout` and `lgpd-delete` erase
  customer data. Never call them without an explicit human instruction naming the subject.
  Track completion with `gdpr-status` — `GET /compliance/gdpr/status/{requestId}`.
- **Region is part of identity.** Writing US data to the EU host creates a second, separate
  profile rather than an error.
- **There is no idempotency key.** Profile and event writes are upserts keyed on the
  identifier fields, so a safe retry depends on sending the same identifier — not on a
  request key.
