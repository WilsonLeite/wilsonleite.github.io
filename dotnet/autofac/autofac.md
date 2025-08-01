# Autofac

### Reference

* Autofac [website](https://autofac.org/)
* [NuGet](https://www.nuget.org/packages?q=Owner%3A%22Autofac%22+Autofac*) packages

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

## Usage

### Injecting a dependency in the constructor:

```csharp
public MainWindow(MainWindowViewModel viewModel)
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

If the dependency is not used in the constructor, it is cleaner to inject it as a property by using the _required_ and _init_ keywords:

```csharp
public MyClass
{
    public required ILog Logger {private get; init;}
}

```
