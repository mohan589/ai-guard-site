# AI Guard

**Native macOS endpoint protection for sensitive data used by local AI agents.**

AI Guard is a pre-release endpoint data-protection application. It evaluates sensitive file access
before data is returned to local AI tools, developer automation, and other processes.

> **Product status:** Entitlement review in progress. AI Guard is being prepared for signed and
> notarized macOS distribution and is not currently offered as a public download.

## Protection model

Optional shell and tool wrappers cannot cover applications that open files directly. AI Guard adds
a native authorization boundary for new sensitive-file opens and keeps policy decisions local.

- **Process attribution:** Associates covered requests with process, executable, user, and
  responsible-process metadata.
- **Local policy:** Evaluates configured sensitive paths and returns an explicit allow or deny
  decision.
- **Durable audit:** Records protected decisions locally with bounded, owner-controlled audit data.

## Apple Endpoint Security usage

The requested entitlement is used by the system extension with bundle identifier
`com.aiguard.endpoint-security`.

AI Guard:

- Subscribes to `ES_EVENT_TYPE_AUTH_OPEN`.
- Evaluates new read opens using file-path and process metadata.
- Responds with the allowed flags or denies the open.
- Protects configured locations such as environment files, private keys, cloud credentials, browser
  credential stores, and administrative policy files.

AI Guard does **not**:

- Read or copy file contents through Endpoint Security.
- Use Endpoint Security data for advertising, tracking, or profiling.
- Silently activate without user or administrator approval.
- Claim complete network or API mediation in the current release.

## Privacy by design

Authorization processing occurs on the endpoint. Enterprise audit delivery is optional,
administrator-configured, redacted, and limited to policy and process metadata rather than
sensitive file contents.

This public repository contains only the static product page. It contains no private application
source, credentials, signing material, analytics, cookies, or client-side scripts.

The standalone GitHub Pages version is prepared at
<https://mohan589.github.io/ai-guard-site/> and will become available after Pages is enabled for
this repository.
