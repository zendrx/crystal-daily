# Athena 0.22.0: Now with Real‑Time Updates

April 25, 2026

Athena, the web framework for Crystal that feels like Symfony (but compiled), just released version 0.22.0. The headline: real‑time updates have arrived.

The new Mercure component brings server‑sent events (SSE) to Athena. It uses a dedicated Mercure hub to push updates from your backend to browsers or mobile apps. You publish an update from anywhere — a controller, a console command, a background worker — and clients receive it instantly over SSE.

Here is a basic example. Assuming a Mercure hub is running:

require "athena-mercure"

token_factory = AMC::TokenFactory::JWT.new ENV["MERCURE_JWT_SECRET"]
token_provider = AMC::TokenProvider::Factory.new token_factory, publish: ["*"]
hub = AMC::Hub.new ENV["MERCURE_URL"], token_provider, token_factory

update = AMC::Update.new(
  "https://example.com/my-topic",
  {message: "Hello world"}.to_json
)
hub.publish update

WebSockets work, but they do not fit every architecture. Mercure uses SSE behind the scenes — simpler, one‑way, and easy to scale because the connection manager is separate from your API service.

Also in this release:

- http and http‑kernel are now standalone shards. You can use them as the base for your own event‑driven framework without pulling in all of Athena.

- Macro code coverage reporting is now built into the Spec component. Set ATHENA_SPEC_COVERAGE_OUTPUT_DIR, run your compile‑time tests, and get reports compatible with Codecov.

- The old Size constraint has been split into two dedicated constraints: Count for collections and Length for strings. Breaking change, but the upgrade path is a simple find‑replace.

- Third‑party bundles are now possible. The MercureBundle is the first example, and the maintainer is inviting the community to create their own bundles. If you have a favourite shard, you could be the one to integrate it.

Athena continues to mature. Real‑time updates remove one of the last big reasons to reach for another framework. If you have not looked at Athena recently, 0.22.0 is a good moment to try again.

Full details and upgrade notes are in the forum post linked below.

Source: Crystal Forum – Athena 0.22.0 release announcement by Blacksmoke16
