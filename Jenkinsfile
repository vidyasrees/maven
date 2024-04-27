@Library('newlibrary')_
node('built-in')
{
    stage('ContDownload_Loans')
    {
        cicd.newGit("https://github.com/vidyasrees/maven.git")
    }
    stage('ContBuild_Loans')
    {
        cicd.newMaven()
    }

}
