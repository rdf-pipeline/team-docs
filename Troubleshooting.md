# Troubleshooting

## Problems when installing noflo-ui

### Symptom: Error when running grunt during noflo-ui installation: Module not found: Error: Cannot resolve module 'coffee-script/register'
**Possible solution:** Before "grunt build"ing noflo-ui, you need to install coffee-script and run ```npm update```.

### Symptom: Unable to parse README.md
```
WARNING in ./~/bindings/README.md
Module parse failed: . . . /noflo-ui/node_modules/bindings/README.md Unexpected token (2:3)
You may need an appropriate loader to handle this file type.
```

**Possible solution:** None needed.  These seem to be harmless warnings.


## Problems when testing NoFlo UI

### Symptom: Cannot find index.html when testing the UI in the browser.
**Possible solution:** You forgot to run ```grunt build```.
