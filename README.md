# TURBO REPO EXAMPLE OF [--filter=[origin/{whatever}] not working as expected](https://github.com/vercel/turbo/issues/6311)

```
yarn #install all packages
```bash

[component-one](#components/component-one/index.ts)
```
 export const fooBar = { foo: 'foo', bar: 'bar' }; // => edit this line

 export const fooBar = { foo: 'foo', baz: 'bar' }; // => to this 
```js

```
yarn tsc  #from root of repo
```bash

#### Expected behavior
only the component-one should be checked for TSC errors as it is the only one that has been changed