## Mini-modern Web Stack

Using a modern web development stack with minimal files by leveraging Deno.

- `deno` our JavaScript runtime and package manager
- `vite` the only build tool that matters
- `svelte` framework for building interfaces
- `sveltekit` out the box web app solutions e.g., routing
- `tailwindcss` flexible CSS framework

**NOTE:** `deno` (as of version `2.1.4`) doesn't support the generated
`./$types` used by SvelteKit. However, it seems that they're working on
[fixing this](https://github.com/denoland/deno/issues/26871#issuecomment-2476706636).
Refer to
[this issue](https://github.com/denoland/deno/issues/17248#issuecomment-2551393652)
for the nitty-gritty.

Consequently, the following won't work:

```ts
import type { PageLoad } from "./$types"; // ERROR: Unable to load local module.

export const load: PageLoad = async ({ fetch, params }) => {
	const res = await fetch(`/api/items/${params.id}`);
	const item = await res.json();

	return { item };
};
```

#### Getting Started

```shell
deno task dev
```

If you encounter an error, it's likely SvelteKit related. SvelteKit uses
scripts, which Deno disables by default.

Run the following to fix things:

```shell
deno install --allow-scripts=npm@sveltejs/kit@2.15.1
```
