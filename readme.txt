ClickOnce does not have prerequisite for asp.net runtime 9.0.7.

https://stackoverflow.com/questions/74142462/clickonce-prerequisite-for-asp-net-core-runtime-6-0-10-x64


- Add the prerequisite for VS
	- download the Asp.Net_runtime_9.0.7_x64 directory
		- Asp.Net_runtime_9.0.7_x64\product.xml
		- Asp.Net_runtime_9.0.7_x64\NetCoreCheck.exe
		- Asp.Net_runtime_9.0.7_x64\en\package.xml
	- copy the files into c:\Program Files (x86)\Microsoft SDKs\ClickOnce Bootstrapper\Packages
		- you need admin rights
	- now the new dependency should appear in VS
		- you do not have to restart VS, just press in "project / publish" and the "more actions / edit"


- If there is a new version 
	- create a new directory structure 
	- modify the version numbers in readme.txt
	- modify the version numbers in package.xml 
	- find the new NetCoreCheck.exe
		- c:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Microsoft\VisualStudio\BootstrapperPackages\net9desktopruntime_x86
	- modify the version numbers in product.xml
	- update HomeSite in product.xml
		- New link for HomeSite: "https://dotnet.microsoft.com/en-us/download" / "All .Net 9.0 downloads" / "ASP.NET Core Runtime 9.0.7, Windows x64 installer" / "Direct link, Copy"
	- add the prerequisite for VS
		- if the prerequisite is not shown in VS then check for errors
		- e.g., you may deleted the quotation mark at HomeSite
	- update the github repo
	
	
- NETCoreCheck.exe problem
	- when the new prerequisite is created for asp.net it was a question which NETCoreCheck.exe is to be used, x86 or x64
		- c:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Microsoft\VisualStudio\BootstrapperPackages\net9coreruntime_x86
	- the answer is x86, though I have 64 bit windows
	- usage of NETCoreCheck.exe 
		- cmd in the proper folder
		- NETCoreCheck.exe Microsoft.AspNetCore.App 9.0.7
		- echo %ERRORLEVEL%
			- it displayes the error code of the last commnad
			- you should see 0 if the framework is installed
	- list all runtimes
		- dotnet --list-runtimes
