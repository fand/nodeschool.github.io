nodeschool.github.io
====================

http://nodeschool.io/ internet web page

please fork it and send us improvements!

## Stickers, Badges and whatnots

These are in the `/images` directory, feel free to use for your events. In `images/make-a-sticker` there is a template for making a sticker too. Woop.

## Translations

If you would like to translate the nodeschool site into another language please make a pull request adding `languages/<language code>.json`.

To generate a new language file template automatically, run the following commands inside a clone of this repository:

```
npm install
npm run language <language code>
```

e.g. `npm run language es` to create a Spanish placeholder file or `npm run en-ca` to create a Canadian English one

This will generate your language file in the `languages/` folder with English placeholder text. Now just translate each line. You should also add your language to the `languages/languages.json` list.

When picking your language code, please use the correct code from the first column of this spreadsheet: http://en.wikiversity.org/wiki/ISO_639-1_language_matrix

The way translations are implemented is using 100% client-side javascript. When the page is loaded the users browser locale is detected (using [browser-locale](http://npmjs.org/browser-locale)) and a XHR request is made to the `languages` folder to try and fetch a JSON translation file for that locale. First we check for the full 5 character locale file (e.g. `en-us`) and if that doesn't exist we fallback to the 2 character version (`en`) and if that doesn't exist we just do nothing and show the default English version.

Translation files are a mapping of translations IDs to the translated strings. There is a separate file called `languages/selectors.json` which maps CSS selectors in markup to the translation IDs.

The good things about this approach:

- The site remains a static site. This means that contributing to the site is really easy as the entire site is just flat HTML, CSS, JS and JSON files
- When PRs get merged they are immediately deployed live to GitHub pages. This makes maintainence really nice as there is no manual deploy step.

The drawbacks of this approach:

- Only the English (default) version is indexed by search engines
- The English version briefly appears on page loads before the translated version is swapped in
