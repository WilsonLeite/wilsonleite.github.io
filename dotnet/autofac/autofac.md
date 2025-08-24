# Autofac

### Reference

* Autofac [website](https://autofac.org/)
* [NuGet](https://www.nuget.org/packages?q=Owner%3A%22Autofac%22+Autofac*) packages

## Console

Create the Global Scope in the Program class:

```csharp
internal class Program
{
    public static void Main(string[] args)
    {
        using (var globalScope = CreateDependencyInjectionGlobalScope())
        {
            var service = globalScope.Resolve<MyService>();
            service.Execute();
        }
    }

    public static ILifetimeScope CreateDependencyInjectionGlobalScope()
    {
        var containerBuilder = new ContainerBuilder();

        ConfigureDependencyInjectionContainer(containerBuilder);

        var container = containerBuilder.Build();

        return container.BeginLifetimeScope();
    }

    private static void ConfigureDependencyInjectionContainer(ContainerBuilder builder)
    {
        // Register all classes in the current assembly
        var currentAssembly = Assembly.GetExecutingAssembly();

        builder.RegisterAssemblyTypes(currentAssembly);

        builder.RegisterAssemblyTypes(currentAssembly)
            .AsImplementedInterfaces();
    }
}
```

## WinUI 3

Install NuGet package ( Only Autofac needed)

On App.xaml.cs

```csharp
private ILifetimeScope GlobalScope;

public App()
{
    this.InitializeComponent();

    var containerBuilder = new ContainerBuilder();

    var currentAssembly = Assembly.GetExecutingAssembly();

    containerBuilder.RegisterAssemblyTypes(currentAssembly);

    containerBuilder.RegisterAssemblyTypes(currentAssembly)
        .AsImplementedInterfaces();

    var container = containerBuilder.Build();

    GlobalScope = container.BeginLifetimeScope();
}

protected override void OnLaunched(Microsoft.UI.Xaml.LaunchActivatedEventArgs args)
{
    m_window = GlobalScope.Resolve<MainWindow>();

    m_window.Activate();
}
```

## .NET MAUI

Create the configuration in the _MauiProgram_ class

```csharp
public static MauiApp CreateMauiApp()
{
    var builder = MauiApp.CreateBuilder();
    builder
        .UseMauiApp<App>()
        .ConfigureFonts(fonts =>
        {
            fonts.AddFont("OpenSans-Regular.ttf", "OpenSansRegular");
            fonts.AddFont("OpenSans-Semibold.ttf", "OpenSansSemibold");
        })
        .ConfigureContainer(new AutofacServiceProviderFactory(), ConfigureDependencyInjectionContainer);
...
}

private static void ConfigureDependencyInjectionContainer(ContainerBuilder builder)
{
    ...
}
```

## Registering

```csharp

// Register all classes in the current assembly
var currentAssembly = Assembly.GetExecutingAssembly();

builder.RegisterAssemblyTypes(currentAssembly);

builder.RegisterAssemblyTypes(currentAssembly)
    .AsImplementedInterfaces();

// Register a class that can be directly depended on
builder.RegisterType<MyClass>().AsSelf();

// Register a class that implements an interface
builder.RegisterType<MyClass>().As<IMyClass>();

// Register a class as a singleton
builder.RegisterType<MyService>().AsSelf().SingleInstance();

// Register an interface as a singleton
// Note this is a different instance than the one registered above
builder.RegisterType<MyService>().As<IMyService>().SingleInstance();

// Register an existing instance as a singleton
var service = new MyService();
builder.RegisterInstance(service);

// Register a factory for MyService that creates an instance explicitly
// (non-singleton)
builder.Register(componentContext => new MyService { myDependency = new MyDependency() });

// Ask the context for an instance of MyDependency
builder.Register(componentContext => new MyService { myDependency = componentContext.Resolve<MyDependency>() });

// The same, but requesting the dependency as a parameter
builder.Register( (MyDependency d) => new MyService { myDependency = d });

// Letting Autofac resolve the dependency
builder.Register(componentContext => componentContext.Resolve<MyService>()).As<IMyService>();

// Register a parameterized factory
// Used like:
// var AnotherServiceFactory = GlobalScope.Resolve<Func<int, IAnotherService>>();
// or
// public Func<int, IAnotherService> AnotherServiceFactory { get; init; }
// var anotherService = AnotherServiceFactory(42);
builder.Register<int, IAnotherService>((componentContext, i) => componentContext.Resolve<AnotherService>());

// Register a Generic service. They are not registered by RegisterAssemblyTypes:
builder.RegisterGeneric(typeof(GenericService<>))
    .AsSelf()
    .AsImplementedInterfaces();
```

Note that classes not registered can still be instantiated using the default Dependency Injection service used by .NET MAUI leading to initialization errors.


## Usage

### Injecting a dependency in the constructor:

```csharp
public MainWindow(MainWindowViewModel viewModel)
```

### Injecting a dependency in a property:

If the dependency is not used in the constructor, it is cleaner to inject it as a property by using the _required_ and _init_ keywords:

```csharp
public MyClass
{
    public required ILog Logger {private get; init;}
}

```

### Injecting a dependency factory in the constructor:

```csharp
public MainWindow(Func<MainWindowViewModel> viewModelFactory)
{
    var viewModel = viewModelFactory();
}
```
### Injecting a dependency factory in the constructor that requires one of the expected parameters:

```csharp
public class A(ILog logger, string objectName) {...}

// Class B constructor:
public B(Func<string, A> AFactory)
{
    var a = AFactory("ObjectName");
}
```
