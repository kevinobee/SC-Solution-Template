## SC-Solution-Template
A solution template and project structure for working with Sitecore and TDS (optional)


## Installation
The instructions provided explain how to install the development environment locally.

In the example  that follows the solution template will be installed to _Template_ directory under _D:\Developer\Sitecore_


#### To pull down the GIT repository from BitBucket

    > cd D:\Developer\Sitecore

    > git clone https://github.com/kevinobee/SC-Solution-Template.git Template


#### Install Sitecore
Install the version of Sitecore that you are working  with to _D:\Developer\Sitecore\Template_ using Sitecore installer or Rocks.


Create a branch off _master_ for your local development and customise the following file:

*    __sitecore.path.xml__

    Located in _build_ directory

    Imported into each _.csproj_ file. This contains MSBuild Properties used to specify the web root and the directory location of referenced Sitecore assembly files. For exammple:


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



When pushing changes back into _master_ avoid committing this file.


