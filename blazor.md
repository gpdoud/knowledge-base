# Blazor

- Blazor server run on the server (similar to MVC)
- Blazor WebAssembly runs solely on the browser

## Page
- @page directive defines the route:  (i.e. "/home")
- Html follows
- @code directive contains C# code
  * [Parameter] attribute defines a property as a url path variable
```
    [Parameter]
    public int Id { get; set; } = 0;
```
- 
