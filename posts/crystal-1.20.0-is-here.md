# Crystal 1.20.0 Is Here

April 16, 2026 — The Crystal team has officially released version 1.20.0, packed with new features, critical security fixes, and performance improvements. This release includes 161 changes from 21 contributors since 1.19.1.

Let's break down what's new.

Security First: Request Smuggling Fix

This release patches a HTTP request smuggling vulnerability (CWE-444) in HTTP::Server. Servers behind certain vulnerable frontends could have been exploited. The fix: requests containing both Content-Length and Transfer-Encoding headers are now rejected. If you run Crystal web servers, upgrade immediately.

Process API Overhaul (RFC 0025)

The modern Process API is here, treating the command line as an array of strings — safer and more intuitive:

Old API
Process.run("crystal", ["tool", "format"])

New API
Process.run(["crystal", "tool", "format"])

The real gem? Process.capture and Process.capture_result — convenient methods for capturing process output without manual pipe juggling.

These APIs are currently experimental and marked with @[Experimental]. The team expects to stabilize them in the next release.

Execution Contexts: M:N Scheduling Lands

The multi-threading preview (-Dpreview_mt -Dexecution_context) keeps maturing. This release adds:

- M:N scheduling — fibers and system threads are now decoupled
- No more blocking on syscalls like getaddrinfo
- Adaptive scaling — the scheduler automatically spins up threads based on workload

Plan: Execution contexts become enabled by default in Crystal 1.21. Start testing your MT code now.

Performance & Systems Features

@[TargetFeature] Annotation (RFC 0020)

You can now write CPU-specific optimizations in a single binary:

@[TargetFeature("+avx2")]
private def foo_avx2
  # AVX2 optimized version
end

Perfect for SIMD code where you want a portable fallback plus AVX2/AVX512 variants. The program must detect CPU features at runtime and call the right function.

Linux io_uring Event Loop (Experimental)

For Linux users: compile with -Devloop=io_uring to try the new async I/O backend. Caveat: It's not always faster than epoll. With SQPOLL enabled (idle timing configurable), you might see gains — or spin at 100% CPU. Experiment carefully.

Kernel TLS Support

OpenSSL now supports Kernel TLS on Linux and FreeBSD by default (if enabled at the OS level with modprobe tls on Linux). Zero-copy TLS for better throughput.

LLVM 22.1 & 23.0 Support

Crystal 1.20 compiles with the latest LLVM releases.

Developer Experience Wins

Short Option Bundling in OptionParser

Finally! -ncb now parses as -n -c -b. No more typing every flag separately.

parser.on("-n", "--noop", "No operation")
parser.on("-c", "--check", "Check only")
parser.on("-b", "--brief", "Brief output")
# -ncb works!

StringScanner Improvements

Janelle Neen contributed multiple quality-of-life improvements: #peek_behind, #scan overloads for Int, and a better #inspect format.

WebSocket Sub-Protocol Negotiation

HTTP::WebSocket now properly handles the Sec-WebSocket-Protocol header.

OAuth Error Handling Fixed

The OAuth module now detects error responses even when providers return HTTP 200 with an error payload (yes, some do that).

Deprecations to Note

Mutex is soft-deprecated in favor of Sync::Mutex. The new implementation uses the improved algorithm introduced in Crystal 1.19. Update your code when you see the warning — the old name will eventually be hard-deprecated.

Full Changelog

For the complete list (all 161 changes), check the official release page on GitHub or the Crystal language blog.

Thanks

This release was made possible by 84codes and every other sponsor. If you use Crystal professionally, consider donating via OpenCollective to keep the momentum going.

Upgrade today: crystal upgrade or grab pre-built packages from crystal-lang.org/install.

161 changes. 21 contributors. One rock-solid release.
