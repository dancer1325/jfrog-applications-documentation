# Authentication | Artifactory
## Overview

* ⚠️MANDATORY⚠️

## Authenticating -- via -- Username and Password / API Key

* `jf c add`
  * allows
    * authenticate 1! yourself -- via -- your JFrog login credentials

| Command option | Description                                                           |
|----------------|-----------------------------------------------------------------------|
| `--url`        | JFrog Artifactory API endpoint URL <br/> USUALLY "*/artifactory"      |
| `--user`       | JFrog username                                                        |
| `--password`   | JFrog password or API key                                             |

* 👀AUTOMATICALLY generates an access token 👀
  * Reason: 🧠enhanced security 🧠
  * 1 hour valid
  * 👀BEFORE it expires, JFrog CLI AUTOMATICALLY refresh the token 👀
    * if you want -> you can disable it

## Authenticating with an Access Token

* `jf c add`

| Command option   | Description                                                           |
|------------------|-----------------------------------------------------------------------|
| `--url`          | JFrog Artifactory API endpoint URL <br/> USUALLY "*/artifactory"      |
| `--access-token` | JFrog access token                                                    |

## Authenticating with RSA Keys

* TODO:
***

**Note**

> Currently, authentication with RSA keys is not supported when working with external package managers and build tools (Maven, Gradle, Npm, Docker, Go and NuGet) or with the cUrl integration.

***

From version 4.4, Artifactory supports SSH authentication using RSA public and private keys. To authenticate yourself to Artifactory using RSA keys, execute the following instructions:

* Enable SSH authentication as described in [Configuring SSH](https://jfrog.com/help/r/jfrog-platform-administration-Documentation/Managing-Ssh-Keys).
*   Configure your Artifactory URL to have the following format: `ssh://[host]:[port]` There are two ways to do this:

    * For each command, use the `--url` command option.
    * Specify the Artifactory URL in the correct format using the **jf c add** command.

    ***

    **Warning**\
    \
    **Don't include your Artifactory context URL**

    > Make sure that the \[host] component of the URL only includes the hostname or the IP, but not your Artifactory context URL.

    ***
* Configure the path to your SSH key file. There are two ways to do this:
  * For each command, use the `--ssh-key-path` command option.
  * Specify the path using the **jf c add** command.

## Authenticating using Client Certificates (mTLS)

From Artifactory release 7.38.4, you can authenticate users using a client certificate ([mTLS](https://en.wikipedia.org/wiki/Mutual\_authentication#mTLS)). To do so will require a reverse proxy and some setup on the front reverse proxy (Nginx). Read about how to set this up [here](https://jfrog.com/help/r/jfrog-artifactory-documentation/Http-Settings).

To authenticate with the proxy using a client certificate, either configure your certificate once using the **jf c add** command or use the --`client-cert-path` and`--client-cert-ket-path` command options with each command.

***

**Note**

> Authentication using client certificates (mTLS) is not supported by commands which integrate with package managers.

***

Not Using a Public CA (Certificate Authority)?

This section is relevant for you if you're not using a public CA (Certificate Authority) to issue the SSL certificate used to connect to your Artifactory domain. You may not be using a public CA either because you're using self-signed certificates or you're running your own PKI services in-house (often by using a Microsoft CA).

In this case, you'll need to make those certificates available for JFrog CLI, by placing them inside the **security/certs** directory, which is under JFrog CLI's home directory. By default, the home directory is **\~/.jfrog**, but it can be also set using the **JFROG\_CLI\_HOME\_DIR** environment variable.

**Note**

1. The supported certificate format is PEM. Make sure to have ONE file with the ending .pem. OR provide as many as you want and run the c_rehash command on the folder as follows  :`c_rehash ~/.jfrog/security/certs/`.
2. Some commands support the **--insecure-tls** option, which skips the TLS certificates verification.
3. Before version 1.37.0, JFrog CLI expected the certificates to be located directly under the **security** directory. JFrog CLI will automatically move the certificates to the new directory when installing version 1.37.0 or above. Downgrading back to an older version requires replacing the configuration directory manually. You'll find a backup if the old configuration under **.jfrog/backup**
