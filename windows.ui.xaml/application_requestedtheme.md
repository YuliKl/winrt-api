---
-api-id: P:Windows.UI.Xaml.Application.RequestedTheme
-api-type: winrt property
---

<!-- Property syntax
public Windows.UI.Xaml.ApplicationTheme RequestedTheme { get;  set; }
-->

# Windows.UI.Xaml.Application.RequestedTheme

## -description
Gets or sets a value that determines the light-dark preference for the overall theme of an app.

## -xaml-syntax
```xaml
<application RequestedTheme="applicationThemeMemberName" .../>
```


## -property-value
A value of the enumeration.

## -remarks
There are two built in themes: "Light" and "Dark". By default your app runs using the "Dark" theme (in the themeresources.xaml file, the key name for the "Dark" resources is "Default"). You can set the app's [RequestedTheme](application_requestedtheme.md) property to specify which theme is used.

The theme can only be set when the app is started, not while it’s running. Attempting to set [RequestedTheme](application_requestedtheme.md) while the app is running throws an exception (**NotSupportedException** for Microsoft .NET code). If you give the user an option to pick a theme that's part of app UI, you must save the setting in the app data and apply it when the app is restarted.

There is also a "HighContrast" theme that uses system values, but apps and app code use a different technique for switching the app to high contrast. The [RequestedTheme](application_requestedtheme.md) property is ignored if the user is running in high contrast mode. See [High-contrast themes](http://msdn.microsoft.com/library/fd7ca6f6-a8f1-47d8-aa6c-3f2ec3168c45) and [XAML high contrast style sample](http://go.microsoft.com/fwlink/p/?LinkID=254993).

Although the app can't switch the themes at run-time, the user can (starting with Windows 8.1). For example, a user might enable a high-contrast theme while your app is running, by using the Alt+Shift+PrtScn key shortcut. If this happens, the XAML resource system will recalculate the resource values for any [{ThemeResource} markup extension](http://msdn.microsoft.com/library/8a1c79d2-9566-44aa-b8e1-cc7adad1bcc5) usage. Theme-appropriate resources such as colors and brushes then use values appropriate for the current theme, even though it wasn't the app that requested that theme originally.

An app can change specific theme values at run-time after [Application.RequestedTheme](application_requestedtheme.md) is applied, if it uses the [FrameworkElement.RequestedTheme](frameworkelement_requestedtheme.md) property and sets values on specific elements in the UI.

The resources that are theme-specific are typically defined in a separate resource dictionary in XAML. This resource dictionary comes from the [ThemeDictionaries](resourcedictionary_themedictionaries.md) property of the primary [ResourceDictionary](resourcedictionary.md) that is used for control templates. The default system resource dictionary for theme-specific resources is named ThemeResources.xaml. Find this file under the path \include\winrt\xaml\design in your Windows Software Development Kit (SDK) for Windows 8 installation location.



> [!NOTE]
> On Windows, setting [RequestedTheme](application_requestedtheme.md) to [ElementTheme.Default](elementtheme.md) will always result in "Dark" being the theme. On Windows Phone, using the [ElementTheme.Default](elementtheme.md) value will result in a query for the system theme, as set by the user.

## -examples

## -see-also
[FrameworkElement.RequestedTheme](frameworkelement_requestedtheme.md), [XAML requested theme sample](http://go.microsoft.com/fwlink/p/?LinkId=306608), [High-contrast themes](http://msdn.microsoft.com/library/fd7ca6f6-a8f1-47d8-aa6c-3f2ec3168c45)