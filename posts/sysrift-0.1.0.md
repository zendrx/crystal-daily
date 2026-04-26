# Sysrift v0.1.0: A Crystal Alternative to linPEAS

April 18, 2026

Sysrift is a static-compiled Linux privilege escalation checker written entirely in Crystal.

Unlike linPEAS, which is 35,000+ lines of noisy Bash, Sysrift is a single self-contained binary with zero runtime dependencies.

Why Crystal for a security tool?

Crystal's ability to compile with --static targeting musl libc produces an executable you can drop in /dev/shm, run, and delete — leaving almost no forensic footprint.

What Sysrift currently covers:

- SUID/SGID binaries with GTFOBins cross-referencing
- sudo CVEs including Baron Samedit
- Kernel CVEs including DirtyCow and Dirty Pipe
- Container escape detection
- Cron job analysis
- Writable system paths
- Environment variable vulnerabilities
- And 14 other high-signal vectors

Output is severity-tagged with a post-run summary that surfaces only critical and medium findings.

Sysrift is not trying to replace linPEAS entirely — at least not yet. But it shows what's possible when you write security tooling in a compiled, memory-safe language that still feels productive.

Check it out: search for "sysrift v0.1.0" on the Crystal Forum.

---

One binary. No dependencies. Just results.
