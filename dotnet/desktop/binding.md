# WinUI 3 Binding

Binding is typically used for associating properties in a user interface control to a property in a context class.

See also [Windows data binding in depth](https://learn.microsoft.com/en-us/windows/apps/develop/data-binding/data-binding-in-depth), including the [cheat sheet](https://learn.microsoft.com/en-us/windows/apps/develop/data-binding/data-binding-in-depth#xbind-and-binding-feature-comparison).

## x:Bind

The target value must be a [DependencyProperty](https://learn.microsoft.com/en-us/windows/uwp/xaml-platform/dependency-properties-overview).

### To the control

```csharp
public sealed partial class MainWindow : Window
{
    public MainWindowModel ViewModel { get; set; }
```

```xml
<Button 
    x:Name="myButton" 
    Command="{x:Bind ViewModel.ButtonClickedCommand}" 
    CommandParameter="{Binding RelativeSource={RelativeSource Self}}" 
    Content="{x:Bind ViewModel.ButtonText, Mode=OneWay}"/>
```

### To the Data Template

```csharp
public partial class ItemModel : ObservableObject
{
    private ICommand? itemButtonClickedCommand;
    public ICommand ItemButtonClickedCommand => itemButtonClickedCommand ??= new RelayCommand<ItemModel?>(ItemButtonClicked);

    private void ItemButtonClicked(ItemModel? item)
    {
    }
}
```

Note that _{x:Bind}_ means the ItemModel in this context.

```xml
<ListView ItemsSource="{x:Bind ViewModel.MyItems}">
    <ListView.ItemTemplate>
        <DataTemplate x:DataType="local:ItemModel">
            <Button 
                Content="Click me" 
                Command="{x:Bind ItemButtonClickedCommand}"
                CommandParameter="{x:Bind}"/>
```

### Referencing the element itself

Note that by declaring _x:Name="Rect1"_ we are creating a _Rect1_ property in the current context (Window or Data Template). 

```xml
<Rectangle 
    x:Name="Rect1" 
    Width="200" 
    Height="{x:Bind Rect1.Width}" 
    ... />
```

## Binding

### Reach the View Model from inside a template

```xml
<Window
    x:Name="ThisWindow"
    ... >

<Button 
    Content="Click me" 
    Command="{Binding ElementName=ThisWindow, Path=ViewModel.ItemClickedCommand}"
    CommandParameter="{x:Bind}" />
```

### Referencing the element itself

```xml
<Button 
    CommandParameter="{Binding RelativeSource={RelativeSource Self}}"
    ... />

<Rectangle 
    Width="200" 
    Height="{Binding Width, RelativeSource={RelativeSource Self}}" 
    ... />
```
