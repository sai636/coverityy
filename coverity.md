# Coverity Shared Library Usage




## Steps Involved

1) Coverity download

2) Coverity configure

3) Coverity create project and stream

4) Coverity build

5) Coverity analyze

6) Coverity commit


---

### Coverity Download



- This step downloads coverity in jenkins workspace and returns coverity bin path as String(cov_path).

>Example:
String cov_path = cov_download(ARTIFACTORY_SERVER_ID,ARTIFACTORY_CREDENTIAL_ID)


- Add cov_path as PATH variable in your env to execute coverity commands

--- 

### Coverity Configure
- This step configures the necessary compilers  for the build step.


>Example:
 cov_configure(compiler,coverityXmlConfigPath,otherOptions)

---
### Coverity Create Project and Stream
- This step creates Project instinct in Coverity connect.If project and streams are already existing it will continue to the next step.

>Example:
cov_create_project_stream(covConnectUrl,projectName,streamName,COVERITY_USERNAME,COVERITY_PASSWORD,otherOptions)

---
### Coverity Build

- This builds the source code and emits the call graph to intermediate directory.

>Example:
cov_build(idir, coverityXmlConfigPath, buildCmd, target)

---
### Coverity Analyze
- This step provides static code violations.


>Example:
cov_analyze(idir,codingStandardConfigFiles,otherOptions)

---
### Coverity Commit

- This step pushes the results to Coverity.


>Example:
cov_commit(idir,covConnectUrl,streamName,COVERITY_USERNAME,COVERITY_PASSWORD,List otherOptions = [])


---

##Parameters required to be passed

- **ARTIFACTORY_SERVER_ID**: This parameter likely represents the name of the Artifactory server from which the download will be performed.

- **ARTIFACTORY_CREDENTIAL_ID**: This parameter likely represents the credentials associated with the Artifactory server for authentication and authorization.

- **compiler**: This parameter likely represents the  build tool to be configured for integration with Coverity.
- **coverityXmlConfigPath**: This parameter likely represents the path to the Coverity configuration file in XML format

- **covConnectUrl**: This parameter likely represents the URL of the Coverity Connect server.
- **projectName**: This parameter likely represents the name of the project to be created.
- **streamName**: This parameter likely represents the name of the stream within the project.
- **COVERITY_USERNAME**- A string representing a username for authentication
- **COVERITY_PASSWORD**- A string represnting a password for authentication
- **idir**: A string representation of Directory
- **buildCmd**: This parameter likely represents the command used to perform the build operation.
- **target**: This parameter likely represents the target or output artifact of the build process.
- **codingStandardConfigFiles**: This parameter likely represents the configuration files the coding standards to be applied during the analysis.
- **streamName**-  A string representing the name of the Stream

####Optional Parameter
-  **OtherOptions**: These are other options likely an optional list of additional configuration options specific to your project.
