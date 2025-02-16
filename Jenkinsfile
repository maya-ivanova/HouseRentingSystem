node {
    stage('Checkout Code') {
        git branch: 'master', url: 'https://github.com/maya-ivanova/HouseRentingSystem.git'
    }
    stage('Restore NuGet packages'){
        bat 'dotnet restore HouseRentingSystem.sln'
    }
    stage('Build solution'){
        bat 'dotnet build HouseRentingSystem.sln --configuration Release'
    }
    stage('Run Tests'){
        bat 'dotnet test .\\HouseRentingSystem.Tests\\HouseRentingSystem.Tests.csproj --configuration Release --logger trx'
    }
    stage('Publish Artifacts'){
        bat 'dotnet publish .\\HouseRentingSystem.Web\\HouseRentingSystem.Web.csproj --configuration Release --output ./publish'
    }
    stage('Archive Build'){
        archiveArtifacts artifacts: 'publish/**', fingerprint: true
    }
}