# MAUI

* The `MauiProgram.cs` file that contains the code for creating and configuring the Application object.

* The `App.xaml` and `App.xaml.cs` files that provide UI resources and create the initial window for the application.

* The `AppShell.xaml` and `AppShell.xaml.cs` files that specify the initial page for the application and handle the registration of pages for navigation routing.

* The `MainPage.xaml` and `MainPage.xaml.cs` files that define the layout and UI logic for the page displayed by default in the initial window.

* `InitializeComponent` must be called in `App.xaml.cs` constructor when XAML is used to describe the UI

* Most of the common types used by a MAUI app are in the `Microsoft.Maui.Dependencies` and `Microsoft.Maui.Extensions` packages.

* Most MAUI controls are located in the `Microsoft.Maui.Controls` namespace, while the `Microsoft.Maui` namespace defines utility types such as Thickness, and the `Microsoft.Maui.Graphics` namespace includes generalized types such as Color.

# Creating MAUI APP

* No changes to App, AppShell, or MainProgram
* Create static class for app
* Add controls in MainPage.xaml within ContentPage and VerticalStackLayout (or another layout)
* an ENTRY is a textbox
* Control attributes
    * x:Name - similar to ID
    * Text - on button face
    * FontSize - just an integer
    * IsEnabled - boolean
    * Clicked - method to call

# Property Elements
```xml
<Label Text="Username" TextColor="Black" FontSize="42" FontAttributes="Bold,Italic">
    <Label.GestureRecognizers>
        <TapGestureRecognizer NumberOfTapsRequired="2" />
    </Label.GestureRecognizers>
</Label>
```

# Event handlers

    public void OnClick(object sender, EventArgs args) { .. }

# Markup Extensions

* This is how to change a control's attribute value at runtime.

* The class must implement `Microsoft.Maui.Controls.Xaml.IMarkupExtension` which provides the ProvideValue(IServiceProvider serviceProvider) method

    [ContentProperty ("Member")]
    public class StaticExtension : IMarkupExtension
    {
        public string Member {get; set;}
        public object ProvideValue (IServiceProvider serviceProvider)
        {
            ...
        }
    }

    <Label Text="Hello, World!"
            Grid.Row="0"
            SemanticProperties.HeadingLevel="Level1"
            FontSize="{x:Static Member=mycode:MainPage.MyFontSize}"
            HorizontalOptions="CenterAndExpand"/>

* DeviceInfo.Platform = { "Android", "iOS", "WinUI", "macOS" }
    * DevoiceInfo.iOS = "iOS"

    <VerticalStackLayout>
        <VerticalStackLayout.Padding>
            <OnPlatform x:TypeArguments="Thickness">
                <On Platform="iOS" Value="30,60,30,30" />
            </OnPlatform>
        </VerticalStackLayout.Padding>
    <!--XAML for other controls goes here -->
    ...
    </VerticalStackLayout>

    <VerticalStackLayout Padding="{OnPlatform iOS='30,60,30,30', Default='30'}">
    <!--XAML for other controls goes here -->
    </VerticalStackLayout>