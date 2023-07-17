`npm init -y`

`npm install --save-dev --save-exact prettier`

`npm init stylelint`

***

Below step is only needed if using **_scss_**

`npm install --save-dev stylelint stylelint-config-standard-scss`

Edit **_.stylelintrc.json_** with below code:

`{
  "extends": ["stylelint-config-standard-scss"]
}`

***

Add necessary rules in **_.stylelintrc.json_** from [here](https://stylelint.io/user-guide/rules)

`npx husky-init -and npm install`

`npm install --save-dev lint-staged`


***


**Inside _package.json_, insert after _devDependencies_**

``` json
 "lint-staged": {
    "*.{css,scss}" : ["stylelint", "prettier --write"],
    "*.html": "prettier --write"
  }
```


**Folder example**

``` json
"lint-staged": {
  "src/scss/**/*.scss" : ["stylelint", "prettier --write"],
  "src/app/**/*.html" : "prettier --write"
}
```

_will match all scss files inside the src/scss directory_

_will match all html files inside the src/app directory_

**also**

``` json
"src/**/*.{html,scss}" : "prettier --write"
```

_**.prettierignore**_ file is considered when running lint staged

***

**Inside _.husky/pre-commit_, add the below line**

`npx lint-staged`

**_Its better to include .vscode folder, stylelintrc.json, .prettierrc.json from this repo while using for other projects._**
