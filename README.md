# Reality Check
## Chaos Engineering for Next.js and other monoliths

**Developers typically develop and test in unrealistically reliable environments.**

They also simply use their own apps less often than users do. Users therefore ecounter ephemeral failures more often, and some snowball into persistent broken states or confusing app behavior. Chaos engineering closes this specific gap between the development and production environments by making failures more common, which allows developers to develop against these edge cases more thoroughly and build resilient architecutre.

**Reality Check is built to intentionally introduce failure in Next.js apps** like shim application endpoint errors, response loss, latency, timeouts, websocket loss, and killed servers, both in the local development and CI testing environments.

The tool works by proxying incoming and outgoing requests using a Node shim, as well as mock service worker in the browser, and randomly introduces a mix of failure types.


## Get started

In your Next.js application directory, run:

```bash
npx realitycheck
```

This essentially runs the `next dev` command, but wrapped in a proxy, and also injects the MSW into the frontend code delivery to the browser.

## Goals:

- Open source
- Run locally or in CI with a single command
- Designed for application monoliths, not containers
- Application-level: Mess up your app, not your computer
- Opinionated defaults: By default, 1 in 3 requests trigger a failure mode
- Targeting: UI to target specific endpoints and failure modes, and dial others back
- Starting with Next.js, then compatibility with other frameworks