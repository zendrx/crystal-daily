# Crystal 1.20.1 is out

April 29, 2026

Crystal 1.20.1 just dropped. It's a small patch release, two days after 1.20.0.

9 changes. 2 contributors.

What got fixed:

A regression in Range#sample that could lose randomness. Now fixed.

Kernel TLS was introduced in 1.20.0 but showed issues in production. Some problems were fixed, but enough remain that Kernel TLS is now disabled by default. You can still opt in manually with ENABLE_KTLS if you know what you're doing.

If you already upgraded to 1.20.0, this is a safe upgrade. If you're on an older version, 1.20.1 is the new stable.

Pre-built packages are on GitHub Releases and the usual install channels.

Full changelog is on the Crystal language blog.

---

Patch releases aren't exciting. But they keep the train on the tracks.
