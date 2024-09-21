# User Interface with XAML

## Fundamentals

A **markup language** is a computer language that is used to introduce various elements in a document.
Elements are described using predefined tags. The tags have specific meaning in the context of the domain
where the document is used. For example, you can use Hypertext Markup Language (HTML) to create a
webpage that you can display in a web browser.

Extensible Application Markup Language (XAML) is a declarative language created by Microsoft that is based
on XML. XAML was designed to simplify the process of creating the UI in applications.

UI on XAML will allow the separation of the app’s UI and behavior to make it easier to manage both. Other
benefits include:

- **Division of labor** : Since XAML is a markup language, it does not require programming knowledge.
    Designers can focus on XAML and programmers can focus on writing the code.
- **Tooling friendly** : It is possible to use a design tool to create the XAML layout for you. You can drag
    and drop controls onto a design surface using a graphical experience.

The first step in using XAML to build a UI is instantiating the UI control types. In XAML, the types can be created
using **Object Element Syntax** , a standard, well-formed XML syntax to declare the element to instantiate. For
example, if you want to declare a label, your XAML element will look like the following: **<Label />**

The above XAML element will be parsed by the XAML parser to instantiate the object in memory. This is the
same with the following C# code: **new Label ();**

The next thing to do is instruct the XAML parser to use controls. We add this instruction using a namespace.
An **XML namespace** is used to specify the location of the information needed to instantiate the XAML elements
that you declare. Namespaces are defined by adding the **xmlns** attribute to the root element in the XAML
document. Typically, the root element of a XAML document is **ContentPage**.

```
<ContentPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
x:Class="MyMauiApp.MainPage">
...
</ContentPage>
```
The two XML namespace ( **xmlns** ) declarations refer to URIs on microsoft.com. However, these URIs have no
content, and they function as version identifiers. The first XML namespace declaration means that tags defined
within the XAML file with no prefix refer to classes in .NET MAUI, for example **ContentPage**. The second
namespace declaration defines a prefix of **x**. This is used for several elements and attributes that are intrinsic
to XAML itself and supported by other XAML implementations.

At the end of the first tag, the **x** prefix is used for an attribute named **Class**. Because the use of this **x** prefix
is virtually universal for the XAML namespace, XAML attributes such as **Class** are almost always referred to
as **x:Class**. The **x:Class** attribute specifies a fully qualified .NET class name: the **MainPage** class in the

MyMauiApp namespace. This means that this XAML file defines a new class named **MainPage** in the
MyMauiApp namespace that derives from ContentPage (the tag in which the x:Class attribute appears).

The **x:Class** attribute can only appear in the root element of a XAML file to define a derived C# class. This is
the only new class defined in the XAML file. Everything else that appears in a XAML file is instead simply
instantiated from existing classes and initialized.

The MainPage.xaml.cs file looks similar to this:
**namespace MyMauiApp;**

```
public partial class MainPage : ContentPage
{
public MainPage()
{
InitializeComponent();
}
}
```
In XML, attributes are used to describe or provide information about an element. In XAML, attributes are used
to set properties on the underlying type. For example:

```
<Label Text="Username" TextColor="Black"/>
```
The above XAML code creates a new **Labe** l object and sets the **Text** and **TextColor** properties. Since
**TextColor** uses the **Color** type and **string** is the only valid thing that can be used for an XML attribute
value, it is needed to convert the **string** value to the **Color** type. A **Type Converter** is used to convert an
XML attribute value to its correct type.

## Event Handling

The **Button** is the most fundamental interactive control. The **Button** control defines a Clicked event that is
fired once the **Button** is tapped. The following code instantiates a **Button** in XAML.
**<Button Text="Dial" Clicked="Button_Clicked"/>**

The **Clicked** event is set to an event handler named **Button_Clicked**. This handler is located in the xaml.cs
file. Below is a sample method definition:

Upon defining your UI in XAML, you will have to add code to respond to user interaction.

```
private void Button_Clicked(object sender, EventArgs e)
{
PhoneDialer.Open(PhoneNumber.Text);
}
```
When the **Button** is tapped, the **Button_Clicked** method executes. The sender argument is the **Button**
object responsible for this event. You can use this to access the **Button** object or to distinguish between
multiple **Button** objects sharing the same **Clicked** event.

**RadioButton**
It is a type of button that allows users to select one option from a set. Each option is represented by one radio
button, and you can only select one radio button in a group. A **RadioButton** displays text when the **Content**
property is assigned a string. To group radio buttons, you can set the **GroupName** property on each radio
button in the group to the same value.

```
<RadioButton Content="Beginner"
GroupName="levels"
CheckedChanged="RadioButton_CheckedChanged"/>
<RadioButton Content="Intermediate"
GroupName="levels"
CheckedChanged="RadioButton_CheckedChanged"/>
<RadioButton Content="Advanced"
GroupName="levels"
CheckedChanged=”RadioButton_CheckedChanged”/>
<Label x:Name=”levelLabel”/>
```
The **RadioButton** control defines a **CheckedChanged** event that is fired when the **IsChecked** property
changes. The **CheckedChanged** event is set to an event handler named **RadioButton_CheckedChanged**.
This handler is located in the xaml.cs file. Below are sample method definition and output:

```
private void RadioButton_CheckedChanged(object sender, CheckedChangedEventArgs e)
{
RadioButton button = sender as RadioButton;
levelLabel.Text = $"You have chosen {button.Content}";
}
```
**SearchBar**
It is a user input control used to initiate a search. The **SearchBar** control supports placeholder text, query
input, search execution, and cancellation. It has a **Placeholder** property that can be set to define the hint
text in the query input box. The following code instantiates a **SearchBar** in XAML with the optional
**Placeholder** property set:

```
<SearchBar Placeholder="Search items..."/>
A search can be executed using the SearchBar control by attaching an event handler to either the following:
```
- **SearchButtonPressed** is called when the user either clicks the search button or presses the
    enter key.
- **TextChanged** is called anytime the text in the query box is changed.

The example below shows an event handler attached to the **TextChanged** event and uses a **ListView** to
display search results.

```
<SearchBar TextChanged="SearchBar_TextChanged"/>
<ListView x:Name="searchResults">
```
The **TextChanged** event is set to an event handler named **SearchBar_TextChanged**. This handler is
located in the xaml.cs file.


