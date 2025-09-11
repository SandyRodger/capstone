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

### Steps to get the final app working on my machine:

- at the end of this process you will have 3 servers running:
  - express
  - vite
  - ngrok

1. in the server directory create these 2 files:

```.env.development
PG_SUDO_USER=sandyboy
PGUSER=sandyboy
PGPASSWORD=password
PGHOST=localhost
PGPORT=5432
PGDATABASE=request_bin
MONGO_URL="mongodb://127.0.0.1:27017/request_bin_development"
MONGO_USER=
MONGO_PASSWORD=password
MONGO_DATABASE=request_bin
```

```.env.test
VITE_WEBHOOK_URL="http://localhost:3000/testing"
```

2. Install webhooks

```
npm install ws
npm install --save-dev @types/ws
```

3. run the postgres schema

```
psql -U sandyboy -d request_bin -f src/db/postgres/schema.sql
```

4. change `/Users/sandyboy/Desktop/request-bin/client/src/components/BinPage/BinPageContent.tsx` line 30 to your ngrok link:

`strictly-fluent-llama.ngrok-free.app/{selectedBin.id}`

5. start ngrok with:

`ngrok http --url=strictly-fluent-llama.ngrok-free.app 3000`

6. test it out with POSTMAN and it should work.


### ssh from EC2 instance

The key fingerprint is:
SHA256:1RVU57NrkaCpcOQD41w4OrJjzTh9l87b0P0sdIkGevc abmrodger@gmail.com
The key's randomart image is:
+--[ED25519 256]--+
|             .+oo|
|        .  . . ..|
|       = o. .. ..|
|      + B. .o . +|
|   . o +S+.o. .+.|
|    B . o.=..= oo|
|   * + . =..+.oo |
|  . o . + o  .+E |
|         +..  .o |
+----[SHA256]-----+

- `eval "$(ssh-agent -s)"` ->Agent pid 49884
- `ssh-add ~/.ssh/github`

PORT=3000
DATABASE_URL=postgres://postgres:master-my-babs11@<rds-endpoint>:5432/<db>?sslmode=require
MONGO_URL=mongodb://<user>:<pass>@<docdb-endpoint>:27017/<db>?tls=true&replicaSet=rs0&readPreference=secondaryPreferred&retryWrites=false
ENV
