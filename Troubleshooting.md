# Troubleshooting

## Symptom: Error when running grunt during noflo-ui installation: Module not found: Error: Cannot resolve module 'coffee-script/register'
*Possible solution:* Globally installed node_modules may be affecting the installation.  Try [deleting node_modules from your home directory](https://stackoverflow.com/questions/13011290/cannot-find-module-coffee-script) and then re-installing:

```bash
pushd ~
sudo rm -rf node_modules
popd
npm install
grunt build
```

