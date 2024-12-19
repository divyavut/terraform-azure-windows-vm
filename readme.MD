# Dot net Build process
1. Nuget restore -> read the .csproj file and downloads all the necessary dependencies for your project.
2. msbuild ---> complie code, runt eh test, generates output files (like .exe, .dll).

# classic pipeline for dotnet tasks
  1. Nuget task  ---> nuget restore
  2. visual studio build, msbuild task ---> msbuild   
  -  msbuild  argumnents

          /P:DeployOnBuild=true /p:WebPublishMethod=Package /p:PackageAsSingleFile=true 
          /p:SkipInvalidConfigurations=true
          /p:PackageLocation="$(build.stagingDirectory)" /p:IncludeServerNameInBuildInfo=true /p:GenerateBuildInfoConfigFile=true
          /p:BuildSymbolStorePath="$(SymbolPath)" /p:ReferencePath="C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Extensions\Microsoft\Pex"

## Important points
- viusal stuido version list 
- viusal studio drive link: https://drive.google.com/drive/folders/1cxAROvlqrHVfOLE0DOrlVnvEMP7BO8vB


# Step to perform CI in seld hosted agent
- create windows vm
- install chrome, install visual studio 2017 community through drive link, check the list of thinks in visual studio installer like .net desktop development, asp.net and web development from workloads, dependency invalidation from individual componenet.
- install dotnet framework 4.8 sdk
- install agent and configure it on windows vm.
- steup ci pipeline with tasks like restore nuget, ms build, copy files, publish artifacts.