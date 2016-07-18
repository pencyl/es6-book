# Node.js support

## 6.2.2

Node 6.2.2 supports almost all of the ES6 features we'll be going through today, without the `--harmony` flag. It will eventually transition to a LTS (Long term support) release too.

## 5.12.0

Not complete but over 50% implemented, requires the `--harmony` flag to enable. The harmony flag enables *staged* features, they not yet ready for production.

```shell
node --harmony myfile.js
```

## Older

Versions previous to 5.x.x still support some ES6 features. For example 0.10.46 supports `const` with the `--harmony` flag, but doesn't support arrow functions.

You can find more detailed information on what is and isn't supported at [node.green](http://node.green/)
