# typescript-json-schema-function-bug

## Issue

**TypeScript Code**:

```ts
export type Handler = (props: {}) => string
export type HandlerObject = {
    prop: Handler
};
```

**Command**

```
typescript-json-schema index.ts HandlerObject
```

Expected Result:

```json
{
    "$schema": "http://json-schema.org/draft-07/schema#",
    "type": "object"
}
```

Actual Result:

```
{
    "$schema": "http://json-schema.org/draft-07/schema#",
    "properties": {
        "prop": {
            "type": "object"
        }
    },
    "type": "object"
}
```

### Workaround

Use method definition that is ignored https://github.com/YousefED/typescript-json-schema/pull/194.

```ts
export type HandlerObject = {
    prop(props: {}): string
};
```

## Changelog

See [Releases page](https://github.com/azu/typescript-json-schema-function-bug/releases).

## Running tests

Install devDependencies and Run `npm test`:

    npm test

## Contributing

Pull requests and stars are always welcome.

For bugs and feature requests, [please create an issue](https://github.com/azu/typescript-json-schema-function-bug/issues).

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## Author

- [github/azu](https://github.com/azu)
- [twitter/azu_re](https://twitter.com/azu_re)

## License

MIT © azu
