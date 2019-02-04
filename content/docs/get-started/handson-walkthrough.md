---
uid: eisk-webapi-handson-walkthrough
---
# Hands on Walk through

In this step by step article, you'll be creating a new web api from the scratch. With the utilities and bootstrap code as provided by EISK, you'll realize how easy to create a new web api with Visual Studio and ASP.NET Core.

This article assumes you've basic understanding with Object Oriented Programming.

## Step 1: Check System Requirements

To start developing a new web api, you'll need the following or upper version of Visual Studio. If you've not installed it yet, you can get a free copy of Visual Studio Community Edition from it's download site (link provided below). 

* Visual Studio 2017 ([Free](https://visualstudio.microsoft.com/vs/community/) Community Edition or higher)

## Step 2.a: Download & Install EISK Web Api

You can download EISK with different options and choices. Consider the following simple walk through to install EISK in your local machine with dotnet cli, which comes built-in with latest visual studio. 

[dotnet cli](https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-new) provides excellent command line options to create, build, test, deploy .net core application easily.

To install EISK Web Api with dotnet cli, open command prompt, and type the following command:

`dotnet new -i eisk.webapi`

Installing template in your local machine will allow you creating as many web api projects with EISK as you want. 

## Step 2.b: Create a New Web Api Project

From the command prompt, navigate to a directory, where you want to create new web api and type the following command:

`dotnet new eiskwebapi -n Eisk`

The 'n' paramter accepts the root namespace of the project (in the given example this is Eisk). You can consider your company name or choice of your root namespace.

After the solution is created simply click the created solution to open in Visual Studio. 

In the solution explorer, you'll be able to see a web api project, few projects providing utility classes and tests. Right click the web api project (default name Eisk.Web) and select "Set as StartUp Project".

Hit F5, to let visual studio build the solution and open the web api project in browser.





 



