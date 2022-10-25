<p align="center">
 <img align="center" alt="Vitest Preview Logo" src="https://user-images.githubusercontent.com/8603085/197406675-dbe5b555-3a71-4c6d-9547-776c18052881.svg" width="120"/>
</p>

<h1 align="center">
<a href="https://www.vitest-preview.com" target="_blank" >Vitest Preview</a>
</h1>

<p align="center">
Debug your Vitest tests. Effortlessly. 🧪🖼⚡️
</p>

<p align="center">
  <img align="center" src="https://user-images.githubusercontent.com/8603085/197373376-f6a3fe33-487b-4c35-8085-8e7e6357ce40.gif" alt="Vitest Preview Demo" />
</p>

<p align="center">
  <a href="https://stackblitz.com/edit/vitest-preview?file=src%2FApp.test.tsx,README.md" title="Try Vitest Preview Now" target="_blank">Try Vitest Preview Online</a>. No downloads needed!
</p>

[![npm version](https://img.shields.io/npm/v/vitest-preview)](https://www.npmjs.com/package/vitest-preview)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-green.svg)](./CONTRIBUTING.md)

[![Try Vitest Preview now](https://developer.stackblitz.com/img/open_in_stackblitz.svg)](https://stackblitz.com/edit/vitest-preview?file=src%2FApp.test.tsx,README.md)

## Why **vitest-preview**

When writing tests, we usually have to debug by reading the cryptic HTML output on the terminal. Sometimes, they are too complicated to visualize the UI in our heads. `vitest-preview` previews your Vitest tests right in a browser, then you can see your actual UI visually. You can write tests and watch rendered output changes accordingly. Vitest Preview lets you concentrate on tests in the "real world" rather than deciphering HTML code.

`vitest-preview` is built on top of [Vite](https://vitejs.dev), it's blazing fast and easy to use.

`vitest-preview` is a younger sibling of [`jest-preview`](https://github.com/nvh95/jest-preview) with the same idea and to solve the same problem. If you are writing tests using Jest, [give it a try](https://stackblitz.com/edit/jest-preview?file=src%2FApp.test.tsx,README.md).

## Features

- 👀 Visualize your testing UI in an external browser in milliseconds.
- 🔄 Auto reloads the browser when `debug()` is executed.
- 💅 Fully support CSS
- 🌄 Support viewing images.

## Installation

```bash
npm install --save-dev vitest-preview
# Or
yarn add -D vitest-preview
pnpm add -D vitest-preview
```

## Configuration

### Process CSS

You need to configure `vitest` to process CSS by:

```diff
// vite.config.js
export default defineConfig({
  test: {
+    css: true,
  },
});

```

You might want to import your CSS global files in `setupFiles`:

```diff
// vite.config.js
export default defineConfig({
  test: {
+    setupFiles: './src/test/setup.ts',
  },
});

```

```diff
// src/test/setup.ts
+import './global.css';
+import '@your-design-system/css/dist/index.min.css';
+import 'bootstrap/dist/css/bootstrap.min.css';

```

### Add script vitest-preview

`vitest-preview` has a CLI that opens **Vitest Preview Dashboard** where you can preview your tests' UI. You can update your `package.json` to add a script for more convenience:

```json
"scripts": {
  "vitest-preview": "vitest-preview"
},
```

### Update .gitignore

Update your `.gitignore`

```diff
// .gitignore
+.vitest-preview
```

## Usage

Put `debug()` wherever you want to see the UI in your tests.

```diff
+import { debug } from 'vitest-preview';

describe('App', () => {
  it('should work as expected', () => {
    render(<App />);
+    debug();
  });
});
```

Open the **Vitest Preview Dashboard** by running the CLI command (updated in [Configuration](#configuration)):

```bash
npm run vitest-preview
# Or
yarn vitest-preview
pnpm vitest-preview
```

Then execute your tests that contain `debug()`. You will see the UI of your tests at [http://localhost:5006](http://localhost:5006).

## Examples

- [react-testing-library](https://github.com/nvh95/vitest-preview/tree/main/examples/react-testing-library)
- [@vue/test-utils](https://github.com/nvh95/vitest-preview/tree/main/examples/vue-test-utils)

## Contributing

Please see the contribution guide at [CONTRIBUTING.md](./CONTRIBUTING.md).

## Is there a similar library for Jest

Yes, it is. It's [Jest Preview](https://github.com/nvh95/jest-preview).

## Star history

[![Star History Chart](https://api.star-history.com/svg?repos=nvh95/vitest-preview&type=Date)](https://star-history.com/#nvh95/vitest-preview&Date)

## License

![This is open source software](https://user-images.githubusercontent.com/8603085/161439058-98faea42-c6e6-46f4-9ce6-218fad5f3b9a.gif)

MIT

## Support

If you like the project, please consider supporting it by giving a ⭐️ to encourage the author.

<!-- TODO: Write a GitHub Actions to sync with root readme -->
