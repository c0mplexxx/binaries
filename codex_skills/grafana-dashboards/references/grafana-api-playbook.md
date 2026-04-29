# Grafana API Playbook

## API Discipline

- fetch the current dashboard before editing
- extract only the fields you need
- patch the smallest possible JSON surface
- do not print full dashboard blobs unless a specific panel must be inspected

## Core API Patterns

- fetch dashboard JSON
- extract version, panel ids, titles, and layout
- build update payload
- POST the updated dashboard
- report status and new version

## Infinity Datasource Gotchas

- prefer stat panels over merged tables when schemas differ
- put HTTP method under `url_options`, not the target root
- do not rely on UQL parser for these workflows
- do not assume backend JSONata works in every installed version
- scalar results such as `/api/v1/series/count` may arrive as `data[0]`
- disable pagination explicitly when needed

## Panel Construction Notes

- stat panels work well for single-value API reads
- row panels help structure large dashboards
- extract and preserve grid placement deliberately

## Secrets and Environment

Do not hardcode tokens or instance-specific secrets in the skill itself. Expect:

- Grafana URL
- auth token
- datasource uid
- environment-specific endpoints

to come from the current environment or explicit user context.
