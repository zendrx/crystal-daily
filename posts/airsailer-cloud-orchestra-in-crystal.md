# Airsailer: Open Source Cloud Orchestrator in Crystal

April 16, 2026

Airsailer is an open-source cloud orchestrator written entirely in Crystal.

This is significant because cloud orchestration — managing infrastructure across AWS, Azure, GCP, and beyond — has traditionally been dominated by Go and Rust. Terraform, Pulumi, Crossplane, OpenTofu — all written in Go.

Airsailer is the first serious entry in this space written in Crystal.

Why does that matter?

Crystal offers a unique combination for infrastructure tooling:

1. Native compilation to a single binary — easy to deploy in CI/CD pipelines or air-gapped environments
2. Memory safety without a garbage collector pause — important for control planes
3. Ruby-like syntax — operators and platform engineers can read and contribute to orchestration logic
4. Low resource footprint — runs anywhere

Details are still emerging from the announcement on the Crystal Forum, but early signals suggest Airsailer focuses on:

- Multi-cloud deployment workflows
- Infrastructure as code with Crystal DSL
- State management and drift detection

This is one to watch. If you're building cloud infrastructure, keep an eye on Airsailer as it develops.

Check the Crystal Forum for the full announcement and source links.

---

Crystal in the cloud. Finally.
