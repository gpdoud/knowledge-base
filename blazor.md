# Blazor

- Blazor server run on the server (similar to MVC)
- Blazor WebAssembly runs solely on the browser
- Create a new blazor page with:
```csharp
dotnet new razorcomponent -n Todo -o Pages
```
- Razor component file names must start with a capital letter (i.e. Todo.razor)
- Start binding process with: `dotnet watch`
- Component can be initialized in: 
```csharp
protected override void OnInitialized() { .. } OR
protected override async Task OnInitializedAsync() { .. }
```
- Creating a class used as a service
```csharp
public class SampleService { .. }
// in builder area of Program.cs
builder.Services.AddSingleton<SampleService>();
// to inject service into component
@inject SampleService sampSvc;
// calling the service from the OnInitializedAsync()
protected override async Task OnInitializedAsync() {
  sampSvc.xxx()
}
```

## Page
- @page directive defines the route:  (i.e. "/home")
- Html follows
- @code directive contains C# code
  * [Parameter] attribute defines a property as a url path variable
```csharp
    [Parameter]
    public int id { get; set; } = 0;
```
- @bind to bind a C# variable to an HTML object
```XML
<input @bind={id} />
```
- Function to call on button click
```csharp
<button @onclick={clicked}>Click Me!</button>
//
private void clicked() { .. }
```
Blazor components can be used in a hierarchy similar to Angular components
- For a parent to pass data to a child, the child must define the data and add the [Parameter] attribute.

Data can be passed to all child components by using:
```XML
<CascadingValue Name=xxx Value=yyy />
```
All child components placed inside have access to all the data by using CascadingParameter(Name=xxx) attribute

```csharp
@code {
  [CascadingParameter(Name=xxx)]
  public string ParamName { get; set; }
}
```

## AppState

Sharing data with any component (similar to a Service in Angular)

- Create a class containing the data to share
```c#
// define the class
public class LoggedInUser {
  public User user { get; set; }
}
// Add a scoped service
builder.Services.AddScoped<LoggedInUser>();
// Inject the service
@page "/"
@inject LoggedInUser loggedInUser

loggedInUser.user = new User();
```