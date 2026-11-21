# autocatalog plugins

Plugins for [autocatalog](https://github.com/jagreehal/autocatalog). Each one
teaches `ac` to read a tool's own files and writes what it finds into a file
the catalog reads.

| Package                                                       | Command              | Reads                          |
| ------------------------------------------------------------- | -------------------- | ------------------------------ |
| [`autocatalog-plugin-kong`](packages/plugin-kong)             | `ac from-kong`       | Kong declarative configuration |
| [`autocatalog-plugin-kubernetes`](packages/plugin-kubernetes) | `ac from-kubernetes` | Kubernetes NetworkPolicies     |
| [`autocatalog-plugin-storybook`](packages/plugin-storybook)   | `ac from-storybook`  | A Storybook build              |
| [`autocatalog-plugin-odcs`](packages/plugin-odcs)             | `ac from-odcs`       | ODCS data contracts            |

Install one next to autocatalog and its command appears:

```bash
npm install --save-dev autocatalog autocatalog-plugin-kong
npx ac from-kong kong.yaml
```

## Writing your own

Every plugin here imports only from `autocatalog-core/plugin`, the part of core
a plugin builds on. Start from
[Writing a plugin](https://jagreehal.github.io/autocatalog/docs/plugins) and copy
the smallest package here that does what you need.

## Working here

```bash
pnpm install
pnpm turbo run build typecheck test
pnpm verify:components   # publishes examples/components through two plugins
pnpm verify:rest-apis    # publishes examples/rest-apis through Kong and Kubernetes
```

The plugins install `autocatalog-core` and `autocatalog-cli` from npm, as yours
would. A change that needs a new core release lands in
[autocatalog](https://github.com/jagreehal/autocatalog) first.

Add a changeset with `pnpm changeset` for any change to a published package.
