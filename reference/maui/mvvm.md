# .NET MAUI MVVM

- Include the Community.MVVM NuGet package
    - CommunityToolkit.Mvvm
- Create a ViewModel class
    - Public
    - Partial
    - Derived from ObservableObject
- Associate the ViewModel to the page using xmlns:_{namespace}_ and x:DataType

```xml
<ContentPage ...
             xmlns:viewModel="clr-namespace:MyAppNamespace"
             x:DataType="viewModel:MainViewModel">
```

- Declare the ViewModel in the Dependency Injection container:

```csharp
// MauiProgram.cs
builder.Services.AddTransient<MainViewModel>();
```

- Inject the ViewModel in the page and initialize the context:

```csharp
public MainPage(MainViewModel viewModel)
{
    InitializeComponent();

    BindingContext = viewModel;
}
```


### Data binding

- Create a single object:
```csharp
[ObservableProperty]
private string? myLabel; 
// field name in lowercase
// A MyLabel property will be created automatically
```

```xml
<Label Text="{Binding MyLabel}" ...
```

- Create a collection:

```csharp
[ObservableProperty]
ObservableCollection<string> myOptions = ["Option 1", "Option 2"];
```

```xml
<Picker ItemsSource="{Binding MyOptions}" />
```

- Create a Command as an event handler:
```csharp
[RelayCommand]
private void ButtonClicked()
{
    MyLabel = "A button was clicked";
}
// A ButtonClickedCommand will be created automatically
```

```xml
<Button Text="Click here" Command="{Binding ButtonClickedCommand}"/>
```

- Create parameterized commands:

```csharp
[RelayCommand]
private void SpecificButtonClicked(Button source)
{
    MyLabel = $"The button with the {source.Text} text was clicked";
}
```

```xml
<Button 
    Text="Also click here" 
    Command="{Binding SpecificButtonClickedCommand}"
    CommandParameter="{Binding Source={RelativeSource Self}, Path=.}"
    />
```
- Show a collection of strings using a template:

```xml
<CollectionView ItemsSource="{Binding MyOptions}">
    <CollectionView.ItemTemplate>
        <DataTemplate x:DataType="{x:Type x:String}">
            <Grid Padding="0,10">
                <Border Padding="10" >
                    <HorizontalStackLayout Spacing="5">
                        <Label>Option:</Label>
                        <Label Text="{Binding}"/>
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

- Show a collection of objects:

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
