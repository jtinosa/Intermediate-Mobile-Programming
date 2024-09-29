# XAML Pages & Layout in .NET MAUI

## **Introduction to Layout Panels**
A **layout panel** is a .NET MAUI container that holds child views and determines their size and position. They adapt automatically when the app's size changes, such as when the user rotates the device.

### **Commonly Used Layout Panels:**

| **Layout Panel**  | **Description** |
|-------------------|------------------|
| **StackLayout**   | Arranges children in a single row or column. |
| **Grid**          | Arranges children in cells created by rows and columns. |
| **AbsoluteLayout**| Uses x and y coordinates to arrange children. |
| **FlexLayout**    | Similar to StackLayout, but wraps children if they don’t fit in a row/column. |

> **Tip:** If you don’t specify a view’s size, it will adjust to fit its content.

## **Specifying View Sizes**
The `View` base class defines:
- `WidthRequest`: Sets the view's width.
- `HeightRequest`: Sets the view's height.

Example:
```xaml
<Label 
  Text="Hello" 
  WidthRequest="100" 
  HeightRequest="300" 
  BackgroundColor="Silver" />
```

The layout panel reads these values and tries to accommodate them. If there isn't enough space, it might ignore them.

> **Note:** `WidthRequest` and `HeightRequest` set the requested size, but not the actual size at runtime. To get the actual size, use the `Width` and `Height` properties.

## **Positioning Views:**
The `View` base class has two properties for positioning:
- `VerticalOptions`
- `HorizontalOptions`

These properties are of type `LayoutOptions` and affect the view’s position within its layout panel.

### **Layout Alignment Values:**
- **Start**: Aligns to the left (horizontal) or top (vertical) of the parent layout.
- **Center**: Centers the view horizontally or vertically.
- **End**: Aligns to the right (horizontal) or bottom (vertical) of the parent layout.
- **Fill**: Expands the view to fill the available space.

Example XAML for alignment:
```xaml
<Label Text="Start" HorizontalOptions="Start" BackgroundColor="Silver" />
<Label Text="Center" HorizontalOptions="Center" BackgroundColor="Silver" />
<Label Text="End" HorizontalOptions="End" BackgroundColor="Silver" />
<Label Text="Fill" HorizontalOptions="Fill" BackgroundColor="Silver" />
```

## **StackLayout**

### **Description:**
- Organizes child views in a single vertical or horizontal stack.
- Can be used as a parent layout containing other layouts.

### **Key Properties:**
- `Orientation`: Defines the stack direction (Vertical or Horizontal).
- `Spacing`: Defines space between child views (default is `0`).

### **Example: Adding Views to StackLayout**
#### **C# Code Example:**
```csharp
var a = new BoxView() { Color = Colors.Silver };  
var b = new BoxView() { Color = Colors.Blue };  
var c = new BoxView() { Color = Colors.Gray };  

stack.Children.Add(a); 
stack.Children.Add(b); 
stack.Children.Add(c); 
```

#### **XAML Version:**
```xaml
<StackLayout>
  <BoxView Color="Silver" />
  <BoxView Color="Blue" />
  <BoxView Color="Gray" />
</StackLayout>
```

### **Horizontal Orientation Example:**
```xaml
<StackLayout Orientation="Horizontal">
  <BoxView Color="Silver" />
  <BoxView Color="Blue" />
  <BoxView Color="Gray" />
</StackLayout>
```

### **Using Spacing:**
```xaml
<StackLayout Spacing="30">
  <BoxView Color="Silver" />
  <BoxView Color="Blue" />
  <BoxView Color="Gray" />
</StackLayout>
```

### **Expands Property in StackLayout:**
The `Expands` property allows child views to request extra space. Example values include `StartAndExpand`, `CenterAndExpand`, `EndAndExpand`, and `FillAndExpand`.

> **Example:** The `FillAndExpand` value allows the view to fill available space.

### **Illustration of Expands Property:**
The orange box represents the view, while the gray rectangle represents the extra space. Only when you use `FillAndExpand` will the view fill the extra space. Other values leave the extra space empty, but it won't be available for other views.
