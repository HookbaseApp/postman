# Hookbase Postman Collections

Official [Postman](https://www.postman.com/) collections for the [Hookbase](https://www.hookbase.app) webhook platform API.

## Collections

| Collection | Description |
|-----------|-------------|
| [Hookbase API](collections/hookbase-api.postman_collection.json) | Complete API reference — sources, destinations (HTTP + warehouse), routes, events, deliveries, transforms, filters, schemas, cron jobs, analytics, and more. |
| [Integration Tests](collections/hookbase-integration-tests.postman_collection.json) | End-to-end test suite for validating API behavior. |

## Quick Start

### Import via Postman

1. Open Postman and click **Import**
2. Drag and drop a collection JSON file, or paste the raw URL:
   ```
   https://raw.githubusercontent.com/HookbaseApp/postman/main/collections/hookbase-api.postman_collection.json
   ```
3. Import the environment file from `environments/hookbase.postman_environment.json`
4. Set your `apiKey` (generate one at [hookbase.app](https://www.hookbase.app) with the `whr_` prefix)

### Run via CLI

```bash
# Install Newman
npm install -g newman

# Run the API collection
newman run collections/hookbase-api.postman_collection.json \
  -e environments/hookbase.postman_environment.json

# Run integration tests
newman run collections/hookbase-integration-tests.postman_collection.json \
  -e environments/hookbase.postman_environment.json
```

## Environment Variables

| Variable | Description |
|----------|-------------|
| `baseUrl` | API base URL (default: `https://api.hookbase.app`) |
| `apiKey` | Your Hookbase API key (`whr_` prefix) |
| `orgId` | Your organization ID |
| `orgSlug` | Your organization slug (used for ingest URLs) |

## Warehouse Destinations

The API collection includes examples for creating warehouse destinations that archive webhooks to cloud storage:

- **Amazon S3** — requires `bucket`, `region`, `accessKeyId`, `secretAccessKey`
- **Cloudflare R2** — requires `bucket`, `endpoint`, `accessKeyId`, `secretAccessKey` (S3-compatible API)
- **Google Cloud Storage** — requires `bucket`, `projectId`, `serviceAccountKey`
- **Azure Blob Storage** — requires `storageAccount`, `container`, `sasToken`

Warehouse destinations require a **Pro** or **Business** plan. Credentials are encrypted at rest.

## Links

- [Hookbase Documentation](https://docs.hookbase.app)
- [API Reference](https://docs.hookbase.app/receive/api/)
- [OpenAPI Spec](https://docs.hookbase.app/openapi.json)
