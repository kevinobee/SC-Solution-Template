## SC-Solution-Template
A solution template and project structure for working with Sitecore and TDS (optional)


## Installation
The instructions provided explain how to install the development environment locally.

In the example  that follows the solution template will be installed to _Template_ directory under _D:\Websites\Development_


#### Install Sitecore
Install the version of Sitecore that you are working  with to _D:\Websites\Development\Template_ using Sitecore installer or Rocks.


#### To pull down the GIT repository from BitBucket

    > cd D:\Developer\Sitecore\Template
	> git clone https://github.com/kevinobee/SC-Solution-Template.git tmp && mv tmp/.git . && rm -rf tmp
	> git checkout -- .
	> git reset hard


Create a branch off _master_ for your local development and customise the following file:

*    __Sitecore.Settings.props__

    Located in _build_ directory. You'll need to set the _SolutionRootDir_ path and _WebsiteUrl_ MSBuild properties. 


        <?xml version="1.0" encoding="utf-8"?>
        <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
            <PropertyGroup>
                <WebsiteUrl>http://yoursite</WebsiteUrl>
                <SolutionRootDir>D:\Websites\Development\Template</SolutionRootDir>
                <SitecorePath>$(SolutionRootDir)\Website</SitecorePath>
                <SitecoreLibPath>$(SolutionRootDir)\lib\Sitecore</SitecoreLibPath>
            </PropertyGroup>
        </Project>

    The _Sitecore.Settings.props_ file is imported into each _.csproj_ file to specify the web root and the directory location of referenced Sitecore assembly files. For exammple:


        <ItemGroup>
            <Reference Include="Sitecore.Analytics">
                <HintPath>$(SitecoreLibPath)\Sitecore.Analytics.dll</HintPath>
                <Private>False</Private>
            </Reference>
            <Reference Include="Sitecore.Client">
                <HintPath>$(SitecoreLibPath)\Sitecore.Client.dll</HintPath>
                <Private>False</Private>
            </Reference>
            <Reference Include="Sitecore.Kernel">
                <HintPath>$(SitecoreLibPath)\Sitecore.Kernel.dll</HintPath>
                <Private>False</Private>
            </Reference>
            ....
        </ItemGroup>



When pushing changes back into _master_ avoid committing this file. To ensure that the file is ignored run the following GIT command:


    > git update-index --assume-unchanged build/Sitecore.Settings.props
