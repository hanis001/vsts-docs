---
title: Connect to your Git repos using credential managers | VSTS & TFS
description: Authenticate to VSTS and TFS Git repos using credential managers
ms.assetid: 7779af87-460c-4078-bc2b-ceb4b758c24e
ms.prod: devops
ms.technology: devops-code-git 
ms.manager: douge
ms.author: sdanie
author: steved0x
ms.topic: conceptual
ms.date: 03/14/2018
monikerRange: '>= tfs-2015'
---


#  Use Git Credential Managers to Authenticate to VSTS
#### VSTS | TFS 2018 | TFS 2017 | TFS 2015 | VS 2017 | VS 2015

Git Credential Managers simplify authentication with your VSTS/TFS Git repos. Credential Managers let you use the same credentials that you use for the VSTS/TFS web portal and support multi-factor authentication through Microsoft Account (MSA) or Azure Active Directory (AAD). In addition to supporting multi-factor authentication with VSTS, the credential managers also provide support two-factor authentication with [GitHub repositories](https://help.github.com/articles/about-two-factor-authentication/).

VSTS provides IDE support for MSA and AAD authentication through [Team Explorer in Visual Studio](../user-guide/connect-team-projects.md), [IntelliJ and Android Studio with the VSTS Plugin for IntelliJ](/vsts/java/download-intellij-plug-in), and [Eclipse (with the Team Explorer Everywhere plug-in)](https://github.com/Microsoft/team-explorer-everywhere). If your environment doesn't have an integration available, configure your IDE  with a [Personal Access Token](../accounts/use-personal-access-tokens-to-authenticate.md) or [SSH](use-ssh-keys-to-authenticate.md) to connect with your to your repos.

## Install the Git Credential Manager
 
### Windows 
Download and run the latest [Git for Windows installer](https://git-scm.com/download/win), which includes the Git Credential Manager for Windows. Make sure to leave the Git Credential Manager installation option enabled when prompted.

   ![Select Enable Git Credential Manager during Git for Windows install](_img/install-with-gcm.png)   

### macOS and Linux

> Review the [system and software requirements](https://github.com/Microsoft/Git-Credential-Manager-for-Mac-and-Linux/blob/master/Install.md#system-requirements) before installing the credential manager.
 
On macOS and Linux, there are [several install options](https://github.com/Microsoft/Git-Credential-Manager-for-Mac-and-Linux/blob/master/Install.md) that use native package managers to install the credential manager. After installing the package for your platform, run the following command to configure Git to use the credential manager :

<pre style="color:white;background-color:black;font-family:Consolas,Courier,monospace;padding:10px">
&gt; git-credential-manager install</pre>

## Using the Git Credential Manager

When you connect to a VSTS Git repository from your Git client for the first time, the credential manager  prompts for your Microsoft Account or Azure Active Directory credentials. If your account has multi-factor authentication enabled, you are prompted to go through that experience as well.

![Git Credential Manager prompting during Git pull](_img/gcm_login_prompt.gif)
   
Once authenticated, the credential manager creates and caches a [personal access token](../accounts/use-personal-access-tokens-to-authenticate.md) for future connections to the repo. Git commands that connect to this account won't prompt for user credentials until the token expires or is revoked through VSTS/TFS.

### Getting help 

You can open up and report issues with the Git Credential Manager for Windows on the [project GitHub](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/issues). 
Frequently Asked Questions for the Git Credential Manager for Windows are available in [the online readme](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/blob/master/Docs/Faq.md). 

Manual installation steps for the [Windows Git Credential Manager](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/blob/master/README.md#manual-installation) and the [macOS and Linux Git Credential Manager](https://github.com/Microsoft/Git-Credential-Manager-for-Mac-and-Linux/blob/master/Install.md#installing-on-mac-or-linux-without-a-package-manager) are available. Use these steps to install the credential manager if the recommended steps above are not suitable for your environment.

### Learn more

In addition to providing full source code, we've also documented how the credential manager integrates with Git. Refer to the MSDN blog posts on the [macOS and Linux Git Credential Manager](http://blogs.msdn.com/b/visualstudioalm/archive/2015/11/18/visual-studio-team-services-git-credential-manager-for-mac-and-linux.aspx) and the 
[Windows Credential Manager](http://blogs.msdn.com/b/visualstudioalm/archive/2015/12/08/announcing-the-git-credential-manager-for-windows-1-0.aspx). There is also
[an article on the project GitHub](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/wiki/How-the-Git-Credential-Managers-works) with information on the low-level internals of the Git Credential Manager for Windows.    
