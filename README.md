# Vlocity Build
--------

Vlocity Build is a command line tool to export and deploy Vlocity DataPacks in a source control friendly format through a YAML Manifest describing your project. Its primary goal is to enable Continuous Integration for Vlocity Metadata through source control. It is written as a Node.js Command Line Tool.  

# Steps to take BackUp of Vlocity Components
--------

## Steps to setup Vlocity Build and Git

### Create a folder in local directory 
```bash
mkdir <projectname>
```

### Create a new Git Repository and follow the steps
```bash
echo "# anthem-sgfoa-test" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/dbandi/anthem-sgfoa-test.git
git push -u origin master
```

### Install Vlocity build
```bash
npm init
npm install --global vlocity
```

### Setup Properties file
Create Properties File
```bash
sf.username = <Your SF Username>
sf.password = <Your SF Password> + <Your SF Security Token>
sf.loginUrl = https://login.salesforce.com
vlocity.dataPacksJobFolder = ./dataPacksJobs
```

### Create a Job file
Create a `dataPacksJobs` folder and create a job yaml file.


### Export Vlocity components 
```bash
vlocity packExport -propertyfile build_<Unique_Org_Name>.properties -job <ReleaseDate>_<ProjectName>_<Unique_Org_Name>_Release_BackUp_Release_BackUp.yaml
```

### Create a git branch
```bash
git checkout -b Release_Branch_<ReleaseDate>
```

### Push the exports to git.
```bash
git add .
git commit -m "<Your_Release_Label">
git push --set-upstream origin <ReleaseDate>_<ProjectName>_<Unique_Org_Name>_Release_BackUp_Release_BackUp
```
