# Authentication

* JFrog CLI + XRay
  * 👀-> JFrog CLI has SEVERAL means of authentication👀

* if you want to access XRay -- via -- JFrog CLI -> use authentication

#### Authenticating -- via -- Username & Password

* `jf c add` + use your Xray login credentials 

| Command Option | Description |
|---------------|-------------|
| `--url` | JFrog Xray API endpoint URL <br/> usually "*/xray" |
| `--user` | JFrog username |
| `--password` | JFrog password |


#### Authenticating -- via -- Access Token

* `jf c add` + use a Xray Access Token

| Command Option | Description |
|---------------|-------------|
| `--url` | JFrog Xray API endpoint URL <br/> usually "*/xray" |
| `--access-token` | JFrog access token |
