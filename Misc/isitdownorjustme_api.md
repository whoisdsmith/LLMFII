---
aliases:
  - isitdownorjustme-API
tags:
  - "#api"
  - "#developer-tools"
  - "#software-development"

  - "#website-monitoring"
  - "#web-development"
  - "#nodejs"
---
## Getting Started

<img width="1439" alt="hero" src="https://user-images.githubusercontent.com/54872601/172040997-c82f58f2-54ca-4e3a-9735-4b40c9ee61ac.png">

### Full Tutorial
https://1998design.medium.com/how-to-get-website-status-with-website-monitor-api-a396e945c007

First, run the development server:

```bash
npm run dev
# or
yarn dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

[API routes] This endpoint can be edited in `pages/api/public.js`.

## How to use
1. METHOD: GET
2. API Path: http://localhost:3000/api/public?url=<WEBSITE_URL><br/>
2a. Local API Sample: http://localhost:3000/api/public?url=https://apple.com or<br/>
2b. Testing API Sample: https://monitor-api.vercel.app/api/public?url=https://apple.com
3. Return: `{
    "status": 200,
    "statusText": "OK",
    "isUP": true,
    "isDown": false
}`

<img width="610" alt="Resp json" src="https://user-images.githubusercontent.com/54872601/172040973-2b9204bd-6b7d-4939-8bfc-c41b737ff1e9.png">

## Questions?
- Please open an issue or ask in discussion section.
