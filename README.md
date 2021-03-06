# @webdeb/next-styles

### CSS + SASS + Modules in Next.js

---

## Description

This module allows you to use css (+ optional [sass, modules]) all in one package.
It uses the latest modules available css-loader, sass-loader, postcss. Check out the sources, its dead simple.

## Why?

Because I found it cumbersome to deal with the official packages from next-plugins to setup css + sass + modules.
So I created this one. It has everything I need for my project, most projects, I believe.

## Install

```sh
npm install @webdeb/next-styles
```

## Use

```js
// next.config.js
const withStyles = require('@webdeb/next-styles')

module.exports = withStyles({
  sass: true, // use .scss files
  modules: true, // style.(m|module).css & style.(m|module).scss for module files
  sassLoaderOptions: {
    sassOptions: {
      includePaths: ["src/styles"], // @import 'variables'; # loads (src/styles/varialbes.scss), you got it..
    },
  },
  cssLoaderOptions: {...},
  postcssLoaderOptions: {...}
})
```

_Hint: Look at the source of truth: `withStyles.js`_

## Known Issues

This project inherits a known next-css problem. https://github.com/zeit/next-plugins/issues/282

If your pages where you are importing css are not working, you are probably facing exactly this problem. The workaround is to load a css/scss file (can be even empty) into your \_app.js.

```js
import "../styles/global.scss"

export default function MyApp({ Component, pageProps }) {
  return <Component {...pageProps} />
}
```

## Credits

Most of the code was taken from the official `next-css` & `next-sass` package.
