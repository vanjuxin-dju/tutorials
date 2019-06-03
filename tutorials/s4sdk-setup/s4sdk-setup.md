---
title: Set Up Your Local Infrastructure to Develop with SAP Cloud SDK
description: Set up your system to create an SAP Cloud Platform application with the SAP Cloud SDK.
auto_validation: true
tags: [ tutorial>intermediate, products>sap-s-4hana-cloud-sdk, products>sap-s-4hana, products>sap-cloud-platform, topic>cloud, topic>java ]
primary_tag: products>sap-s-4hana-cloud-sdk
time: 10
---

## Details
### You will learn  
In this tutorial, you will go through the steps required to install the [SDK](https://developers.sap.com/topics/s4hana-cloud-sdk.html) and corresponding tools to use it for the development of your SAP Cloud Platform application.

For a complete overview visit the [SAP Cloud SDK Overview](https://blogs.sap.com/2017/05/10/first-steps-with-sap-s4hana-cloud-sdk/).


---

[ACCORDION-BEGIN [Step 1: ](Prepare the Infrastructure)]

### On Windows (Windows 7+ / Windows Server 2003+)

**Install Chocolatey (a package manager for Windows)**

```
@powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
```

**Install Java Development Kit; if not yet available, install a specific JDK (e.g. JDK 8)**

```
choco install jdk8
```

**Install Maven**

```
choco install maven
```

### On Mac

**Install `Homebrew` (Mac package manager to help with the remaining installation)**

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

**2. Install Java Development Kit, if it is not yet available**

```
brew update
brew tap AdoptOpenJDK/openjdk
brew cask install java
```

_Tip: Install a specific JDK if you like (e.g. JDK 8)_

```
brew cask install caskroom/versions/java8
```

**Install Maven**

```
brew update
brew install maven
```
To validate that everything is installed correctly, you can use command `javac -version` and `mvn -version`, the output should look similar to the following (you may have the newer version of the software, thought):

```bash
javac -version
```

```bash
mvn -version
```

Check that the environment variable `JAVA_HOME` points to the path of your JDK installation, e.g. `C:\Program Files\path\to\java\jdk1.8.0_72`.

[DONE]

[ACCORDION-END]

[ACCORDION-BEGIN [Step 2: ](Install IDE)]

To develop your first 'Hello World' application with SAP Cloud SDK, you can just use your command line and a simple text editor. However, for larger development projects you can work with the IDE of your choice.

We recommend using [`Intellij IDEA`](https://www.jetbrains.com/idea/#chooseYourEdition) or [`Eclipse`](https://www.eclipse.org/users/). Follow the installation instructions of corresponding tools to prepare your IDE. In case you use Eclipse, make sure to install the [`Maven plugin for Eclipse`](http://www.eclipse.org/m2e/).

[DONE]

[ACCORDION-END]

[ACCORDION-BEGIN [Step 3: ](Troubleshooting with Corporate Proxies)]

Some of the steps in the upcoming tutorial blogs will fail if you sit behind a corporate proxy. If you cannot escape the proxy, you need to tell Maven where your proxy is located.
To do this, you need to cd to your `~/.m2 directory` (e.g. on Windows: `C:/Users/<username>/.m2"`") and create a file called `settings.xml`. Then you paste the following content:

```xml
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
                      http://maven.apache.org/xsd/settings-1.0.0.xsd">
  <proxies>
    <proxy>
      <id>my_corp_proxy</id>
      <active>true</active>
      <protocol>http</protocol>
      <host>proxy</host>
      <port>8080</port>
      <username></username>
      <password></password>
      <nonProxyHosts>localhost,127.0.0.1</nonProxyHosts>
    </proxy>
  </proxies>
</settings>
```

After finishing these steps, you are ready to start the development of your SAP Cloud Platform applications with SAP Cloud SDK. If you are interested to learn more, stay tuned for the upcoming development topics that we will cover in the following tutorials: available project templates in the SDK, setting up the communication with SAP S/4HANA, deployment on Cloud Foundry, etc.

[DONE]

[ACCORDION-END]

[ACCORDION-BEGIN [Appendix: ](Test yourself)]

[VALIDATE_1]

[ACCORDION-END]
---

### Additional Information
Choose your next step depending on whether you would like to deploy to Cloud Foundry or Neo:
  - **Tutorial for Cloud Foundry:** [Create a sample application on Cloud Foundry using SAP S/4HANA Cloud SDK](https://developers.sap.com/tutorials/s4sdk-cloud-foundry-sample-application.html)
  - **Tutorial for Neo:** [Create a sample application on SCP Neo using SAP S/4HANA Cloud SDK](https://developers.sap.com/tutorials/s4sdk-scp-neo-sample-application.html)
