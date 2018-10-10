node("MSBuild")
{
	def solutionName = "JenkinsTestProjectCoreConsoleApp"
	stage('Checkout') 
	{
		checkout scm
	}

	stage('Install Nuget Commandline')
	{
		powershell 'choco install nuget.commandline'
	}

	stage('Restore Nuget packages')
	{
		powershell 'nuget restore ${solutionName}.sln'
	}

	stage('Build')
	{
		// C:/Program Files (x86)/Microsoft Visual Studio/2017/Community/MSBuild/15.0/Bin/MSBuild.exe
		bat "\"${tool 'MSBuild'}\" ${solutionName}.sln /p:Configuration=Debug /t:Restore;Clean;Build"
	}
	
	/*stage('Test')
	{
		// C:/Program Files (x86)/Microsoft Visual Studio/2017/Community/Common7/IDE/MSTest.exe
		dir('UnitTestProjectDotNetCore/bin/Debug/netcoreapp2.1')
		{
		    bat "\"${tool 'MSTest'}\" /testcontainer:UnitTestProjectDotNetCore.dll"
		}
	}*/
	
}
