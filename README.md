Difference between thsi file and the solace-dev-codelab is in package.JSON

`"scripts": {
  "watch": "nodemon --watch WordleCodeLab.md --exec \"claat export -o temp/ WordleCodeLab.md && npx kill-port 9090 && cd temp/WordleCodeLab && claat serve\""
  }`

Why difference, because Windows, and he used Mac which can run Liniux scripts, but Windows is special
