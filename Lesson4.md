# User Interface with XAML

## Fundamentals

A **markup language** is a computer language used to introduce various elements in a document. Elements are described using predefined tags, which have specific meanings in their respective domains. For example, Hypertext Markup Language (HTML) is used to create webpages displayed in web browsers.

**Extensible Application Markup Language (XAML)** is a declarative language created by Microsoft, based on XML. XAML simplifies the process of creating user interfaces (UIs) in applications.

### Benefits of XAML

- **Division of Labor**: XAML allows designers to focus on the markup without needing programming knowledge, while programmers can focus on writing code.
- **Tooling Friendly**: Design tools can help create XAML layouts by allowing drag-and-drop functionality.

### Instantiating UI Controls

The first step in using XAML to build a UI is instantiating the UI control types. In XAML, you use **Object Element Syntax** to declare the elements you want to instantiate. For example, to declare a label, you write:

```
<Label />
```

This XAML element is parsed by the XAML parser to instantiate the object in memory, equivalent to the following C# code:

```csharp
new Label();
```

### Using Namespaces

To instruct the XAML parser to use controls, you add a namespace. An **XML namespace** specifies where to find the information needed to instantiate the declared XAML elements. You define namespaces by adding the **xmlns** attribute to the root element in the XAML document, typically **ContentPage**:

```xml
<ContentPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="MyMauiApp.MainPage">
    ...
</ContentPage>
```

In this example:
- The first XML namespace declaration refers to classes in .NET MAUI.
- The second declaration defines a prefix **x** used for intrinsic elements and attributes in XAML.

### The x:Class Attribute

The **x:Class** attribute specifies the fully qualified .NET class name, such as the **MainPage** class in the MyMauiApp namespace. This indicates that the XAML file defines a new class named **MainPage** that derives from **ContentPage**.

The **x:Class** attribute can only appear in the root element of a XAML file. All other elements are instantiated from existing classes.

### Example of MainPage.xaml.cs

The corresponding C# file might look like this:

```csharp
namespace MyMauiApp;

public partial class MainPage : ContentPage
{
    public MainPage()
    {
        InitializeComponent();
    }
}
```

### Attributes in XAML

In XAML, attributes are used to set properties on the underlying types. For example:

```xml
<Label Text="Username" TextColor="Black"/>
```

This code creates a new **Label** object and sets its **Text** and **TextColor** properties. A **Type Converter** converts the string value for **TextColor** to the **Color** type.

## Event Handling

### Button Control

The **Button** control is a fundamental interactive element. It defines a **Clicked** event fired when the button is tapped. Here's how you instantiate a button in XAML:

```xml
<Button Text="Dial" Clicked="Button_Clicked"/>
```

The **Clicked** event is linked to an event handler named **Button_Clicked**, defined in the code-behind file:

```csharp
private void Button_Clicked(object sender, EventArgs e)
{
    PhoneDialer.Open(PhoneNumber.Text);
}
```

### RadioButton Control

A **RadioButton** allows users to select one option from a set. Each option is represented by a radio button, and only one can be selected at a time. To group radio buttons, set the **GroupName** property:

```xml
<RadioButton Content="Beginner" GroupName="levels" CheckedChanged="RadioButton_CheckedChanged"/>
<RadioButton Content="Intermediate" GroupName="levels" CheckedChanged="RadioButton_CheckedChanged"/>
<RadioButton Content="Advanced" GroupName="levels" CheckedChanged="RadioButton_CheckedChanged"/>
<Label x:Name="levelLabel"/>
```

The **CheckedChanged** event is handled by the following method:

```csharp
private void RadioButton_CheckedChanged(object sender, CheckedChangedEventArgs e)
{
    RadioButton button = sender as RadioButton;
    levelLabel.Text = $"You have chosen {button.Content}";
}
```

### SearchBar Control

The **SearchBar** control allows user input for initiating searches. It supports placeholder text and query input. Here’s an example of instantiating a SearchBar:

```xml
<SearchBar Placeholder="Search items..."/>
```

You can execute a search by attaching event handlers to:

- **SearchButtonPressed**: Called when the search button is clicked or the enter key is pressed.
- **TextChanged**: Called whenever the text in the query box changes.

Here's an example with **TextChanged**:

```xml
<SearchBar TextChanged="SearchBar_TextChanged"/>
<ListView x:Name="searchResults"/>
```

The **TextChanged** event links to the following handler:

```csharp
private void SearchBar_TextChanged(object sender, TextChangedEventArgs e)
{
    // Implement search logic here
}
```
```

### Tips for Presentation
1. **Use Visuals**: Consider using diagrams or screenshots of UI elements.
2. **Engage with Examples**: Live coding or demoing the XAML code can help solidify understanding.
3. **Q&A Sessions**: Encourage questions throughout to clarify concepts.

Feel free to modify any part of this as needed!
