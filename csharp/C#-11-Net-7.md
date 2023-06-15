C# 11

## Object required initialization

When creating a class with properties that MUST be initialized, 
there is a new 'required' keyword that can be added to the property
definition

```cs
class Abc {
    public required string firstname { get; init; }
    public required string lastname { get; init; }
}
```

## Literal strings (triple or more double quotes)

Literal strings allow formatting the string directly by surrounding the string with at least 3 or more quotes

```cs
var str = """
    This is a literial string
    you can format it just by typing
    it can contain "quotes"
        and further indents
    if a triple set os quotes 
    are needed in the string, 
    the delimiter could just be four
    double quotes
"""

They can be interpolated strings using one
or more dollar signs. The number of curly braces
must match the number of dollar signs

```cs
var str = $$"""{{aVariable}}"""
```

## UTF-8 string

To create a UTF-8 string, just append 'u8' after the 
closing final quote.

```cs
var str = "This is a string"u8
```