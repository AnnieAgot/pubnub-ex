# Pubnub Build Failure Demo

This is a barebones Sveltekit repo, setup with as described in the default README below. It is also set to use `adapter-node`.

Create a `.env` file with required keys:

```
VITE_PUBLISH_KEY=pub-...
VITE_SUBSCRIBE_KEY=...
VITE_SECRET_KEY=...
```

Run in dev mode (`npm run dev`). Send messages to the channel configured in `Messaging.svelte`. The messages should be logged and a counter incremented in the ui.

Running a build, `npm run build` will fail:

```sh
> pubnub-ex@0.0.1 build
> vite build


vite v4.3.9 building SSR bundle for production...
✓ 50 modules transformed.

vite v4.3.9 building for production...
✓ 44 modules transformed.
.svelte-kit/output/client/_app/version.json                               0.03 kB │ gzip:  0.05 kB
.svelte-kit/output/client/vite-manifest.json                              1.83 kB │ gzip:  0.37 kB
.svelte-kit/output/client/_app/immutable/nodes/0.6ca3df57.js              0.55 kB │ gzip:  0.37 kB
.svelte-kit/output/client/_app/immutable/nodes/1.350b4922.js              0.98 kB │ gzip:  0.57 kB
.svelte-kit/output/client/_app/immutable/chunks/singletons.708cc683.js    2.84 kB │ gzip:  1.46 kB
.svelte-kit/output/client/_app/immutable/entry/app.3327755a.js            5.50 kB │ gzip:  2.19 kB
.svelte-kit/output/client/_app/immutable/chunks/index.6dba6488.js         7.06 kB │ gzip:  2.86 kB
.svelte-kit/output/client/_app/immutable/entry/start.ce9861be.js         23.99 kB │ gzip:  9.51 kB
.svelte-kit/output/client/_app/immutable/nodes/2.80713574.js            188.76 kB │ gzip: 47.60 kB
✓ built in 1.55s
.svelte-kit/output/server/vite-manifest.json                   1.31 kB
.svelte-kit/output/server/internal.js                          0.19 kB
.svelte-kit/output/server/entries/fallbacks/layout.svelte.js   0.24 kB
.svelte-kit/output/server/entries/pages/_page.svelte.js        0.88 kB
.svelte-kit/output/server/entries/fallbacks/error.svelte.js    0.89 kB
.svelte-kit/output/server/chunks/index.js                      3.27 kB
.svelte-kit/output/server/chunks/internal.js                   5.36 kB
.svelte-kit/output/server/index.js                            86.29 kB

Run npm run preview to preview your production build locally.

> Using @sveltejs/adapter-node
Circular dependency: node_modules/pubnub/lib/event-engine/states/handshake_reconnecting.js -> node_modules/pubnub/lib/event-engine/states/handshake_failure.js -> node_modules/pubnub/lib/event-engine/states/handshake_reconnecting.js
Circular dependency: node_modules/pubnub/lib/event-engine/states/handshaking.js -> node_modules/pubnub/lib/event-engine/states/handshake_reconnecting.js -> node_modules/pubnub/lib/event-engine/states/handshake_failure.js -> node_modules/pubnub/lib/event-engine/states/handshake_stopped.js -> node_modules/pubnub/lib/event-engine/states/handshaking.js
Circular dependency: node_modules/pubnub/lib/event-engine/states/unsubscribed.js -> node_modules/pubnub/lib/event-engine/states/handshaking.js -> node_modules/pubnub/lib/event-engine/states/handshake_reconnecting.js -> node_modules/pubnub/lib/event-engine/states/receiving.js -> node_modules/pubnub/lib/event-engine/states/unsubscribed.js
Circular dependency: node_modules/pubnub/lib/event-engine/states/receiving.js -> node_modules/pubnub/lib/event-engine/states/receive_reconnecting.js -> node_modules/pubnub/lib/event-engine/states/receiving.js
Circular dependency: node_modules/pubnub/lib/event-engine/states/receive_reconnecting.js -> node_modules/pubnub/lib/event-engine/states/receive_failure.js -> node_modules/pubnub/lib/event-engine/states/receive_reconnecting.js
Circular dependency: node_modules/pubnub/lib/event-engine/states/receiving.js -> node_modules/pubnub/lib/event-engine/states/receive_reconnecting.js -> node_modules/pubnub/lib/event-engine/states/receive_failure.js -> node_modules/pubnub/lib/event-engine/states/receive_stopped.js -> node_modules/pubnub/lib/event-engine/states/receiving.js
Circular dependency: node_modules/pubnub/lib/event-engine/states/unsubscribed.js -> node_modules/pubnub/lib/event-engine/states/handshaking.js -> node_modules/pubnub/lib/event-engine/states/unsubscribed.js
Circular dependency: node_modules/semver/classes/comparator.js -> node_modules/semver/classes/range.js -> node_modules/semver/classes/comparator.js
Circular dependency: node_modules/superagent/lib/node/index.js -> node_modules/superagent/lib/node/agent.js -> node_modules/superagent/lib/node/index.js
Circular dependency: node_modules/ftp/node_modules/readable-stream/lib/_stream_readable.js -> node_modules/ftp/node_modules/readable-stream/lib/_stream_duplex.js -> node_modules/ftp/node_modules/readable-stream/lib/_stream_readable.js
Circular dependency: node_modules/ftp/node_modules/readable-stream/lib/_stream_duplex.js -> node_modules/ftp/node_modules/readable-stream/lib/_stream_writable.js -> node_modules/ftp/node_modules/readable-stream/lib/_stream_duplex.js
error during build:
RollupError: Illegal reassignment of import "commonjsRequire" in "node_modules/formidable/lib/incoming_form.js".
    at error (file:///home/anne/Dev/pubnub-ex/node_modules/rollup/dist/es/shared/node-entry.js:2124:30)
    at Module.error (file:///home/anne/Dev/pubnub-ex/node_modules/rollup/dist/es/shared/node-entry.js:13463:16)
    at Identifier.disallowImportReassignment (file:///home/anne/Dev/pubnub-ex/node_modules/rollup/dist/es/shared/node-entry.js:8285:29)
    at Identifier.deoptimizePath (file:///home/anne/Dev/pubnub-ex/node_modules/rollup/dist/es/shared/node-entry.js:8172:18)
    at AssignmentExpression.applyDeoptimizations (file:///home/anne/Dev/pubnub-ex/node_modules/rollup/dist/es/shared/node-entry.js:8920:19)
    at AssignmentExpression.hasEffects (file:///home/anne/Dev/pubnub-ex/node_modules/rollup/dist/es/shared/node-entry.js:8846:18)
    at ExpressionStatement.hasEffects (file:///home/anne/Dev/pubnub-ex/node_modules/rollup/dist/es/shared/node-entry.js:5762:28)
    at IfStatement.hasEffects (file:///home/anne/Dev/pubnub-ex/node_modules/rollup/dist/es/shared/node-entry.js:10632:33)
    at BlockStatement.hasEffects (file:///home/anne/Dev/pubnub-ex/node_modules/rollup/dist/es/shared/node-entry.js:8533:22)
    at FunctionDeclaration.hasEffectsOnInteractionAtPath (file:///home/anne/Dev/pubnub-ex/node_modules/rollup/dist/es/shared/node-entry.js:9047:27)
```

# create-svelte

Everything you need to build a Svelte project, powered by [`create-svelte`](https://github.com/sveltejs/kit/tree/master/packages/create-svelte).

## Creating a project

If you're seeing this, you've probably already done this step. Congrats!

```bash
# create a new project in the current directory
npm create svelte@latest

# create a new project in my-app
npm create svelte@latest my-app
```

## Developing

Once you've created a project and installed dependencies with `npm install` (or `pnpm install` or `yarn`), start a development server:

```bash
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

## Building

To create a production version of your app:

```bash
npm run build
```

You can preview the production build with `npm run preview`.

> To deploy your app, you may need to install an [adapter](https://kit.svelte.dev/docs/adapters) for your target environment.
