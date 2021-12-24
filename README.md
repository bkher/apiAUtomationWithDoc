# README #

This README would normally document whatever steps are necessary to get your application up and running.

### What is this repository for? ###

* Docitt API Automation


### Who Tools & Frameworks do I need on my machine? ###

* For Framework, you would need ****.NET Core 3.1**** on your machine
* For IDE, you would either require ****Visual Studio**** (Community Edition) or ****VS Code ****


### How do I get set up? ###

* If you are using Visual Studio, you can simply click on the .sln file to Import the project
* For using in Visual Studio Code, open the containinig folder in VS Code.
*	As soon as the project is loaded, open any file (preferably **.cs), and VS Code will ask
*	to add some settings. Click Yes and things would be good 


### How to execute the Tests ? ###

* 	If you are using an IDE, you can install a Test Explorer (if not installed), 
*		and from the Test Explorer -> you can select a single or mulitple tests
*		For e.g. Visual Studio has a default Test Explorer, but for VS Code, you
*		would need to install an Extension for that.
					** OR **
*	You can execute the tests via Command Line Utility, using the ****dotnet test**** command
*	A Basic syntax would look like below
** dotnet test ** *[list of loggers via --logger]* *[list of filters via --filter]* *[list of test parameters via -- TestRunParameters.Parameter(name=\"<name>\", value=\"<value>\")]*
*	
*	An eg. would be 
*	***dotnet test*** --filter FullyQualifiedName~SampleTest --logger:"console;verbosity=detailed" --logger:"nunit;LogFilePath=TestResults\NunitResult.xml" --logger:"html;LogFileName=dotnetResult.html" -- NUnit.ShowInternalProperties=true -- TestRunParameters.Parameter(name=\"app:username\", value=\"user\") -- TestRunParameters.Parameter(name=\"app.password\", value=\"P@ss!234\")
*
*	In the above command
*
*	We have used ***1 filter ***
*	1. This filter will execute all the tests that ****contains**** the name ***SampleTest***
*	2. We can keep an exact match if we use ***=*** instead of ***~***
*
*	We have used ***3 loggers ***
*	1. For Loggin to Console
*	2. For generating NUnitResult.xml
*	3. For generating dotnet HTML Result
*
*	We have used ***2 TestRunParameters***
*	1. Variable Name would be ****app:username**** and its value would be ****user****
*	2. Variable Name would be ****app:password**** and its value would be ****P@ss!234****


###  appsettings.json  ###
* Location : Root -> ApiAutomation -> appsettings.json
* You can add properties in json format and it will be read during the execution.
* Values from the file can be used in the code via ***ConfigManager*** class
*	e.g. : ****ConfigManager.GetBundle.GetValue<T>("propKey")****				{if the propKey is a root level key}
*	e.g. : ****ConfigManager.GetBundle.GetValue<T>("key1:key2:key3")****		{if key1 is a root level key, key2 is the child of key1 and key3 is the child of key2}


###  How to provide Excel files for TestData  ###
*	in the AppSettings.json, there will be a section called ***testdata***
*	you can mention the directory path where single or multiple **.xlsx files will be located
*	if the directory path is an absolute path, then set the value of ***isPathAbsolute*** as ***true***
*			if kept false, the path will be considered relative from the ****bin -> debug -> netcoreapp3.1**** location
*	List of excel file names will be given as a JSON Array for the key ***fileNames***

###  Do's and Don't for TestData  ###
*	DO 		: You can add New Columns, New Sheets to the existing Workbooks, without having to change anything in the appsettings.json
*	DO 		: You can keep the value of a Cell "blank" (without any contents), and its value will be considered as Empty Text
*	DON'T	: Don't keep the name of 2 sheets same even if they are in different workbooks
*	DON'T	: Don't keep the value of 2 Headers same for a particular sheet. If the Sheets are different, you can repeat the header, but not within a single sheet
*	DON'T 	: Don't leave the 1st Column blank for any row
*	DON'T	: Don't use any HyperLink in any sheet. If excel adds that automatically, make sure you remove the hyperlink
*	DO		: You can use a random utility and the data for a cell will be read by converting into the random value runtime.
			*	#random-email		: Creates a random Valid Email
			*	#random-username	: Creates a random Valid Username
			*	#random-password	: Creates a random Valid Password
			*	#random-firstName	: Creates a random Valid First Name
			*	#random-lastName	: Creates a random Valid Last Name
			*	#random-mobile		: Creates a random Valid 10 digit Mobile phone
			*	#random-birthDate	: Creates a random BirthDate from (1-Jan-1950 to 1-Jan-2002)
			*	#random-string		: Creates a random string of length 10 chars
			*	#random-string-m	: Creates a random string of length m chars
			*	#random-string-m-n	: Creates a random string of length between m to n chars
			*	#random-number		: Creates a random numeric string of length 10 chars
			*	#random-number-m	: Creates a random number string of length m chars
			*	#random-number-m-n	: Creates a random number string of length between m to n chars
			*	#random-regex-[A-a]**: Creates a random values based on the regex pattern provided after the hyphen



### Who do I talk to? ###

* Gunjan
* Bhagatsinh