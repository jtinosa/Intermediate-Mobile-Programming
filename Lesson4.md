```markdown
# User Interface with XAML

## Fundamentals

A **markup language** is a computer language used to introduce various elements in a document. Elements are described using predefined tags with specific meanings in the context of their domain. For example, Hypertext Markup Language (HTML) is used to create webpages displayable in web browsers.

**Extensible Application Markup Language (XAML)** is a declarative language created by Microsoft, based on XML. XAML was designed to simplify the process of creating user interfaces (UI) in applications.

### Benefits of UI with XAML

- **Separation of UI and behavior**: Makes it easier to manage both aspects.
- **Division of labor**: Designers can focus on XAML, while programmers focus on code.
- **Tooling friendly**: Allows use of design tools for creating XAML layouts graphically.

### Creating UI Controls with XAML

1. **Instantiate UI control types** using Object Element Syntax:
   ```xml
   <Label />
   ```
   This is equivalent to the C# code: `new Label();`

2. **Add namespace instructions** to use controls:
   ```xml
   <ContentPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
                xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
                x:Class="MyMauiApp.MainPage">
     ...
   </ContentPage>
   ```

   - First `xmlns`: Tags without prefix refer to .NET MAUI classes.
   - Second `xmlns:x`: Defines prefix for XAML-intrinsic elements and attributes.
   - `x:Class`: Specifies the fully qualified .NET class name.

3. **Set properties** on UI controls using attributes:
   ```xml
   <Label Text="Username" TextColor="Black"/>
   ```

## Event Handling

### Button

```xml
<Button Text="Dial" Clicked="Button_Clicked"/>
```

```csharp
private void Button_Clicked(object sender, EventArgs e)
{
    PhoneDialer.Open(PhoneNumber.Text);
}
```

### RadioButton

```xml
<RadioButton Content="Beginner"
             GroupName="levels"
             CheckedChanged="RadioButton_CheckedChanged"/>
<RadioButton Content="Intermediate"
             GroupName="levels"
             CheckedChanged="RadioButton_CheckedChanged"/>
<RadioButton Content="Advanced"
             GroupName="levels"
             CheckedChanged="RadioButton_CheckedChanged"/>
<Label x:Name="levelLabel"/>
```

```csharp
private void RadioButton_CheckedChanged(object sender, CheckedChangedEventArgs e)
{
    RadioButton button = sender as RadioButton;
    levelLabel.Text = $"You have chosen {button.Content}";
}
```

### SearchBar

```xml
<SearchBar Placeholder="Search items..." TextChanged="SearchBar_TextChanged"/>
<ListView x:Name="searchResults">
```

Event handlers:
- `SearchButtonPressed`: Triggered when search button is clicked or enter key is pressed.
- `TextChanged`: Triggered anytime the text in the query box changes.
```
