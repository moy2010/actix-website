---
title: HTTP/2
---

import RenderCodeBlock from '@theme/CodeBlock';
import CodeBlock from '@site/src/components/code_block.js';
import { actixWebMajorVersion } from "@site/vars";

`actix-web` automatically upgrades connections to *HTTP/2* if possible.

# Negotiation

<!-- TODO: use rustls example -->

When either of the `rustls` or `openssl` features are enabled, `HttpServer` provides the [bind_rustls][bindrustls] method and [bind_openssl][bindopenssl] methods, respectively.

<!-- DEPENDENCY -->


<RenderCodeBlock className="language-toml">
{`[dependencies]
actix-web = { version = "${actixWebMajorVersion}", features = ["openssl"] }
openssl = { version = "0.10", features = ["v110"] }
`}
</RenderCodeBlock>

<CodeBlock example="http2" file="main.rs" section="main" />

Upgrades to HTTP/2 described in [RFC 7540 §3.2][rfcsection32] are not supported. Starting HTTP/2 with prior knowledge is supported for both cleartext and TLS connections ([RFC 7540 §3.4][rfcsection34]) (when using the lower level `actix-http` service builders).

> Check out [the TLS examples][examples] for concrete example.

[rfcsection32]: https://httpwg.org/specs/rfc7540.html#rfc.section.3.2
[rfcsection34]: https://httpwg.org/specs/rfc7540.html#rfc.section.3.4
[bindrustls]: https://docs.rs/actix-web/4/actix_web/struct.HttpServer.html#method.bind_rustls
[bindopenssl]: https://docs.rs/actix-web/4/actix_web/struct.HttpServer.html#method.bind_openssl
[tlsalpn]: https://tools.ietf.org/html/rfc7301
[examples]: https://github.com/actix/examples/tree/master/https-tls
