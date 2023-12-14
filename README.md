# Reality Check
## Chaos Engineering for Next.JS and other monoliths

Developers typically develop and test applications in an *unrealistically reliable* environment.

Sometimes, users can just hit refresh. But some failure modes are more serious and result in lingering broken states or confusing application behavior for users if side effects are not idempotent, retry is not utilized correctly, databases communication is not scoped to transactions, alongside many, many other scenarios. Users encounter these situations more often than developers for a range of reasons, including that cloud environments typically involve more networking than local development, automated tests usually mock services as reliably successful, and users' use patterns are much heavier than developers and so they are more likely to hit ephemeral failures.

Reality Check aims to expose more failure modes more frequently by introducing shim application endpoint failures, response loss, latency, timeouts, websocket loss, and killed servers into the local development and CI testing environment. This helps the developer build towards more resilient architectures.

The tool works by proxying incoming and outgoing requests using a Node shim, as well as mock service worker in the browser, and randomly introduces a mix of failure types.

## Get started

In your Next.JS application directory, run:

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
- Starting with Next.JS, then compatibility with other frameworks