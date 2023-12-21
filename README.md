# Tag Releaser v1 

## Brief info
This actions creates Github tag based on the version in config.

Action is [matreshka](https://github.com/godverv/Matreshka) config based.
That means that to work properly, this action need a yaml file of the following format:

```yaml
app_info:
  version: "v1"
```

Where version - is the field you need to update 
whenever you'd like to release a new tag

## Configuration

### Workflow file

```yaml
name: master-actions
run-name: RELEASE
on:
  push:
    branches:
      - master

jobs:
  tag-release:
    runs-on: ubuntu-latest
    steps:
      - name: Release
        uses: RedSockActions/release_tag@v1
        with:
          token: ${{ github.token }}
          config_path: ./config/config.yaml
```
#### token
This action requires github.token in order to create a tag

#### config_path
You can create a custom path to config file. 

"./config/config.yaml" - is a default value

#### organization configuration
In order to **allow** action create tags, you have to check 
option at action settings -> https://github.com/organizations/{YOUR_ORGANISATION_NAME_GOES_HERE}/settings/actions)

It should be like this:
![workflow_permissions.png](static%2Fworkflow_permissions.png)


###### Made by RedSock with love for coding 