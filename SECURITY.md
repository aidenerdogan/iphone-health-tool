# Security policy

Please report vulnerabilities privately through GitHub Security Advisories once
the repository is published. Do not include sensitive diagnostic payloads in a
public issue.

The supported product path uses public platform capabilities and keeps
diagnostic data on the local computer unless the user explicitly exports it.
Independently implemented device-protocol adapters are optional, read-only in
the first release, and isolated from the supported path.

Imported logs, screenshots, archives, and device metadata are untrusted input.
The application must never execute imported content or perform a device
mutation without explicit confirmation.
