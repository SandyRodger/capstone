## Start up

## Check databases:

- Postgres
  - psql "postgresql://requestbin:requestbin@localhost:5432/request_bin"
  - SELECT * FROM webhook_events LIMIT 5;
- MongoDB
  - mongosh "mongodb://localhost:27017"
  - show dbs
  - use request_bin
  - show collections
  - db.github_payloads.estimatedDocumentCount()

TEST MONGO COMMIT
```
curl -X POST http://localhost:3000/webhook \
  -H "Content-Type: application/json" \
  -H "X-GitHub-Event: push" \
  -H "X-GitHub-Delivery: 11111111-2222-3333-4444-555555555555" \
  -d '{
    "ref": "refs/heads/main",
    "repository": { "full_name": "SandyRodger/request-bin-demo" },
    "sender": { "login": "SandyRodger" },
    "head_commit": { "id": "abc123", "message": "feat: save to mongo" },
    "commits": [
      { "id": "abc123", "message": "feat: save to mongo" },
      { "id": "def456", "message": "fix: small tweak" }
    ]
  }'
```
- mongosh
- use request_bin
- db.github_payloads.estimatedDocumentCount()
```
db.github_payloads.find(
  {},
  {
    "headers.x-github-event": 1,
    "headers.x-github-delivery": 1,
    "repository.full_name": 1,
    "sender.login": 1,
    "ref": 1,
    "head_commit.id": 1,
    "head_commit.message": 1,
    "commits.id": 1,
    "commits.message": 1,
    receivedAt: 1
  }
).sort({ _id: -1 }).limit(3)
```

### Things my team talk about that I don't know:

- mongooseDB
- 

### Preston's server .env.development and test:

PG_SUDO_USER=
PGUSER=
PGPASSWORD=password
PGHOST=localhost
PGPORT=5432
PGDATABASE=request_bin_development
MONGO_URL="mongodb://127.0.0.1:27017/request_bin_development"
MONGO_USER=
MONGO_PASSWORD=password
MONGO_DATABASE=request_bin_development or test
client .env development:
VITE_WEBHOOK_URL="http://localhost:3000"
.env.test
VITE_WEBHOOK_URL="http://localhost:3000/testing"
