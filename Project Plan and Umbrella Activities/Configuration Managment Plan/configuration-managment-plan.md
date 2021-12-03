# Tune Tip Configuration Managment Plan

## GitHub

We are currently utilizing GitHub for source control and our CI/CD plan (continuous integration/continuous development). Each version of our software is kept in a GitHub repository with a detailed README of instructions and specifications.

### Cloning & Creating New Repository for New Version

When development has begun on a new future release version the team will clone our latest version into a newly created GitHub repository that will hold the new release version of the solution.

### GitHub Projects

We will assign tasks/stories of new functionality and features we want to add by utilizing the gnatt chart/GitHub projects to keep track and assign TODO items.

### Branching

Each developer can work in parallel to complete stories by creating a new working branch off the main branch. This can be done by cloning the following command:

`git checkout -b branchname`

### Pull Requests

Once the developer has finished their task item and would like to check in their changes to include in the main branch the developer can submit a pull request. Each pull request triggers a GitHub Action workflow which will first build and run the application and any specified tests created for the project. The team can then be notified if any pull requests have introduced any issues/bugs that need to be fixed before merging into the main development branch.

### GitHub Actions

The repositories are currently utilizing GitHub Actions which is a continuous integration and continuous delivery platform that allows you to automate your build, test, and deployment pipeline. You can see examples of these here for the music-service and music -ui repositories:

[music-service]( https://github.com/Group6CapstoneGroup/music-service/actions/workflows/dotnet-package.yml)

[music-ui]( https://github.com/Group6CapstoneGroup/music-ui/actions)
