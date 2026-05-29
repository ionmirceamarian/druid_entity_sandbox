# druid_entity_sandbox

A browser-based sandbox for inspecting and testing Druid entity data transformations.

## What it does

`index.html` is a single-file tool that lets you load Druid entity JSON objects, write JavaScript expressions against them, and immediately see how the output merges back into the entity context — without needing a running Druid instance.

**Core workflow:**

1. **Import entities** — paste any JSON that contains a `$entityTypeName$` field (or an array of them). The tool registers each entity as a named context slot, e.g. `[[DBLink]]`.
2. **Define output targets** — pair a target (`@result`, `[[Entity]]`, or `[[Entity]].field`) with a JavaScript expression (typically an IIFE). Targets write back into the entity context or into standalone variables.
3. **Run the verifier** — executes all expressions in order, deep-merges results into the context, and displays the merged output for each target plus the full resulting context.

**Key features:**

- `[[EntityName]]` slot syntax inside expressions resolves to the live entity object from context.
- Collection entities (`*_Collection` type with an `items` array) are wrapped in a Proxy that exposes a `.Count` property alongside standard array access.
- Entity cards are editable in-place; changes sync to the context immediately.
- Light/dark theme toggle.

## Usage

Open `index.html` directly in a browser — no build step or server required.