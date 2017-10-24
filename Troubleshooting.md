# Troubleshooting

**Table of Contents**

<!-- toc -->

- [noflo-ui Repository](#noflo-ui-repository)
  * [Error when running grunt during noflo-ui installation: Module not found: Error: Cannot resolve module 'coffee-script/register'](#error-when-running-grunt-during-noflo-ui-installation-module-not-found-error-cannot-resolve-module-coffee-scriptregister)
  * [Unable to parse README.md](#unable-to-parse-readmemd)
  * [Cannot find index.html when testing the UI in the browser.](#cannot-find-indexhtml-when-testing-the-ui-in-the-browser)
- [noflo-rdf-components Repository](#noflo-rdf-components-repository)
  * ['compare-rdf should print usage if given no command line arguments: Uncaught AssertionError: expected 1 to equal 2' when running ```mocha test```](#compare-rdf-should-print-usage-if-given-no-command-line-arguments-uncaught-assertionerror-expected-1-to-equal-2-when-running-mocha-test)
  * ['ImportError: No module named rdflib' when running ```mocha test```](#importerror-no-module-named-rdflib-when-running-mocha-test)
  * [rdflib.plugin.PluginException: No plugin registered for (json-ld, )](#rdflibpluginpluginexception-no-plugin-registered-for-json-ld-)
  * [ERROR: 'Could not compile stylesheet' when running ```mocha test```](#error--could-not-compile-stylesheet-when-running-mocha-test)
  * [During "mocha test": Uncaught TypeError: callback is not a function at . . . noflo-rdf-components/node_modules/noflo-groups/node_modules/noflo-core/node_modules/noflo/lib/Component.js](#during-mocha-test-uncaught-typeerror-callback-is-not-a-function-at----noflo-rdf-componentsnode_modulesnoflo-groupsnode_modulesnoflo-corenode_modulesnoflolibcomponentjs)
- [noflo-server Repository](#noflo-server-repository)
  * [During "grunt build": Warning: failed to fetch https://raw.githubusercontent.com/noflo/noflo/master/component.json, got 404 "Not Found"](#during-grunt-build-warning-failed-to-fetch-httpsrawgithubusercontentcomnoflonoflomastercomponentjson-got-404-not-found)

<!-- tocstop -->

To re-generate the Table of Contents:
```bash
npm install --save markdown-toc
./node_modules/.bin/markdown-toc -i Troubleshooting.md
```

--------------------
## noflo-ui Repository

### Error when running grunt during noflo-ui installation: Module not found: Error: Cannot resolve module 'coffee-script/register'

Before "grunt build"ing noflo-ui, you need to install coffee-script and run ```npm update```.


### Unable to parse README.md
```
WARNING in ./~/bindings/README.md
Module parse failed: . . . /noflo-ui/node_modules/bindings/README.md Unexpected token (2:3)
You may need an appropriate loader to handle this file type.
```

None needed.  These seem to be harmless warnings.


### Cannot find index.html when testing the UI in the browser.

You forgot to run ```grunt build```.


--------------------
## noflo-rdf-components Repository

### 'compare-rdf should print usage if given no command line arguments: Uncaught AssertionError: expected 1 to equal 2' when running ```mocha test```

Install python module rdflib:
```bash
pip install rdflib
```


### 'ImportError: No module named rdflib' when running ```mocha test```

Install python module rdflib:
```bash
pip install rdflib
```


### rdflib.plugin.PluginException: No plugin registered for (json-ld, <class 'rdflib.parser.Parser'>)



### ERROR:  'Could not compile stylesheet' when running ```mocha test```



### During "mocha test": Uncaught TypeError: callback is not a function at . . . noflo-rdf-components/node_modules/noflo-groups/node_modules/noflo-core/node_modules/noflo/lib/Component.js



--------------------
## noflo-server Repository

### During "grunt build": Warning: failed to fetch https://raw.githubusercontent.com/noflo/noflo/master/component.json, got 404 "Not Found"


