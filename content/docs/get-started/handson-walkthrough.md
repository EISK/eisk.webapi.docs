---
uid: eisk-webapi-handson-walkthrough
---
# Hands on Walkthrough

In this step by step article, you'll be creating a new web api from the scratch. With the utilities and bootstrap code as provided by EISK, you'll realize how easy to create a new web api with Visual Studio and ASP.NET Core.

This article assumes you've basic understanding with Object Oriented Programming.

## Step 1: Check System Requirements

To start developing a new web api, you'll need the following or upper version of Visual Studio. If you've not installed it yet, you can get a free copy of Visual Studio Community Edition from it's download site (link provided below). 

* Visual Studio 2017 ([Free](https://visualstudio.microsoft.com/vs/community/) Community Edition or higher)

## Step 2: Download EISK Web Api

You can download EISK with variety of [options and choices](xref:eisk-webapi-download-options). 

If you're familiar with [git](https://git-scm.com/) (and installed in your local machine) you can perform a git clone with the following git bash command to get latest EISK Web Api code sample.

`git clone https://github.com/EISK/eisk.webapi.git`

Alternatively you can run the following dotnet cli (which comes by default with Visual Studio) command to install and create a new EISK Web Api project:

* Command to install EISK template in your machine: `dotnet new -i eisk.webapi`
* Command to create a new project: `dotnet new eiskwebapi -n Eisk`

Check [here](xref:eisk-webapi-download-options-dotnet-new) for additional details and installtion options with dotnet CLI.

## Step 3: Build & Run EISK Web Api Locally

After the solution is available, simply click the created solution to open in Visual Studio. 

In the solution explorer, you'll be able to see a web api project, few projects providing utility classes and tests. Right click the web api project (default name Eisk.Web) and select "Set as StartUp Project".

Hit F5, to let visual studio build the solution and open the web api project in browser.






 



