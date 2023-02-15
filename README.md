_<h1 align='center'>zhead</h1>

<p align="center">
<a href='https://github.com/harlan-zw/zhead/actions/workflows/test.yml'>
</a>
<a href="https://www.npmjs.com/package/zhead" target="__blank"><img src="https://img.shields.io/npm/v/zhead?style=flat&colorA=002438&colorB=28CF8D" alt="NPM version"></a>
<a href="https://www.npmjs.com/package/zhead" target="__blank"><img alt="NPM Downloads" src="https://img.shields.io/npm/dm/zhead?flat&colorA=002438&colorB=28CF8D"></a>
<a href="https://github.com/harlan-zw/zhead" target="__blank"><img alt="GitHub stars" src="https://img.shields.io/github/stars/harlan-zw/zhead?flat&colorA=002438&colorB=28CF8D"></a>
</p>


<p align="center">
All the types you need for your &lt;head&gt;.<br><br>Powering <a href="https://github.com/harlan-zw/unhead">Unhead</a>.
</p>

<p align="center">
<table>
<tbody>
<td align="center">
<img width="800" height="0" /><br>
<i>Status:</i> Stable</b> <br>
<sup> Please report any issues 🐛</sup><br>
<sub>Made possible by my <a href="https://github.com/sponsors/harlan-zw">Sponsor Program 💖</a><br> Follow me <a href="https://twitter.com/harlan_zw">@harlan_zw</a> 🐦 • Join <a href="https://discord.gg/275MBUBvgP">Discord</a> for help</sub><br>
<img width="800" height="0" />
</td>
</tbody>
</table>
</p>

## Features

- 💎 Fully typed Head schema
- 💎 Commented with MDN docs
- 💎 Fully Augmentable
- 💎 [100+ typed meta's](https://github.com/harlan-zw/zhead/blob/main/packages/schema/src/metaFlat.ts)

## Installation

```bash
npm install --save-dev zhead

# Using yarn
yarn add --dev zhead
```

## Types

### Head

Typescript base schema for document &lt;head&gt;.

```ts
export interface Head<E extends MergeHead = MergeHead> {
  title?: string
  titleTemplate?: string | ((title?: string) => string)
  base?: Partial<Merge<E['base'], Base>>
  link?: (Link & UnsafeKeys & Default<E['link']>)[]
  meta?: (Meta & UnsafeKeys & Default<E['meta']>)[]
  style?: (Style & UnsafeKeys & Default<E['style']>)[]
  script?: (Script & UnsafeKeys & Default<E['script']>)[]
  noscript?: (Noscript & UnsafeKeys & Default<E['noscript']>)[]
  htmlAttrs?: (HtmlAttributes & UnsafeKeys & Default<E['htmlAttrs']>)
  bodyAttrs?: (BodyAttributes & UnsafeKeys & Default<E['bodyAttrs']>)
}
```

### Flat Meta

See [metaFlat.ts](/src/metaFlat.ts) for the full list.

```ts
// SAMPLE

export interface MetaFlat {
    /**
     * This attribute declares the document's character encoding.
     * If the attribute is present, its value must be an ASCII case-insensitive match for the string "utf-8",
     * because UTF-8 is the only valid encoding for HTML5 documents.
     * <meta> elements which declare a character encoding must be located entirely within the first 1024 bytes
     * of the document.
     *
     * @see https://developer.mozilla.org/en-US/docs/Web/HTML/Element/meta#attr-charset
     */
    charset: string
    /**
     * Use this tag to provide a short description of the page.
     * In some situations, this description is used in the snippet shown in search results.
     *
     * @see https://developers.google.com/search/docs/advanced/appearance/snippet#meta-descriptions
     */
    description: string
    /**
     * This tag tells the browser how to render a page on a mobile device.
     * Presence of this tag indicates to Google that the page is mobile friendly.
     *
     * @see https://developer.mozilla.org/en-US/docs/Web/HTML/Element/meta/name#standard_metadata_names_defined_in_other_specifications
     */
    viewport: string | Partial<{
      /**
       * Defines the pixel width of the viewport that you want the web site to be rendered at.
       */
      width: number | string | 'device-width'
      /**
       * Defines the height of the viewport. Not used by any browser.
       */
      height: number | string | 'device-height'
      /**
       * Defines the ratio between the device width
       * (device-width in portrait mode or device-height in landscape mode) and the viewport size.
       *
       * @minimum 0
       * @maximum 10
       */
      initialScale: number | string
      /**
       * Defines the maximum amount to zoom in.
       * It must be greater or equal to the minimum-scale or the behavior is undefined.
       * Browser settings can ignore this rule and iOS10+ ignores it by default.
       *
       * @minimum 0
       * @maximum 10
       */
      maximumScale: number | string
      /**
       * Defines the minimum zoom level. It must be smaller or equal to the maximum-scale or the behavior is undefined.
       * Browser settings can ignore this rule and iOS10+ ignores it by default.
       *
       * @minimum 0
       * @maximum 10
       */
      minimumScale: number | string
      /**
       * If set to no, the user is unable to zoom in the webpage.
       * The default is yes. Browser settings can ignore this rule, and iOS10+ ignores it by default.
       */
      userScalable: 'yes' | 'no'
      /**
       * The auto value doesn't affect the initial layout viewport, and the whole web page is viewable.
       *
       * The contain value means that the viewport is scaled to fit the largest rectangle inscribed within the display.
       *
       * The cover value means that the viewport is scaled to fill the device display.
       * It is highly recommended to make use of the safe area inset variables to ensure that important content
       * doesn't end up outside the display.
       */
      viewportFit: 'auto' | 'contain' | 'cover'
  }>

  // ...
}
```

## API

### defineHead

Use this decorator for a simple fully-typed head schema.

```ts
import { defineHead } from 'zhead'

const head = defineHead({
  title: 'My Page',
})

// {
//    title: 'My Page',
// }
```

## Sponsors

<p align="center">
  <a href="https://raw.githubusercontent.com/harlan-zw/static/main/sponsors.svg">
    <img src='https://raw.githubusercontent.com/harlan-zw/static/main/sponsors.svg'/>
  </a>
</p>


## License

MIT License © 2022-PRESENT [Harlan Wilton](https://github.com/harlan-zw)_
