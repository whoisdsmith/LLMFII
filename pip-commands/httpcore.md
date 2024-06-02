---
tags: [786), 439, 440, 441), 433), 429), 428), 403), 365), 358, 362), 354), 333), 331), 313), 311), 310), 296), 305), 167), 236), 241, 243), 242, 244), 249), 235), 237), 221), 185), 223), 225), 168), 169), 190), 189), 139), 154), 153), 164), 121, 130), 100, 134), 129), 128), 102, 137), 101), 140), 112), 97), 98), 92), 89, 90), 83), 79), 81), 70)]
---

# Httpcore

## Description

A minimal low-level HTTP client.

## README

# HTTP Core

[![Test Suite](https://github.com/encode/httpcore/workflows/Test%20Suite/badge.svg)](https://github.com/encode/httpcore/actions)
[![Package version](https://badge.fury.io/py/httpcore.svg)](https://pypi.org/project/httpcore/)

> *Do one thing, and do it well.*

The HTTP Core package provides a minimal low-level HTTP client, which does
one thing only. Sending HTTP requests.

It does not provide any high level model abstractions over the API,
does not handle redirects, multipart uploads, building authentication headers,
transparent HTTP caching, URL parsing, session cookie handling,
content or charset decoding, handling JSON, environment based configuration
defaults, or any of that Jazz.

Some things HTTP Core does do:

* Sending HTTP requests.
* Thread-safe / task-safe connection pooling.
* HTTP(S) proxy & SOCKS proxy support.
* Supports HTTP/1.1 and HTTP/2.
* Provides both sync and async interfaces.
* Async backend support for `asyncio` and `trio`.

## Requirements

Python 3.8+

## Installation

For HTTP/1.1 only support, install with:

```shell
$ pip install httpcore
```

There are also a number of optional extras available...

```shell
$ pip install httpcore['asyncio,trio,http2,socks']
```

# Sending Requests

Send an HTTP request:

```python
import httpcore

response = httpcore.request("GET", "https://www.example.com/")

print(response)
# <Response [200]>
print(response.status)
# 200
print(response.headers)
# [(b'Accept-Ranges', b'bytes'), (b'Age', b'557328'), (b'Cache-Control', b'max-age=604800'), ...]
print(response.content)
# b'<!doctype html>\n<html>\n<head>\n<title>Example Domain</title>\n\n<meta charset="utf-8"/>\n ...'
```

The top-level `httpcore.request()` function is provided for convenience. In practice whenever you're working with `httpcore` you'll want to use the connection pooling functionality that it provides.

```python
import httpcore

http = httpcore.ConnectionPool()
response = http.request("GET", "https://www.example.com/")
```

Once you're ready to get going, [head over to the documentation](https://www.encode.io/httpcore/).

## Motivation

You *probably* don't want to be using HTTP Core directly. It might make sense if
you're writing something like a proxy service in Python, and you just want
something at the lowest possible level, but more typically you'll want to use
a higher level client library, such as `httpx`.

The motivation for `httpcore` is:

* To provide a reusable low-level client library, that other packages can then build on top of.
* To provide a *really clear interface split* between the networking code and client logic,
  so that each is easier to understand and reason about in isolation.

## Dependencies

The `httpcore` package has the following dependencies...

* `h11`
* `certifi`

And the following optional extras...

* `anyio` - Required by `pip install httpcore['asyncio']`.
* `trio` - Required by `pip install httpcore['trio']`.
* `h2` - Required by `pip install httpcore['http2']`.
* `socksio` - Required by `pip install httpcore['socks']`.

## Versioning

We use [SEMVER for our versioning policy](https://semver.org/).

For changes between package versions please see our [project changelog](CHANGELOG.md).

We recommend pinning your requirements either the most current major version, or a more specific version range:

```python
pip install 'httpcore==1.*'
```

# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

## 1.0.5 (March 27th, 2024)

- Handle `EndOfStream` exception for anyio backend. (#899)
- Allow trio `0.25.*` series in package dependencies. (#903)

## 1.0.4 (February 21st, 2024)

- Add `target` request extension. (#888)
- Fix support for connection `Upgrade` and `CONNECT` when some data in the stream has been read. (#882)

## 1.0.3 (February 13th, 2024)

- Fix support for async cancellations. (#880)
- Fix trace extension when used with socks proxy. (#849)
- Fix SSL context for connections using the "wss" scheme (#869)

## 1.0.2 (November 10th, 2023)

- Fix `float("inf")` timeouts in `Event.wait` function. (#846)

## 1.0.1 (November 3rd, 2023)

- Fix pool timeout to account for the total time spent retrying. (#823)
- Raise a neater RuntimeError when the correct async deps are not installed. (#826)
- Add support for synchronous TLS-in-TLS streams. (#840)

## 1.0.0 (October 6th, 2023)

From version 1.0 our async support is now optional, as the package has minimal dependencies by default.

For async support use either `pip install 'httpcore[asyncio]'` or `pip install 'httpcore[trio]'`.

The project versioning policy is now explicitly governed by SEMVER. See https://semver.org/.

- Async support becomes fully optional. (#809)
- Add support for Python 3.12. (#807)

## 0.18.0 (September 8th, 2023)

- Add support for HTTPS proxies. (#745, #786)
- Drop Python 3.7 support. (#727)
- Handle `sni_hostname` extension with SOCKS proxy. (#774)
- Handle HTTP/1.1 half-closed connections gracefully. (#641)
- Change the type of `Extensions` from `Mapping[Str, Any]` to `MutableMapping[Str, Any]`. (#762)

## 0.17.3 (July 5th, 2023)

- Support async cancellations, ensuring that the connection pool is left in a clean state when cancellations occur. (#726)
- The networking backend interface has [been added to the public API](https://www.encode.io/httpcore/network-backends). Some classes which were previously private implementation detail are now part of the top-level public API. (#699)
- Graceful handling of HTTP/2 GoAway frames, with requests being transparently retried on a new connection. (#730)
- Add exceptions when a synchronous `trace callback` is passed to an asynchronous request or an asynchronous `trace callback` is passed to a synchronous request. (#717)
- Drop Python 3.7 support. (#727)

## 0.17.2 (May 23th, 2023)

- Add `socket_options` argument to `ConnectionPool` and `HTTProxy` classes. (#668)
- Improve logging with per-module logger names. (#690)
- Add `sni_hostname` request extension. (#696)
- Resolve race condition during import of `anyio` package. (#692)
- Enable TCP_NODELAY for all synchronous sockets. (#651)

## 0.17.1 (May 17th, 2023)

- If 'retries' is set, then allow retries if an SSL handshake error occurs. (#669)
- Improve correctness of tracebacks on network exceptions, by raising properly chained exceptions. (#678)
- Prevent connection-hanging behaviour when HTTP/2 connections are closed by a server-sent 'GoAway' frame. (#679)
- Fix edge-case exception when removing requests from the connection pool. (#680)
- Fix pool timeout edge-case. (#688)

## 0.17.0 (March 16th, 2023)

- Add DEBUG level logging. (#648)
- Respect HTTP/2 max concurrent streams when settings updates are sent by server. (#652)
- Increase the allowable HTTP header size to 100kB. (#647)
- Add `retries` option to SOCKS proxy classes. (#643)

## 0.16.3 (December 20th, 2022)

- Allow `ws` and `wss` schemes. Allows us to properly support websocket upgrade connections. (#625)
- Forwarding HTTP proxies use a connection-per-remote-host. Required by some proxy implementations. (#637)
- Don't raise `RuntimeError` when closing a connection pool with active connections. Removes some error cases when cancellations are used. (#631)
- Lazy import `anyio`, so that it's no longer a hard dependency, and isn't imported if unused. (#639)

## 0.16.2 (November 25th, 2022)

- Revert 'Fix async cancellation behaviour', which introduced race conditions. (#627)
- Raise `RuntimeError` if attempting to us UNIX domain sockets on Windows. (#619)

## 0.16.1 (November 17th, 2022)

- Fix HTTP/1.1 interim informational responses, such as "100 Continue". (#605)

## 0.16.0 (October 11th, 2022)

- Support HTTP/1.1 informational responses. (#581)
- Fix async cancellation behaviour. (#580)
- Support `h11` 0.14. (#579)

## 0.15.0 (May 17th, 2022)

- Drop Python 3.6 support (#535)
- Ensure HTTP proxy CONNECT requests include `timeout` configuration. (#506)
- Switch to explicit `typing.Optional` for type hints. (#513)
- For `trio` map OSError exceptions to `ConnectError`. (#543)

## 0.14.7 (February 4th, 2022)

- Requests which raise a PoolTimeout need to be removed from the pool queue. (#502)
- Fix AttributeError that happened when Socks5Connection were terminated. (#501)

## 0.14.6 (February 1st, 2022)

- Fix SOCKS support for `http://` URLs. (#492)
- Resolve race condition around exceptions during streaming a response. (#491)

## 0.14.5 (January 18th, 2022)

- SOCKS proxy support. (#478)
- Add proxy_auth argument to HTTPProxy. (#481)
- Improve error message on 'RemoteProtocolError' exception when server disconnects without sending a response. (#479)

## 0.14.4 (January 5th, 2022)

- Support HTTP/2 on HTTPS tunnelling proxies. (#468)
- Fix proxy headers missing on HTTP forwarding. (#456)
- Only instantiate SSL context if required. (#457)
- More robust HTTP/2 handling. (#253, #439, #440, #441)

## 0.14.3 (November 17th, 2021)

- Fix race condition when removing closed connections from the pool. (#437)

## 0.14.2 (November 16th, 2021)

- Failed connections no longer remain in the pool. (Pull #433)

## 0.14.1 (November 12th, 2021)

- `max_connections` becomes optional. (Pull #429)
- `certifi` is now included in the install dependencies. (Pull #428)
- `h2` is now strictly optional. (Pull #428)

## 0.14.0 (November 11th, 2021)

The 0.14 release is a complete reworking of `httpcore`, comprehensively addressing some underlying issues in the connection pooling, as well as substantially redesigning the API to be more user friendly.

Some of the lower-level API design also makes the components more easily testable in isolation, and the package now has 100% test coverage.

See [discussion #419](https://github.com/encode/httpcore/discussions/419) for a little more background.

There's some other neat bits in there too, such as the "trace" extension, which gives a hook into inspecting the internal events that occur during the request/response cycle. This extension is needed for the HTTPX cli, in order to...

* Log the point at which the connection is established, and the IP/port on which it is made.
* Determine if the outgoing request should log as HTTP/1.1 or HTTP/2, rather than having to assume it's HTTP/2 if the --http2 flag was passed. (Which may not actually be true.)
* Log SSL version info / certificate info.

Note that `curio` support is not currently available in 0.14.0. If you're using `httpcore` with `curio` please get in touch, so we can assess if we ought to prioritize it as a feature or not.

## 0.13.7 (September 13th, 2021)

- Fix broken error messaging when URL scheme is missing, or a non HTTP(S) scheme is used. (Pull #403)

## 0.13.6 (June 15th, 2021)

### Fixed

- Close sockets when read or write timeouts occur. (Pull #365)

## 0.13.5 (June 14th, 2021)

### Fixed

- Resolved niggles with AnyIO EOF behaviours. (Pull #358, #362)

## 0.13.4 (June 9th, 2021)

### Added

- Improved error messaging when URL scheme is missing, or a non HTTP(S) scheme is used. (Pull #354)

### Fixed

- Switched to `anyio` as the default backend implementation when running with `asyncio`. Resolves some awkward [TLS timeout issues](https://github.com/encode/httpx/discussions/1511).

## 0.13.3 (May 6th, 2021)

### Added

- Support HTTP/2 prior knowledge, using `httpcore.SyncConnectionPool(http1=False)`. (Pull #333)

### Fixed

- Handle cases where environment does not provide `select.poll` support. (Pull #331)

## 0.13.2 (April 29th, 2021)

### Added

- Improve error message for specific case of `RemoteProtocolError` where server disconnects without sending a response. (Pull #313)

## 0.13.1 (April 28th, 2021)

### Fixed

- More resiliant testing for closed connections. (Pull #311)
- Don't raise exceptions on ungraceful connection closes. (Pull #310)

## 0.13.0 (April 21st, 2021)

The 0.13 release updates the core API in order to match the HTTPX Transport API,
introduced in HTTPX 0.18 onwards.

An example of making requests with the new interface is:

```python
with httpcore.SyncConnectionPool() as http:
    status_code, headers, stream, extensions = http.handle_request(
        method=b'GET',
        url=(b'https', b'example.org', 443, b'/'),
        headers=[(b'host', b'example.org'), (b'user-agent', b'httpcore')]
        stream=httpcore.ByteStream(b''),
        extensions={}
    )
    body = stream.read()
    print(status_code, body)
```

### Changed

- The `.request()` method is now `handle_request()`. (Pull #296)
- The `.arequest()` method is now `.handle_async_request()`. (Pull #296)
- The `headers` argument is no longer optional. (Pull #296)
- The `stream` argument is no longer optional. (Pull #296)
- The `ext` argument is now named `extensions`, and is no longer optional. (Pull #296)
- The `"reason"` extension keyword is now named `"reason_phrase"`. (Pull #296)
- The `"reason_phrase"` and `"http_version"` extensions now use byte strings for their values. (Pull #296)
- The `httpcore.PlainByteStream()` class becomes `httpcore.ByteStream()`. (Pull #296)

### Added

- Streams now support a `.read()` interface. (Pull #296)

### Fixed

- Task cancellation no longer leaks connections from the connection pool. (Pull #305)

## 0.12.3 (December 7th, 2020)

### Fixed

- Abort SSL connections on close rather than waiting for remote EOF when using `asyncio`. (Pull #167)
- Fix exception raised in case of connect timeouts when using the `anyio` backend. (Pull #236)
- Fix `Host` header precedence for `:authority` in HTTP/2. (Pull #241, #243)
- Handle extra edge case when detecting for socket readability when using `asyncio`. (Pull #242, #244)
- Fix `asyncio` SSL warning when using proxy tunneling. (Pull #249)

## 0.12.2 (November 20th, 2020)

### Fixed

- Properly wrap connect errors on the asyncio backend. (Pull #235)
- Fix `ImportError` occurring on Python 3.9 when using the HTTP/1.1 sync client in a multithreaded context. (Pull #237)

## 0.12.1 (November 7th, 2020)

### Added

- Add connect retries. (Pull #221)

### Fixed

- Tweak detection of dropped connections, resolving an issue with open files limits on Linux. (Pull #185)
- Avoid leaking connections when establishing an HTTP tunnel to a proxy has failed. (Pull #223)
- Properly wrap OS errors when using `trio`. (Pull #225)

## 0.12.0 (October 6th, 2020)

### Changed

- HTTP header casing is now preserved, rather than always sent in lowercase. (#216 and python-hyper/h11#104)

### Added

- Add Python 3.9 to officially supported versions.

### Fixed

- Gracefully handle a stdlib asyncio bug when a connection is closed while it is in a paused-for-reading state. (#201)

## 0.11.1 (September 28nd, 2020)

### Fixed

- Add await to async semaphore release() coroutine (#197)
- Drop incorrect curio classifier (#192)

## 0.11.0 (September 22nd, 2020)

The Transport API with 0.11.0 has a couple of significant changes.

Firstly we've moved changed the request interface in order to allow extensions, which will later enable us to support features
such as trailing headers, HTTP/2 server push, and CONNECT/Upgrade connections.

The interface changes from:

```python
def request(method, url, headers, stream, timeout):
    return (http_version, status_code, reason, headers, stream)
```

To instead including an optional dictionary of extensions on the request and response:

```python
def request(method, url, headers, stream, ext):
    return (status_code, headers, stream, ext)
```

Having an open-ended extensions point will allow us to add later support for various optional features, that wouldn't otherwise be supported without these API changes.

In particular:

* Trailing headers support.
* HTTP/2 Server Push
* sendfile.
* Exposing raw connection on CONNECT, Upgrade, HTTP/2 bi-di streaming.
* Exposing debug information out of the API, including template name, template context.

Currently extensions are limited to:

* request: `timeout` - Optional. Timeout dictionary.
* response: `http_version` - Optional. Include the HTTP version used on the response.
* response: `reason` - Optional. Include the reason phrase used on the response. Only valid with HTTP/1.*.

See https://github.com/encode/httpx/issues/1274#issuecomment-694884553 for the history behind this.

Secondly, the async version of `request` is now namespaced as `arequest`.

This allows concrete transports to support both sync and async implementations on the same class.

### Added

- Add curio support. (Pull #168)
- Add anyio support, with `backend="anyio"`. (Pull #169)

### Changed

- Update the Transport API to use 'ext' for optional extensions. (Pull #190)
- Update the Transport API to use `.request` and `.arequest` so implementations can support both sync and async. (Pull #189)

## 0.10.2 (August 20th, 2020)

### Added

- Added Unix Domain Socket support. (Pull #139)

### Fixed

- Always include the port on proxy CONNECT requests. (Pull #154)
- Fix `max_keepalive_connections` configuration. (Pull #153)
- Fixes behaviour in HTTP/1.1 where server disconnects can be used to signal the end of the response body. (Pull #164)

## 0.10.1 (August 7th, 2020)

- Include `max_keepalive_connections` on `AsyncHTTPProxy`/`SyncHTTPProxy` classes.

## 0.10.0 (August 7th, 2020)

The most notable change in the 0.10.0 release is that HTTP/2 support is now fully optional.

Use either `pip install httpcore` for HTTP/1.1 support only, or `pip install httpcore[http2]` for HTTP/1.1 and HTTP/2 support.

### Added

- HTTP/2 support becomes optional. (Pull #121, #130)
- Add `local_address=...` support. (Pull #100, #134)
- Add `PlainByteStream`, `IteratorByteStream`, `AsyncIteratorByteStream`. The `AsyncByteSteam` and `SyncByteStream` classes are now pure interface classes. (#133)
- Add `LocalProtocolError`, `RemoteProtocolError` exceptions. (Pull #129)
- Add `UnsupportedProtocol` exception. (Pull #128)
- Add `.get_connection_info()` method. (Pull #102, #137)
- Add better TRACE logs. (Pull #101)

### Changed

- `max_keepalive` is deprecated in favour of `max_keepalive_connections`. (Pull #140)

### Fixed

- Improve handling of server disconnects. (Pull #112)

## 0.9.1 (May 27th, 2020)

### Fixed

- Proper host resolution for sync case, including IPv6 support. (Pull #97)
- Close outstanding connections when connection pool is closed. (Pull #98)

## 0.9.0 (May 21th, 2020)

### Changed

- URL port becomes an `Optional[int]` instead of `int`. (Pull #92)

### Fixed

- Honor HTTP/2 max concurrent streams settings. (Pull #89, #90)
- Remove incorrect debug log. (Pull #83)

## 0.8.4 (May 11th, 2020)

### Added

- Logging via HTTPCORE_LOG_LEVEL and HTTPX_LOG_LEVEL environment variables
and TRACE level logging. (Pull #79)

### Fixed

- Reuse of connections on HTTP/2 in close concurrency situations. (Pull #81)

## 0.8.3 (May 6rd, 2020)

### Fixed

- Include `Host` and `Accept` headers on proxy "CONNECT" requests.
- De-duplicate any headers also contained in proxy_headers.
- HTTP/2 flag not being passed down to proxy connections.

## 0.8.2 (May 3rd, 2020)

### Fixed

- Fix connections using proxy forwarding requests not being added to the
connection pool properly. (Pull #70)

## 0.8.1 (April 30th, 2020)

### Changed

- Allow inherintance of both `httpcore.AsyncByteStream`, `httpcore.SyncByteStream` without type conflicts.

## 0.8.0 (April 30th, 2020)

### Fixed

- Fixed tunnel proxy support.

### Added

- New `TimeoutException` base class.

## 0.7.0 (March 5th, 2020)

- First integration with HTTPX.