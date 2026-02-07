# rsbuild-plugin-google-analytics

An Rsbuild plugin to setup Google Analytics in your website.

<p>
  <a href="https://npmjs.com/package/rsbuild-plugin-google-analytics">
   <img src="https://img.shields.io/npm/v/rsbuild-plugin-google-analytics?style=flat-square&colorA=564341&colorB=EDED91" alt="npm version" />
  </a>
  <img src="https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square&colorA=564341&colorB=EDED91" alt="license" />
  <a href="https://npmcharts.com/compare/rsbuild-plugin-google-analytics?minimal=true"><img src="https://img.shields.io/npm/dm/rsbuild-plugin-google-analytics.svg?style=flat-square&colorA=564341&colorB=EDED91" alt="downloads" /></a>
</p>

## Usage

Install:

```bash
npm add rsbuild-plugin-google-analytics -D
```

Add plugin to your `rsbuild.config.ts`:

```ts
// rsbuild.config.ts
import { pluginGoogleAnalytics } from 'rsbuild-plugin-google-analytics';

export default {
  plugins: [
    pluginGoogleAnalytics({
      // replace this with your Google tag ID
      // see: https://support.google.com/analytics/answer/9539598?hl=en
      id: 'G-xxxxxxxxxx',
    }),
  ],
};
```

## Options

Here are the available options:

| Name   | Type      | Description                        | Defaults    |
| ------ | --------- | ---------------------------------- | ----------- |
| id     | `string`  | Google tag ID                      | `undefined` |
| enable | `boolean` | Whether to enable Google Analytics | `true`      |

## TypeScript support

If you experience this error on UI side `window.gtag is not a function`, you may need to add types for [gtag](https://developers.google.com/tag-platform/gtagjs) by installing this package:

```bash
npm install --save-dev @types/gtag.js
```

and you also have to add it to the types in your `tsconfig.json`:

```json
{
  "compilerOptions": {
    "types": ["gtag.js"]
  }
}
```

Then you won't experience any TS errors with code like this:

```ts
if (isProd()) {
  gtag('event', 'exception', { description: err.message });
}
```

## License

[MIT](./LICENSE).
