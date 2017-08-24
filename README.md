# AliasDOM
Alias DOM.

## Usage

Use it like this:

```js
const { Alias } = require('aliasdom');
const $el = Alias({
    join: true, // whether alias names should be joined like routes
    '.header': {
        'input.search': {
            alias: 'search'
        },
        'div.user': {
            alias: 'user'
        }
    },
    '.content': {
        lazy: true, // whether the children would be got only if they should
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
$el: {
    'search': /* the element of `.header input.search` */,
    'user': /* the element of `.header div.user` */,
    'article': /* the element of `.content div.article` */,
    'operation': /* the element of `.content div.operate` */,
    'operation/like': /* the element of `.content div.operate a.like` */,
    'operation/comment': /* the element of `.content div.operate input.comment` */
}
```

If `join` is set `false` or not set, then it is:

```js
$el: {
    'search': /* the element of `.header input.search` */,
    'user': /* the element of `.header div.user` */,
    'article': /* the element of `.content div.article` */,
    'operation': /* the element of `.content div.operate` */,
    'like': /* the element of `.content div.operate a.like` */,
    'comment': /* the element of `.content div.operate input.comment` */
}
```

When `lazy` is set `true`, the children would be retrieved with the getter functions executed.

## License

MIT
