# Hyperlink

## Overview

The HyperLink control must be inside a TextBlock.

See the official [documentation](https://learn.microsoft.com/en-ca/windows/windows-app-sdk/api/winrt/microsoft.ui.xaml.documents.hyperlink).

## How to detect a middle click?

We can detect a middle click in the parent TextBlock. However, there is no direct way to tell to what span/run/etc. inside the Textblock that point maps to. To be sure, we can have only the HyperLink inside the TextBlock.

```xml
<TextBlock PointerPressed="TextBlock_PointerPressed"><Hyperlink Click="Hyperlink_Click">Go!</Hyperlink></TextBlock>
```

```csharp
private void Hyperlink_Click(Hyperlink sender, HyperlinkClickEventArgs args)
{
    //...
}

private void TextBlock_PointerPressed(object sender, PointerRoutedEventArgs e)
{
    var properties = e.GetCurrentPoint(sender as UIElement).Properties;

    if (properties.IsMiddleButtonPressed)
    { 
        // Prevents the default action if any other handler is present.
        e.Handled = true; 

        // Do your thing...
    }
}
```