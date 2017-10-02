# Troubleshooting

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
