# Troubleshooting

<!-- toc -->

- [noflo-ui install and test](#noflo-ui-install-and-test)
  * [Symptom: Error when running grunt during noflo-ui installation: Module not found: Error: Cannot resolve module 'coffee-script/register'](#symptom-error-when-running-grunt-during-noflo-ui-installation-module-not-found-error-cannot-resolve-module-coffee-scriptregister)
  * [Symptom: Unable to parse README.md](#symptom-unable-to-parse-readmemd)
  * [Symptom: Cannot find index.html when testing the UI in the browser.](#symptom-cannot-find-indexhtml-when-testing-the-ui-in-the-browser)
- [noflo-rdf-components install and test](#noflo-rdf-components-install-and-test)
  * [Symptom: 'compare-rdf should print usage if given no command line arguments: Uncaught AssertionError: expected 1 to equal 2' when running ```mocha test```](#symptom-compare-rdf-should-print-usage-if-given-no-command-line-arguments-uncaught-assertionerror-expected-1-to-equal-2-when-running-mocha-test)
  * [Symptom: 'ImportError: No module named rdflib' when running ```mocha test```](#symptom-importerror-no-module-named-rdflib-when-running-mocha-test)
  * [Symptom: rdflib.plugin.PluginException: No plugin registered for (json-ld, )](#symptom-rdflibpluginpluginexception-no-plugin-registered-for-json-ld-)
  * [Symptom: ERROR: 'Could not compile stylesheet' when running ```mocha test```](#symptom-error--could-not-compile-stylesheet-when-running-mocha-test)
  * [Symptom: During "mocha test": Uncaught TypeError: callback is not a function at . . . noflo-rdf-components/node_modules/noflo-groups/node_modules/noflo-core/node_modules/noflo/lib/Component.js](#symptom-during-mocha-test-uncaught-typeerror-callback-is-not-a-function-at----noflo-rdf-componentsnode_modulesnoflo-groupsnode_modulesnoflo-corenode_modulesnoflolibcomponentjs)
- [noflo-server install and test](#noflo-server-install-and-test)
  * [Symptom: During "grunt build": Warning: failed to fetch https://raw.githubusercontent.com/noflo/noflo/master/component.json, got 404 "Not Found"](#symptom-during-grunt-build-warning-failed-to-fetch-httpsrawgithubusercontentcomnoflonoflomastercomponentjson-got-404-not-found)

<!-- tocstop -->

To re-generate the Table of Contents:
```bash
npm install --save markdown-toc
./node_modules/.bin/markdown-toc -i Getting-Started.md
```


## noflo-ui install and test

### Symptom: Error when running grunt during noflo-ui installation: Module not found: Error: Cannot resolve module 'coffee-script/register'
**Possible solution:** Before "grunt build"ing noflo-ui, you need to install coffee-script and run ```npm update```.

### Symptom: Unable to parse README.md
```
WARNING in ./~/bindings/README.md
Module parse failed: . . . /noflo-ui/node_modules/bindings/README.md Unexpected token (2:3)
You may need an appropriate loader to handle this file type.
```

**Possible solution:** None needed.  These seem to be harmless warnings.


### Symptom: Cannot find index.html when testing the UI in the browser.

**Possible solution:** You forgot to run ```grunt build```.


## noflo-rdf-components install and test

### Symptom: 'compare-rdf should print usage if given no command line arguments: Uncaught AssertionError: expected 1 to equal 2' when running ```mocha test```

**Possible solution:** Install python module rdflib:
```bash
pip install rdflib
```


### Symptom: 'ImportError: No module named rdflib' when running ```mocha test```

**Possible solution:** Install python module rdflib:
```bash
pip install rdflib
```


### Symptom: rdflib.plugin.PluginException: No plugin registered for (json-ld, <class 'rdflib.parser.Parser'>)

**Possible solution:** 


### Symptom: ERROR:  'Could not compile stylesheet' when running ```mocha test```

**Possible solution:**

### Symptom: During "mocha test": Uncaught TypeError: callback is not a function at . . . noflo-rdf-components/node_modules/noflo-groups/node_modules/noflo-core/node_modules/noflo/lib/Component.js

**Possible solution:**

## noflo-server install and test 

### Symptom: During "grunt build": Warning: failed to fetch https://raw.githubusercontent.com/noflo/noflo/master/component.json, got 404 "Not Found"

**Possible solution:**
