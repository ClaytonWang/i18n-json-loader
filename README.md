[npm][npm-url]
[node][node-url]

# i18n-json-loader for Webpack

The `i18n-json-loader` folk from `translate-loader`. This loader can resolve like `color.en-US.json`,`color.zh-CN.json`,
they are not need at folder `**en_US/`,`**zh-CN/`.

## Install

```shell
npm install --save-dev i18n-json-loader
```

## Usage

The `i18n-json-loader` enables you to import/require translation modules that are "aliased"
during runtime to specific files, based on browser's locale.

**helloworld.js**
```js
import labels from "labels_nls.json";

console.debug(`${labels.helloWorld} (${labels.localeName})`);
```

**labels_nls.json**
```json
{
    "localeName": "Default",
    "helloWorld": "Hello World"
}
```

labels_nls.en-GB.json**
```json
{
    "localeName": "English",
    "helloWorld": "Hello World"
}
```

labels_nls.en-US.json**
```json
{
    "localeName": "English US",
    "helloWorld": "Hello World"
}
```

labels_nls.es.json**
```json
{
    "localeName": "Español",
    "helloWorld": "Hola Mundo"
}
```

labels_nls.pt.json**
```json
{
    "localeName": "Português",
    "helloWorld": "Olá Mundo"
}
```

**webpack.config.js**
```js
module.exports = {
    module: {
        rules: [{
            test: /_nls\.json$/,
            use: "i18n-json-loader?locales=en;en-US;es;pt"
        }]
    }
};
```

or

**webpack.config.js**
```js
module.exports = {
    module: {
        rules: [{
            test: /_nls\.json$/,
            use: [
                {
                    loader: "i18n-json-loader",
                    options: {
                        locales: [ "en", "en-US", "es", "pt" ]
                    }
                }
            ]
        }]
    }
};
```

## Maintainers

| [Clay Wang][clay] |

[npm-url]: https://www.npmjs.com/package/i18n-json-loader
[node-url]: https://nodejs.org

[clay]: https://github.com/claytonwang
