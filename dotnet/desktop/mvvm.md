# .NET Desktop MVVM

## File conventions

* Put UI-related files in the same directory
* The directory name will define the namespace
* File names:
    * Window: _Subject_ Window.xaml
    * Page: _Subject_ Page.xaml
    * ViewModels: _Subject_ Model.cs


## Project setup

- Include the Community.MVVM NuGet package
    - CommunityToolkit.Mvvm

## ViewModel class

### WinUI 3

- Create a ViewModel class
    - Public
    - Derived from ObservableObject

### MAUI

- Create a ViewModel class
    - Public
    - Partial
    - Derived from ObservableObject

## Associating a ViewModel to a Window or Page

### WinUI 3

* Declare the ViemModel as a Property of the page
* Initialize it in the constructor

```csharp
private MainWindowModel viewModel { get; set; }

public MainWindow(MainWindowModel viewModel)
{
    this.InitializeComponent();
    this.viewModel = viewModel;
}
```

### MAUI

- Associate the ViewModel Type to the page using xmlns:_{namespace}_ and x:DataType

```xml
<ContentPage ...
             xmlns:viewModel="clr-namespace:MyAppNamespace"
             x:DataType="viewModel:MainViewModel">
```

- Inject the ViewModel in the page and initialize the context:

```csharp
public MainPage(MainViewModel viewModel)
{
    InitializeComponent();

    BindingContext = viewModel;
}
```

## Data binding to a single object

### WinUI 3

Create an Observable Object explicitly:

```csharp
private string? myLabel;

public string? MyLabel
{
    get => myLabel;
    set => SetProperty(ref myLabel, value);
}
```
```xml
<Label Text="{x:Bind viewModel.MyLabel, Mode=OneWay}"/>
```

### MAUI

```csharp
[ObservableProperty]
private string? myLabel; 
// field name in lowercase
// A MyLabel property will be created automatically
```

```xml
<Label Text="{Binding MyLabel}"/>
```
## Using a collection

### WinUI 3

```csharp
public ObservableCollection<string> MyOptions { get;set; }
```

```xml
<ComboBox ItemsSource="{x:Bind viewModel.MyOptions, Mode=OneWay}"/>
```

### MAUI

```csharp
[ObservableProperty]
ObservableCollection<string> myOptions = ["Option 1", "Option 2"];
```

```xml
<Picker ItemsSource="{Binding MyOptions}"`BackgroundColor="Beige" />
```

## Using a Command as an event handler

### WinUI 3

```csharp
private ICommand? buttonClickedCommand;
public ICommand ButtonClickedCommand => buttonClickedCommand ??= new RelayCommand(ButtonClicked);

private void ButtonClicked()
{
}

private ICommand? button2ClickedCommand;
public ICommand Button2ClickedCommand => button2ClickedCommand ??= 
    new RelayCommand<Button?>(Button2Clicked);

private void Button2Clicked(Button? button)
{
}

private ICommand? button3ClickedCommand;
public ICommand Button3ClickedCommand => button3ClickedCommand ??= 
    new RelayCommand<Button?>(Button2Clicked, CanExecute);

private bool CanExecute(Button? btn)
{
    return true;
}

```

```xml
<Button Content="Click here" 
        Command="{x:Bind viewModel.ButtonClickedCommand}">
<Button Content="Or here" 
        Command="{x:Bind viewModel.Button2ClickedCommand}
        CommandParameter="{Binding RelativeSource={RelativeSource Self}}"">
```

### MAUI

```csharp
[RelayCommand]
private void ButtonClicked()
{
}
// A ButtonClickedCommand will be created automatically

[RelayCommand]
private void SpecificButtonClicked(Button source)
{
    MyLabel = $"The button with the {source.Text} text was clicked";
}

[ObservableProperty]
[NotifyCanExecuteChangedFor(nameof(Button3ClickedCommand))]
private bool canClickButton = true;

[RelayCommand(CanExecute = nameof(CanClickButton))]
private void Button3Clicked()
{
    CanClickButton = false;
}
```

```xml
<Button Text="Click here" Command="{Binding ButtonClickedCommand}"/>

<Button 
    Text="Or click here" 
    Command="{Binding SpecificButtonClickedCommand}"
    CommandParameter="{Binding Source={RelativeSource Self}, Path=.}"
    />
```

## Show a collection of objects

### WinUI 3

```csharp
// Elsewhere
public partial class ItemModel : ObservableObject
{
    public required string Name { get; set; }

    public required int Id { get; set; }

    private ICommand? itemButtonClickedCommand;
    public ICommand ItemButtonClickedCommand => itemButtonClickedCommand ??= new RelayCommand<ItemModel?>(ItemButtonClicked);

    private void ItemButtonClicked(ItemModel? item)
    {
    }
}

// MainViewModel
public ObservableCollection<ItemModel> MyItems { get; set; } = [
    new ItemModel { Name = "Xuxa", Id = 123 }
];
```

```xml
<ListView ItemsSource="{x:Bind viewModel.MyItems}">
    <ListView.ItemTemplate>
        <DataTemplate x:DataType="local:ItemModel">
            <Grid Padding="0,10">
                <Border Padding="10" >
                    <StackPanel Spacing="5" Orientation="Horizontal">
                        <TextBlock VerticalAlignment="Center">Name:</TextBlock>
                        <TextBlock  VerticalAlignment="Center" Text="{x:Bind Name}"/>
                        <Button 
                            Content="Click me" 
                            Command="{x:Bind ItemButtonClickedCommand}"
                            CommandParameter="{x:Bind}"
                        />
                    </StackPanel>
                </Border>
            </Grid>
        </DataTemplate>
    </ListView.ItemTemplate>
</ListView>
```

### MAUI

```csharp
// Elsewhere
public partial class ItemModel: ObservableObject
{
    [ObservableProperty]
    private string name;

    [ObservableProperty]
    private int id;
}

// MainViewModel
[ObservableProperty]
ObservableCollection<ItemModel> myItems = [ 
    new ItemModel { Name = "Xuxa", Id = 123 } 
    ];


[RelayCommand]
private void ItemClicked(ItemModel item)
{
    MyLabel = $"The item {item.Id} was clicked";
}
```

```xml
<CollectionView ItemsSource="{Binding MyItems}">
    <CollectionView.ItemTemplate>
        <DataTemplate x:DataType="{x:Type viewModel:ItemModel}">
            <Grid Padding="0,10">
                <Border Padding="10" >
                    <HorizontalStackLayout Spacing="5">
                        <Label>Name:</Label>
                        <Label Text="{Binding Name}"/>
                        <Button 
                            Text="Click me" 
                            Command="{Binding ItemClickedCommand, Source={RelativeSource AncestorType={x:Type viewModel:MainViewModel}}}"
                            CommandParameter="{Binding}"
                            />
                    </HorizontalStackLayout>
                </Border>
            </Grid>
        </DataTemplate>
    </CollectionView.ItemTemplate>
</CollectionView>
```

# Using partial properties in WinUI3

Set the language version = preview in the .csproj file:

```xml
    ...
    <Nullable>enable</Nullable>
    <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Create properties as partial:

```csharp
[ObservableProperty]
public partial string ButtonText { get; set; } = "Click this button";
```