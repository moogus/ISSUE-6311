## TURBO REPO EXAMPLE OF [`--filter=[origin/{whatever}] not working as expected`](https://github.com/vercel/turbo/issues/6311)

### Steps to reproduce
**Script set up for turbo**
```
/* root package.json */
"scripts": {
		"tsc": "turbo run tsc --filter=[origin/main] --no-daemon"
	},
```
**Install**
```
yarn #install all packages
```
**Edit a package**
#### [component-one](https://github.com/moogus/ISSUE-6311/blob/main/components/component-one/index.ts)
```
 export const fooBar = { foo: 'foo', bar: 'bar' }; // => edit this line
 export const fooBar = { foo: 'foo', baz: 'bar' }; // => to this 
```
**Run Turbo command**
```
yarn tsc  #from root of repo
```

#### Expected behavior
Only the component-one package should be checked for TSC errors as it is the only one that has been changed.

#### Actual behavior
All packages are checked for TSC errors, this does not happen if `"turbo": "1.5.6"` is used in the root package.json.

_Please note if nothing has changed all packages are checked anyway, which is not the behaviour in `1.5.6`_