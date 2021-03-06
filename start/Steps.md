1. create "start" folder
1. push to origin
1. in start folder create sln file
1. `dotnet new sln`
1. in start folder create azure-function in order to contain the azure function proj
1. with function ext create func in above folder
1. use this crontab expression "\*/5 \* \* \* \*"
1. run the azure func with F5
1. git push
1. add func proj to sln file
1. cd into folder with sln file
1. `dotnet sln .\start.sln add .\azure-function\azure-function.csproj`
1. in "start" add "azure-function-manager"
1. cd in the newly created folder
1. `dotnet new classlib`
1. change in csproj from net5.0 to netstandard2.1
1. `dotnet sln .\start.sln add .\azure-function-manager\azure-function-manager.csproj`
1. cd in start and mkdir azure-function-entities
1. `dotnet new classlib`
1. change in csproj from net5.0 to netstandard2.1
1. `dotnet sln .\start.sln add .\azure-function-entities\azure-function-entities.csproj`
1. git push
1. create class Output.cs in entities (folder "models") with props:
   - Message
   - ApiKey
1. create service GreetingsService.cs in managers (folder "services") with methods:
   - SayHello()
1. pull up its interface
1. move interface to its own file
1. make the func not static & create its constructor
1. add refs among projs
   1. in azure function add ref to manager proj
   1. in manager add ref to entities proj
1. inject IGreetingsService in TimerTriggerFunc.cs
1. install Microsoft.Azure.Functions.Extensions in azure func proj
1. create Startup.cs in func proj
1. inherit from FunctionsStartup
1. decorate namespace with `[assembly: FunctionsStartup(typeof(Startup))]`
1. add file to .gitignore at start folder level
1. override Configure()
   1. register service IGreetingsService
1. create output class in TimerTriggerFunc and log the instance
1. override ConfigureAppConfiguration()
1. add Microsoft.Extensions.Configuration.UserSecrets in azure-function
1. add secret to azure-function proj user secrets file
1. in startup.cs > ConfigureAppConfiguration()
   1. get context from builder
   1. initialize Configuration prop (bring in the necessary ns)
1. use IConfiguration in TimerTriggerFunc by injecting it in ctor
1. use %TimerCron% in local.settings.json
