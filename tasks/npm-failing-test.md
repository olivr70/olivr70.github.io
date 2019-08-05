## Fork de npm CLI , `npm test` échoue

Voir le [Forum npm](https://npm.community/)

### Description

Fork de npm/cli dans olivr70/cli

Clone, lancement des tests, éhec du test `npm test`

Pour relancer uniquement le test :
`./node_modules/.bin/tap -o lifecyle-path.tap test/broken-under-nyc-and-travis/lifecycle-path.js`

Fiche sur
[Contribution issue : failing test after fork "lifecycle-path.js" - 🐞 bugs - npm forum](https://npm.community/t/contribution-issue-failing-test-after-fork-lifecycle-path-js/9149)

### Action

Création d'une PR
[Corrected test/lifecycle-path.js by olivr70 · Pull Request #228 · npm/cli](https://github.com/npm/cli/pull/228)
