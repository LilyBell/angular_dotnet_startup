# Setup

Before diving into coding an applicaiton built with Angular 4 and .NET there are some prequisites which must be satisfied. This process is based upon instructions originally authored by [@ciel](https://www.github.com/ciel) and has been modified for use with Facebook's yarn package manager.

## Step 1: Install [rimraf](https://github.com/isaacs/rimraf)

rimraf is a package that emulates the Linux command rm -rf to avoid errors in Windows associated with deletion of non empty directories.

```
yarn global add rimraf
```

## Step 2: Install [Angular 4](https://angular.io)

```
yarn global add @angular/cli
```

## Step 3: Install [Typescript](https://www.typescriptlang.org/)

```
yarn global add typescript
```

## Step 4: Clone [git repo](https://www.github.com/LilyBell/angular_dotnet_startup).
Please include the trailing '.' as this instructs git to clone into the current directory rather than create a new directory.

```
git clone --depth=1 https://github.com/LilyBell/angular_dotnet_startup.git .
```

## Step 5: Delete the git repository and install npm modules

```
rimraf .git
npm install
```

## Step 6: Create root directories
These directories are for source code, tooling and IDE specifics

```
mkdir src
mkdir .vscode
mkdir .nuget
mkdir .blueprints
```

## Step 7: Create new .NET solution
Note that the solution is being named ```.``` and being given an output of ```.``` This is done to keep the names generic and fit with the pattern of other agnostic files like ```.gitignore``` and ```.jsbeautify.``` This is not a requirement.

```
dotnet new sln -n . -o .
```

## Step 8: Correct solution filename
Because of the way the ```dotnet-cli``` creates the solution file, it gets made with a filename of ```..sln```, so we use the ```mv``` command to fix it.

```
mv ..sln .sln
```

## Step 9: Create a new .NET Core class library

```
dotnet new classlib -n common -o ./src/common
```

## Step 10: Create a new .NET Core ASP.NET project
This is the actual application that will run the .NET(C#) backend and the Angular 4(JavaScript) frontend.

```
dotnet new mvc -n client -o ./src/client
```

## Step 11: Add each of the projects to the previously created solution
This assures that ```dotnet-cli``` knows how to treat the attached projects.

```
dotnet sln . add ./src/common/common.csproj
dotnet sln . add ./src/client/client.csproj
```

# Optional Steps


