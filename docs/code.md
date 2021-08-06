# Writing Code

## Getting Started

1. Update your global gitignore to allow DLL, BAK, and PDB files.
2. You should create a website folder where your project will be. This can be anywhere on your system.  My environment is in 
C:\Websites\Development\
3. Clone the repository into that folder
4. Create a new folder in the root:  _Website_  This would make the path C:\Websites\Development\Website\ in my environment.
5. Install DNN 07.02.00 into the Website folder just like you would for any other DNN site
6. Update IIS and your local HOSTS file to point to http://dnndev.me
7. Open the solution in Visual Studio
8. Write code.

---

## Dependencies

### DNN / DotNetNuke

All new development is currently being built against DNN 09.04.00.

[Download DNN Platform version 09.04.00](https://github.com/dnnsoftware/Dnn.Platform/releases/tag/v9.4.0)

Be sure that you get the file permissions properly assigned to the folders when you install DNN.  

### Visual Studio Extensions  

The following Visual Studio Extensions are currently installed and being used in my environment, but are not 
necessary to work on the project.  There are more, but these are the only ones that are relevant to this project.  

* GhostDoc  
* Guidinserter2  
* Microsoft ASP.NET and Web Tools  
* NuGet Package Manager  
* ReSharper 9 (not free, except to [active open source developers](https://www.jetbrains.com/eforms/openSourceRequest.action?licenseRequest=RSOSL))  
* UIMap Toolbox  
* Web Essentials  

---

## Pull Requests  

First, thank you! Every single moment you participate benefits a lot of people in the world.  

Here are a few ground rules:  

* Do not submit pull requests for more than one fix. Keep them small and focused.  
* Please code review yourself. There are a lot of pull requests with typos and mistakes. Don't worry, we all do it. But a code review of yourself will help. :)  
* Please review the diff in GitHub that I will see before I merge your pull requests. If it's hard for you to tell what the differences are, it's going to be hard for me too.  

## How to Build

You should probably not build the at the solution level, since this will also build the website, but it won't 
hurt anything if you do.  It will just take longer.

In general, you should be building from the specific module project you're currently working on.

### What happens when I build?

Building in __DEBUG__ mode will compile the project/solution as you'd expect, but an MS Build script will also 
move the module files into the appropriate Website\DesktopModules\ folder as well.  

Building in __RELEASE__ mode will _not_ move the project files, but it will package up the respective module 
in an Install and Source package that can be used to install on another DNN site for testing or deployment. The 
resulting packages will be found in the following directory.

\Website\Install\Module\

This is VERY important to know.  Each project has a .Build file that properly maps it's files that need to 
be moved into the website folder.  

You can reverse engineer this to see how it works by referencing each individual Module.Build file.  In order 
to add this to your own module project, copy the build file, make the appropriate changes, and then add the 
following lines of code to your project file.

```xml
  <ItemGroup> 
    <Content Include="Module.Build"> 
      <SubType>Designer</SubType> 
    </Content> 
  </ItemGroup> 
  <Import Project="Module.Build" /> 
```

## Debugging

Debugging should be done using the "Attach to Process" method.