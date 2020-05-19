# Windows Package Manager - Red Team repo
This repository contains manifest files for the **Windows Package Manager**. It is a fork of the official Community repo that hosts offensive security tools that may be used by security professionals. **To ensure usability and sharability of these tools, all packages should be hosted on servers that do NOT scan the contents with AV.** It is regularly updated from the Community. You are highly encouraged to submit manifests for your favorite application.

The **Windows Package Manager** is an open source client.  You will find the source code [here](https://github.com/microsoft/winget-cli).

# Submitting a Package
To submit a package to the repository, you should follow these steps:
1) Follow the **Contributing** guidelines below
2) Author a Manifest
3) Test your manifest
4) Submit your PR
5) Respond to any feedback

## Authoring a Manifest

The minimal manifest syntax is below.

Current limitations are:
* One manifest per PR
* One installer per PR
* The storage location for the installer must not subject to AV/anti-malware scanning

Be sure the manifest filename matches the `Version` and the manifest is located in the folder path matching `manifests\<publisher>\<package>\<version>.yaml`

```yaml
Id: string # publisher.package format
Publisher: string # the name of the publisher
Name: string # the name of the application
Version: string # version numbering format
License: string # the open source license or copyright
InstallerType: string # enumeration of supported installer types (exe, msi, msix)
Installers:
  - Arch: string # enumeration of supported architectures
    URL: string # path to download installation file
    Sha256: string # SHA256 calculated from installer
# ManifestVersion: 0.1.0
```

### Using the YAMLCreate.ps1
To help author manifest files, Microsoft has provided a YAMLCreate.ps1 powershell script located in the Tools folder.  
The script will prompt you for the URL to the installer, then will prompt you to fill in metadata.

I recommend running the script in the location where you want to produce the manifest file.  For example: `manifests\<publisher>\<package>\`.  After successful completion, it will produce the YAML file.


## Test your manifest
Now that you have authored your manifest, you should make sure it works as expected.
1) Verify the syntax.  You can do that by typing the following command: `winget validate <manifest>`
2) Test the install.  You can do that by installing the manifest: `winget install -m <manifest.`
For more details, see [packages](https://docs.microsoft.com/windows/package-manager/package).

## Submit your PR
With the manifest verified, you will need to submit a PR.  Your manifest should be located in the folder path matching `manifests\<publisher>\<package>\<version>.yaml`

### Validation Process
The PR request will go through a validation process.  During the process, the PR request will get labels to help drive the validation.
In the event of a failure, the BOT will suggest where the problem is with the submission and assign the PR back to you.  

### Respond to PR feedback
If the PR has been assigned to you, a timer is triggered.  You will have 7 days to resolve the issue, or the PR will be closed automatically by the BOT.  

For a list of the BOT labels, see [packages](https://docs.microsoft.com/windows/package-manager/package).

# Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

For the avoidance of doubt, you may not make any Submissions linking to third party materials if such 
Submission is prohibited by the applicable third party and/or otherwise violates such third party's rights.

