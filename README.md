# DraftJS: Export ContentState to HTML

This is a module for [DraftJS](https://github.com/facebook/draft-js) that will export your editor content to semantic HTML.

It was extracted from [React-RTE](https://react-rte.org) and placed into a separate module for more general use. Hopefully it can be helpful in your projects.

## Installation

    npm install --save draft-js-export-html

## How to Use

```javascript
import {stateToHTML} from 'draft-js-export-html';
let html = stateToHTML(contentState);
```

## Options

You can optionally pass a second "options" argument to `stateToHTML` which should be an object with one or more of the following properties:

### `inlineStyles`

You can define rendering options for inline styles. This applies to built-in inline styles (e.g. `BOLD`) or your own custom inline styles (e.g. `RED`). You can specify which element/tag name will be used (e.g. use `<b>` instead of `<strong>` for `BOLD`). You can add custom attributes (e.g. `class="foo"`) or add some styling (e.g. `color: red`).

Example:

```javascript
let options = {
  inlineStyles: {
    // Override default element (`strong`).
    BOLD: {element: 'b'},
    ITALIC: {
      // Add custom attributes. You can also use React-style `className`.
      attributes: {class: 'foo'},
      // Use camel-case. Units (`px`) will be added where necessary.
      style: {fontSize: 12}
    },
    // Use a custom inline style. Default element is `span`.
    RED: {style: {color: '#900'}},
  },
};
let html = stateToHTML(contentState, options);
```


This project is still under development. If you want to help out, please open an issue to discuss or join us on [Slack](https://draftjs.slack.com/).

## License

This software is [BSD Licensed](/LICENSE).
