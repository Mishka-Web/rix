# Rix

Experimental direct reactive UI framework for building fast interfaces with signals, DOM bindings and optional `.rix` syntax.

Rix is not production-ready yet. The first goal is to build a small working runtime without React, Vue or any other UI framework.

## Idea

Rix follows a simple principle:

```txt
state changes → exact DOM updates
```

Instead of rerendering the whole component, Rix should update only the exact DOM parts that depend on changed state.

## Planned features

* Signals
* Effects
* Computed values
* Direct DOM bindings
* Components
* Conditional rendering
* List rendering
* Router
* `.rix` compiler syntax
* UI kit

## Future `.rix` syntax

```rix
component Counter {
  state count = 0

  action increment {
    count++
  }

  view {
    <button @click="increment">
      Count: {count}
    </button>
  }
}
```

## Runtime example

Before the `.rix` compiler exists, Rix will work through a TypeScript runtime API.

```ts
import { signal, h, mount } from "@rix/core";

function App() {
  const count = signal(0);

  return h(
    "button",
    {
      onClick: () => count.set(count() + 1),
    },
    "Count: ",
    () => count()
  );
}

mount("#app", App);
```

## Repository structure

```txt
rix/
  packages/
    core/
  examples/
    counter/
  docs/
    roadmap.md
    philosophy.md
```

## Current status

Early experimental stage.

The first milestone is `@rix/core` with:

* `signal()`
* `effect()`
* `h()`
* `mount()`
* working counter example

## License

MIT
