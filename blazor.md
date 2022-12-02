# Blazor

- Blazor server run on the server (similar to MVC)
- Blazor WebAssembly runs solely on the browser
- Create a new blazor page with:
```
dotnet new razorcomponent -n Todo -o Pages
```
- Razor component file names must start with a capital letter (i.e. Todo.razor)
- Start binding process with: `dotnet watch`
- Creating a class used as a service
```
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
```
    [Parameter]
    public int id { get; set; } = 0;
```
- @bind to bind a C# variable to an HTML object
```
<input @bind={id} />
```
- Function to call on button click
```
<button @onclick={clicked}>Click Me!</button>
//
private void clicked() { .. }
```
