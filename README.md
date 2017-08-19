# Webpack TypeScript Knowledge

<p align="center">
	<img src="./images/webpack.png" alt="Vue" height="128" style="vertical-align: bottom;">
	<img src="./images/ts.png" alt="Vue" height="128" style="vertical-align: bottom;">
</p>
<br>

📚 My knowledge from using [webpack](https://webpack.js.org/) and [TypeScript](https://www.typescriptlang.org/) _(and [Vue](https://vuejs.org/))_. 

<br>

## ⚔️ Node Execution

- [ts-node](https://github.com/TypeStrong/ts-node)
  - How to run with non-`commonjs` `module` in `tsconfig.json`? (Why? See [TypeStrong/ts-node#212](https://github.com/TypeStrong/ts-node/issues/212))  
    ✅ Use `TS_NODE_COMPILER_OPTIONS={\\\"module\\\":\\\"commonjs\\\"}` with [`cross-env`](https://github.com/kentcdodds/cross-env).

    ```json
	{
		"scripts": {
			"run-ts": "cross-env TS_NODE_COMPILER_OPTIONS={\\\"module\\\":\\\"commonjs\\\"} script.ts"
		}
	}
    ```

## <img src="./images/webpack.png" alt="Vue" height="32" align="top"> webpack

- Type declaration:
  - [`@types/webpack`](https://npm.im/@types/webpack)
  - [`@types/node`](https://npm.im/@types/node)

  ```bash
  npm install --save-dev @types/node @types/webpack
  # or
  yarn add @types/node @types/webpack
  ```
- How to run config `webpack.config.ts` with non-`commonjs` `module` in `tsconfig.json`? (Why? See [TypeStrong/ts-node#212](https://github.com/TypeStrong/ts-node/issues/212))  
  ✅ Use `TS_NODE_COMPILER_OPTIONS={\\\"module\\\":\\\"commonjs\\\"}` with [`cross-env`](https://github.com/kentcdodds/cross-env).

  ```json
  {
	  "scripts": {
		  "bundle": "cross-env TS_NODE_COMPILER_OPTIONS={\\\"module\\\":\\\"commonjs\\\"} webpack"
	  }
  }
  ```

### Loader

- [ts-loader](https://github.com/TypeStrong/ts-loader)
  - How to use with [vue](https://vuejs.org/)?  
    ✅ Add [`appendTsSuffixTo`](https://github.com/TypeStrong/ts-loader#appendtssuffixto-regexp-default) option.

    ```javascript
	{
		test: /\.ts$/,
		loader: 'ts-loader',
		options: {
			appendTsSuffixTo: [/\.vue$/]
		}
	}
    ```

## [<img src="./images/vue.png" alt="Vue" height="32" align="top"> Vue](https://vuejs.org/)

- Recommended `tsconfig.json` config.

  ```json
  {
	  "compilerOptions": {
		  "allowSyntheticDefaultImports": true,
		  "lib": [
			  "dom",
			  "es5",
			  "es2015"
		  ],
		  "module": "es2015",
		  "moduleResolution": "node",
		  "experimentalDecorators": true // For using decorator
	  }
  }
  ```

- Decorator:
  - [vue-class-component](https://github.com/vuejs/vue-class-component)  
    > Decorator for class-style Vue component.
  - [vue-property-decorator](https://github.com/kaorun343/vue-property-decorator)  
    > Decorator for Vue component property.
