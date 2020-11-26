> **:warning: as of version 1.0.0, this package name has been changed from
> `react-native-render-html-table-bridge` to `@native-html/table-plugin`**. To
> migrate, you must add the new package in your project and change imports.
> Also, [check all breaking changes here](https://github.com/native-html/table-plugin/blob/master/packages/table-plugin/CHANGELOG.md#100-2020-08-19).

<h1 align="center">@native-html/table-plugin</h1>

<p align="center">
  <a href="https://www.npmjs.com/package/@native-html/table-plugin"
    ><img
      src="https://img.shields.io/npm/v/@native-html/table-plugin"
      alt="npm"
  /></a>
  <a href="https://semver.org/spec/v2.0.0.html"
    ><img
      src="https://img.shields.io/badge/semver-2.0.0-e10079.svg"
      alt="semver"
  /></a>
  <a href="https://codecov.io/gh/native-html/table-plugin"
    ><img
      src="https://codecov.io/gh/native-html/table-plugin/branch/master/graph/badge.svg"
      alt="codecov"
  /></a>
  <a
    href="https://github.com/native-html/table-plugin/actions?query=branch%3Amaster+workflow%3ACI"
    ><img
      src="https://github.com/native-html/table-plugin/workflows/CI/badge.svg?branch=master"
      alt="CI"
  /></a>
  <img
    src="https://img.shields.io/npm/dm/@native-html/table-plugin.svg"
    alt="DL/month"
  />
</p>

<p align="center">
  🔠 A WebView-based plugin to render tables in react-native-render-html.
</p>

<p align="center">
  <img
    src="https://github.com/native-html/table-plugin/raw/master/images/expo-example.png"
  />
</p>
<div align="center">
  <a href="https://expo.io/@jsamr/native-html-table-plugin-example"
    >Try it on Expo!</a
  >
</div>
<div align="center">
  <img
    src="https://github.com/native-html/table-plugin/raw/master/images/android.gif"
    width="300"
  />
</div>
<hr/>

```sh
npm add --save @native-html/table-plugin
```

```sh
yarn add @native-html/table-plugin
```

**Features**:

- Render HTML tables with a `WebView` component you provide;
- Supports `HTML.onLinkPress` prop to handle clicks;
- Automatic height;
- Customize table style with ease.

**Known Limitations**:

- Don't forget you're rendering cells inside a webview, so you won't be able to apply your custom renderers there
- Limited support of Expo &lt;33 version ; full support [&ge;33 versions](https://github.com/expo/expo/milestone/22) (see bellow limitation)
- Autoheight behavior and `onLinkPress` config options only work with [`WebView` &ge; `v5.0.0` community edition](https://github.com/react-native-community/react-native-webview/releases/tag/v5.0.0)

## Minimal working example

_[Full example](example/SimpleExample.js)_

You need 3 conditions to get to a working example:

1. Provide import for `WebView` component. [Instructions will differ depending on your setup](#errors-when-importing-webview-component);
2. Inject `alterNode` and `ignoredTags` props to `HTML` component;
3. `makeTableRenderer` and inject `renderers` prop to `HTML` component.

```javascript
import React from 'react';
import { ScrollView } from 'react-native';
import HTML from 'react-native-render-html';
import {
  IGNORED_TAGS,
  alterNode,
  makeTableRenderer
} from '@native-html/table-plugin';
import WebView from 'react-native-webview';

const html = `
<table>
  <tr>
    <th>Entry Header 1</th>
    <th>Entry Header 2</th>
  </tr>
  <tr>
    <td>Entry First Line 1</td>
    <td>Entry First Line 2</td>
  </tr>
</table>
`;

const renderers = {
  table: makeTableRenderer({ WebView })
};

const htmlConfig = {
  alterNode,
  renderers,
  ignoredTags: IGNORED_TAGS
};

export const Example = () => (
  <ScrollView>
    <HTML html={html} {...htmlConfig} />
  </ScrollView>
);
```

## API Reference

**The complete API reference is available here: [docs/table-plugin.md](docs/table-plugin.md).**
Most notably, check [`TableConfig`](docs/table-plugin.tableconfig.md) to see how you can customize the table behavior.

**Landmark exports**:

- [`makeTableRenderer`](docs/table-plugin.maketablerenderer.md)
- [`makeCustomTableRenderer`](docs/table-plugin.makecustomtablerenderer.md)
- [`alterNode`](docs/table-plugin.alternode.md)
- [`IGNORED_TAGS`](docs/table-plugin.ignored_tags.md)

Other exports:

- [`HTMLTable`](docs/table-plugin.htmltable.md)
- [`defaultTableStylesSpecs`](docs/table-plugin.defaulttablestylesspecs.md)
- [`cssRulesFromSpecs`](docs/table-plugin.cssrulesfromspecs.md)
- [`TABLE_TAGS`](docs/table-plugin.table_tags.md)

## Troubleshooting

<a name="errors-when-importing-webview-component" />

### Errors when importing `WebView` component

> :warning: **Always favor
> [`react-native-community/react-native-webview`](https://github.com/react-native-community/react-native-webview)
> over legacy `WebView` when possible.**

Setting up `WebView` component largely vary on your `react-native` or `expo` version.
Please refer to the official documentation and make sure you have selected your RN / Expo SDK version:

- [Expo](https://docs.expo.io/versions/latest/sdk/webview/);
- [React Native](https://facebook.github.io/react-native/docs/webview).

### Typescript errors

If you encounter typescript errors, chances are you are not following `peerDependencies` rules. Make sure you follow these rules:

| react-native-render-html | @native-html/table-plugin |
| ------------------------ | ------------------------- |
| ≤ 4.2.0                  | ≤ 0.5.3                   |
| ≥ 4.2.1                  | ≥ 0.6.0                   |

## FAQ

### How to easily style the table?

Use `TableConfig.tableStyleSpecs`. The options will get merged with defaults,
so you are not required to pass every field. See
[documentation](docs/table-plugin.tablestylespecs.md).

```javascript
import {
  defaultTableStylesSpecs,
  cssRulesFromSpecs
} from '@native-html/table-plugin';

const renderers = {
  table: makeTableRenderer({
    tableStyleSpecs: {
      // my style specs
    }
  })
};
```

### How to disable autoheight?

Pass `computeContainerHeight` option with a function returning `null`:

```javascript
import {
  defaultTableStylesSpecs,
  cssRulesFromSpecs
} from '@native-html/table-plugin';

const renderers = {
  table: makeTableRenderer({
    computeContainerHeight() {
      return null;
    }
  })
};
```

<a name="extend-styles" />

### How to extend default or custom styles?

**A**: Use `cssRulesFromSpecs` function and override `cssRules` config.

```javascript
import {
  defaultTableStylesSpecs,
  cssRulesFromSpecs
} from '@native-html/table-plugin';

const cssRules =
  cssRulesFromSpecs(defaultTableStylesSpecs) +
  `
a {
  text-transform: uppercase;
}
`;

const renderers = {
  table: makeTableRenderer({
    cssRules
  })
};
```

### How to customize the Table component?

**A**: Use `makeCustomTableRenderer` function. [See custom example](example/CustomExample.js).

<img src="https://github.com/native-html/table-plugin/raw/master/images/adaptative.jpeg" width="300">

### How to load custom fonts?

**A**: Extend styles and add `@font-face` rules.

```javascript
import {
  defaultTableStylesSpecs,
  cssRulesFromSpecs
} from '@native-html/table-plugin';
import { Platform } from 'react-native';

function getFontAssetURL(fontFileName: string) {
  return Platform.select({
    ios: `url(${fontFileName})`,
    android: `url(file://android_asset/fonts/${fontFileName})`
  });
}

const openSansUnicodeRanges =
  'U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD';

const openSansRegular = getFontAssetURL('OpenSans-Regular.ttf');

const cssRules =
  cssRulesFromSpecs({
    ...defaultTableStylesSpecs,
    fontFamily: '"Open Sans"' // beware to quote font family name!
  }) +
  `
@font-face {
  font-family: 'Open Sans';
  font-style: normal;
  font-weight: 400;
  src: ${openSansRegular}, format('ttf');
  unicode-range: ${openSansUnicodeRanges};
}
`;

const renderers = {
  table: makeTableRenderer({
    cssRules
    // Other config options
  })
};
```