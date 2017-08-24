# AliasDOM
Alias DOM.

## Usage

Use it like this:

```js
const { Alias } = require('aliasdom');
const $el = Alias({
    join: true, // if alias names should be joined like routes
    '.header': {
        'input.search': {
            alias: 'search'
        },
        'div.user': {
            alias: 'user'
        }
    },
    '.content': {
        lazy: true, // if the children would be got only if they should
        'div.article': 'article',
        'div.operate': {
            alias: 'operation',
            'a.like': 'like',
            'input.comment': 'comment'
        }
    }
});
```

Then you would get:

```js
$el === {
    'search': /**/,
    'user': /**/,
    'article': /**/,
    'operation': /**/,
    'operation/like': /**/,
    'operation/comment': /**/
}
```
