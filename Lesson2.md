## .NET Multi-platform App UI (.NET MAUI)
- .NET Multi-platform App UI (.NET MAUI) is a cross-platform framework for creating native mobile and desktop apps with C# and XAML.
- .NET MAUI allows you to develop apps that can run on Android, iOS, macOS, and Windows from a single shared code-base.

![Figure 1. .NET MAUI Supported platforms](https://github.com/user-attachments/assets/24b1773e-1272-44c7-8280-493bde7279fa)

- .NET MAUI is open-source and is the evolution of Xamarin.Forms, extended from mobile to desktop scenarios, with UI controls rebuilt from the ground up for performance and extensibility. If you've previously used Xamarin.Forms to build cross-platform user interfaces, you'll notice many similarities with .NET MAUI. However, there are also some differences. Using .NET MAUI, you can create multi-platform apps using a single project, but you can add platform-specific source code and resources if necessary. One of the key aims of .NET MAUI is to enable you to implement as much of your app logic and UI layout as possible in a single code-base.

## How .NET MAUI Works

.NET MAUI unifies Android, iOS, macOS, and Windows APIs into a single API that allows a write-once run-anywhere developer experience while additionally providing deep access to every aspect of each native platform.

## Key Components

### Platform-Specific Frameworks
.NET 6 or greater provides a series of platform-specific frameworks for creating apps:
- **.NET for Android**
- **.NET for iOS**
- **.NET for Mac Catalyst**
- **Windows UI 3 (WinUI 3) library**

### Base Class Library (BCL)
These frameworks all have access to the same .NET Base Class Library (BCL). This library abstracts the details of the underlying platform away from your code. The BCL depends on the .NET runtime to provide the execution environment for your code.

- **Execution Environment**:
  - **Android, iOS, macOS**: Implemented by Mono, an implementation of the .NET runtime.
  - **Windows**: .NET CoreCLR provides the execution environment.

## UI and Code Sharing

While the BCL enables apps running on different platforms to share common business logic, the various platforms have different ways of defining the user interface for an app. They provide varying models for specifying how the elements of a user interface communicate and interoperate.

You can craft the UI for each platform separately using the appropriate platform-specific framework (.NET for Android, .NET for iOS, .NET for Mac Catalyst, or WinUI 3), but this approach requires you to maintain a code-base for each individual family of devices.

## Unified Framework

.NET MAUI provides a single framework for building the UIs for mobile and desktop apps. The following diagram shows a high-level view of the architecture of a .NET MAUI app:

![.NET MAUI Architecture](https://github.com/user-attachments/assets/8d7e4a39-b0e0-4c2a-81f5-c690ff4b3e84)



