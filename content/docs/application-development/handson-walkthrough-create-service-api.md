---
uid: eisk-webapi-handson-walkthrough-create-service-api
---

# Create New Service Api

In this step by step article, you'll be creating a new web api from the scratch through which you can perform CRUD operation on a database entity. 

With the utilities and bootstrap code as provided by EISK, you'll realize how easy to create a new web api with Visual Studio and ASP.NET Core.

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

## Step 3: Build & Run Locally

After the solution is available, simply click the created solution to open in Visual Studio. 

In the solution explorer, you'll be able to see a web api project, few projects providing utility classes and tests. Right click the web api project (default name Eisk.Web) and select "Set as StartUp Project".

Hit F5, to let visual studio build the solution and open the web api project output in browser.

The index page of the project is basically [Swagger UI](https://docs.microsoft.com/en-us/aspnet/core/tutorials/web-api-help-pages-using-swagger), showing a web console to explore underlying web api. 

EISK by default provides a simple use case to perform CRUD operation in an employee table in [Domain Driven Development](https://en.wikipedia.org/wiki/Domain-driven_design) fashion.

The Swagger UI enables accessing the "Employees" api different http verbs (get, post, put, delete etc) and perform data operations in database encapculated with Entity Framework.

Invoke the 'Get' call as available in the first options, by considering the following steps:

`Get (/api/Empliyees) -> Try it out -> Execute`

A json response will be shown under "Server response" section with all employees as available in database.

You can perform other http verb operations by following the similar steps mentioned above.

## Step 4: Creating a New Service Api

As you get familiar with the default use case employee, you may want to write your own api with a new use case, so see how the EISK has been designed to write web api easily with best coding and architectural guidelines.

### Use Case Employee Time Sheet

As an application user, I want to store employee time sheet for different projects everyday. A single time sheet entry may associate zero or one project.

### Creating New Domain

To support the above use case, let's create a "EmployeeTimeSheet.cs" domain under the following solution location: 

`Project: Eisk.Domains`

`New file path: Entities\EmployeeTimeSheet.cs`

	using System;
	using System.ComponentModel.DataAnnotations;
	using System.ComponentModel.DataAnnotations.Schema;

	namespace Eisk.Domains.Employee
	{
		public class EmployeeTimeSheet
		{
			[Key]
			[DatabaseGenerated(DatabaseGeneratedOption.Identity)]
			public int Id { get; set; }
			public int EmployeeId { get; set; }
			public DateTime TimeSheetDate { get; set; }
			public float LoggedHours { get; set; }
			public string ProjectCode { get; set; }

		}
	}

### Add Property to Database Context

Add a property as provided below in the following solution location: 

`Project: Eisk.DataServices.EFCore`

`File location: DataContext\AppDbContext.cs`

	public virtual DbSet<EmployeeTimeSheet> EmployeeTimeSheets { get; set; }

### Add Service Api
	
Add a new class as provided below on the following solution location: 

`Project: Eisk.WebApi`

`New file location: Controllers\EmployeeTimeSheetsController.cs`

	using Microsoft.AspNetCore.Mvc;

	namespace Eisk.WebApi.Controllers
	{
		using Core.DomainService;
		using Domains.Entities;
		using Eisk.Core.WebApi;

		[Route("api/[controller]")]
		public class EmployeeTimeSheetsController
			:WebApiControllerBase<EmployeeTimeSheet,int>
		{
			public EmployeeTimeSheetsController(
				DomainService<EmployeeTimeSheet, int> 
					employeeTimeSheetDomainService)
						:base(employeeTimeSheetDomainService)
			{
				
			}
		}
	}


### Build & Run Locally 

Similar to Step 3, simply press "Control + F5" to open WebApi project in browser. 

In the Swagger UI you'll notice a new section is available to test the new api we just created for EmployeeTimeSheets.

Play with the UI to add create, read, update, delete employee time-sheet.


