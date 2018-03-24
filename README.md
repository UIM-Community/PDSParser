# PDSParser
PDS Configuration file parser

## Getting started

This package is available in the Node Package Repository and can be easily installed with [npm](https://docs.npmjs.com/getting-started/what-is-npm) or [yarn](https://yarnpkg.com).

```bash
$ npm i pdsparser
# or
$ yarn add pdsparser
``` 

Example of parsing a UIM Configuration file

```xml
<setup>
	loglevel = 5
	probes = cdm,dirscan,processes
</setup>
```

```js
const pdsparser = require('pdsparser');

async function main() {
	const config = await (new pdsparser('./script.cfg')).read();
	
	const loglevel 	= config.setup.loglevel || 5;
	const probes 	= (config.setup.probes || '').split(',');
}
main().catch(console.error);
```

Use destructuration to simplify readability

```js
const {
	setup: { 
		loglevel = 5,
		probes = ''
	}
} = await (new pdsparser('./script.cfg')).read();
```
