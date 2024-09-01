# Visual Controls

## Building Blocks

A .NET MAUI project initially contains:

- MauiProgram.cs file – contains the code for creating and configuring the Application object.
- App.xaml and App.xaml.cs files – provide UI resources and create the initial window for the application.
- AppShell.xaml and AppShell.xaml.cs files – specify the initial page for the application and handle the registration of pages for navigation routing.
- MainPage.xaml and MainPage.xaml.cs files – define the layout and UI logic for the page displayed by default in the initial window.

A .NET MAUI project also contains a default set of application resources such as images, icons, fonts, and default bootstrap code for each platform.

## The Application Class

- The **App** class represents the .NET MAUI application as a whole. 
- It inherits a default set of behaviors from Microsoft.Maui.Controls.Application.
- The App class is instantiated and loaded by the bootstrap code for each platform.
- The constructor of the App class will, in turn, usually create an instance of the AppShell class and assign it to the MainPage property.
- This code controls the first screen the user sees through what is defined in the AppShell.

The App class also contains:

- Methods for handling life-cycle events, including when the app is sent to the background.
- Methods for creating new Windows for the application. The .NET MAUI application, by default, has a single window but can create and launch additional windows, which is helpful in desktop and tablet applications.

## Navigation Structures

## Shell

.NET MAUI Shell reduces the complexity of app development by providing the fundamental features that most apps require, including:

- A single place to describe the visual hierarchy of an app.
- A common navigation user experience.
- A URI-based navigation scheme that permits navigation to any page in the app.
- An integrated search handler.

In a .NET MAUI Shell app, the visual hierarchy of the app is described in a class that subclasses the Shell class.

This class can consist of three main hierarchical objects:

- FlyoutItem or TabBar: A FlyoutItem represents one or more items in the flyout and should be used when the navigation pattern for the app requires a flyout.
- A TabBar represents the bottom tab bar and should be used when the navigation pattern for the app begins with bottom tabs and doesn't require a flyout.
- Tab – represents grouped content, navigable by bottom tabs.
- ShellContent – represents the ContentPage objects for each tab.

These objects do not represent any user interface but rather the organization of the app's visual hierarchy. Shell will take these objects and produce the navigation user interface for the content.

## Pages

- Pages are the root of the UI hierarchy in .NET MAUI inside of a Shell. 
- A solution includes a class called MainPage, which derives from **ContentPage** , the simplest and most common page type. 
- A content page displays a single view.

.NET MAUI has several other built-in page types, too, including the following:

- TabbedPage: This is the root page used for tab navigation. A tabbed page contains child page objects, one for each tab.
- FlyoutPage: This page enables the implementation of a master/detail style presentation. A flyout page contains a list of items. When selecting an item, a view displaying the details for that item appears.
- NavigationPage: This page provides a hierarchical navigation experience where you can navigate through pages, forwards and backwards, as desired.

Other page types are available and are mostly used for enabling different navigation patterns in multi-screen
apps.

## Views

A content page typically displays a view. A view enables users to retrieve and present data in a specific manner.

- The default view for a content page is a **ContentView** , which displays items as-is. If the view is shrunk, items may disappear from the display until the view is resized.
- A **ScrollView** enables the display of items in a scrolling window; if the window is shrunk, items will be displayed by scrolling up and down.
- A **CarouselView** is a scrollable view that lets the user swipe through a collection of items.
- A **CollectionView** can retrieve data from a named data source and present each item using a template as a format. There are many other types of views available as well.

## Controls and Layouts

- A view can contain a single control, such as a button, label, or text box.
- Note that a view is also a control so it can contain another view.
- However, a user interface restricted to a single control would not be very useful, so controls are positioned in a layout.

- A layout defines the rules by which the controls are displayed relative to each other.
- It is also a control so it can be added to a view.
- Looking at the default MainPage.xaml file, a page/view/layout/control hierarchy can be seen in action.
- In this XAML code, the VerticalStackLayout element is just another control that enables fine-tuning the layout of other controls.

```
<ContentPage ...>
<ScrollView ...>
<VerticalStackLayout>
<Image ... />
<Label ... />
<Label ... />
<Button ... />
</VerticalStackLayout>
</ScrollView>
</ContentPage>
```
Some of the common controls used to define layouts are:

- **VerticalStackLayout** and **HorizontalStackLayout** , optimized stack layouts that lay out controls in a top-to-bottom or left-to-right stack. A StackLayout is also available, which has a property named StackOrientation, which can be set to Horizontal or Vertical. On a tablet or phone, modifying this property in an application code enables the adjustment of the display if the user rotates the device.

- **AbsoluteLayout** , which is used to set exact coordinates for controls.
- **FlexLayout** , is similar to StackLayout, except that it enables wrapping the child controls it contains if they do not fit in a single row or column. This layout also provides options for alignment and adapting to different screen sizes. For example, a FlexLayout control can align its child control to the left, right, or center when arranged vertically. When aligned horizontally, controls can be justified to ensure even spacing. A horizontal FlexLayout could be used inside a ScrollView to display a horizontally scrollable series of frames (each frame could be a vertically arranged FlexLayout).
- **Grid** , which positions its child elements in a grid of rows and columns. Column and row sizes can be defined, as well as spans, so grid layouts do not necessarily have a "checkerboard look" to them.

```
Figure 1. Common layout types.
```
## Tuning a Layout

It is useful to add a little breathing space around a control. Each control has a Margin property that is respected by the layouts. Think of margin as the control pushing others away.

All the layouts also have a Padding property that keeps any of their children from getting close to the border of the layout. One way to think of this is that all the controls are in a box with padded walls.

Another useful whitespace setting is the Spacing property of VeticalStackLayout or HorizontalStackLayout. This is the space between all the children of the layout. This is additive with the control’s own margin, so the actual whitespace will be margin plus spacing.



