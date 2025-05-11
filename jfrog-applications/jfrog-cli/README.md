# JFrog CLI

* JFrog CLI
  * == client / 
    * allows
      * automating access
      * simplifying your automation scripts
      * making MORE readable & easier to maintain 
  * uses | JFrog 
    * Artifactory,
    * Xray,
    * Distribution
    * Pipelines (-- through their -- respective REST APIs)
  * support
    * [upload & download capabilities advances](#advanced-upload-and-download-capabilities)
    * [popular package managers & build tools](#support-for-popular-package-managers-and-build-tools)
    * [scan of source code & binaries](#scan-of-source-code-artifacts-containers--and-binaries)
    * [build-info](#support-build-info)

## Advanced upload and download capabilities

* JFrog CLI     
  * allows you to
    * 👀upload & download artifacts CONCURRENTLY 👀
      * -- via -- configurable number of threads
      * -> your automated builds run faster
    * | big artifacts, define chunks
      * Reason: 🧠split files -- for -- parallel download🧠
    * download files easily -- via -- wildcard patterns
    * upload files easily -- via -- 
      * wildcard patterns
      * regular expressions,
      * ANT patterns
  * optimizes both upload & download operations
    * Reason: 🧠skip artifacts / ALREADY EXIST | their target location🧠 
      * | BEFORE uploading or downloading an artifact, JFrog CLI queries -- , with the artifact's checksum, -- Artifactory
      * if it ALREADY EXISTS | Artifactory's storage -> CLI skips sending the file
  * long upload & download operations can be paused | middle
    * -- via -- checksum optimization

## Support for popular package managers and build tools

* == JFrog CLI integrates -- with -- package managers 
  * _Example:_ npm, Maven, NuGet, Docker, ...
  * -> easily manage & publish packages

## Scan of source code (artifacts, containers, ...) and binaries

* JFrog CLI 
  * provides
    * scanning capabilities
      * -> ensure the security & compliance of your source
  * \+ JFrog Xray
    * allows you to
      * scan & analyze your projects & packages (artifacts, containers,...)
  * uses
    * identify and mitigate potential risks,
    * ensure the integrity of your software supply chain

## Support Build-Info

* Build-Info
  * == metadata Software Bill of Materials (SBOM)  
    * == 👀components' information used | build 👀
      * version history, 
      * artifacts, 
      * project modules, 
      * dependencies,
      * environment variables
      * ...  
    * == ".json"
  * allows
    * gain traceability & analysis capabilities
  * uses
    * JFrog CLI can create it
    * store it | Artifactory

#### System Requirements

* ANY OS / FULLY supports [Go programming language](https://golang.org/)
