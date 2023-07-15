# TQL - Tips and techniques in C#

## `if() statement - simplifed`

In general, an `if`` with an  `else` is more complex that an `if` without an `else'.`

```cs
string Bool2String(bool b) {
    if(b) {
        return "Yes";
    } else {
        return "No";
    }
}
// a simplier way
string Bool2String(bool b) {
    if(b) {
        return "Yes";
    }
    return "No";
}
```

## Pure functions

- All data is pass as parameters
- No side effects (changing parameter values)
- No changes to data outside the method
- Results returned

## Dependency Injection

- With a constructor
- With a method

## Recursion (binary tree)

## Interfaces

## Extension Methods

## Middleware for WebAPI

## Secrets in .Net

## Check if string value is one of a finite set

Sometimes, trying to validate a string value causes some headaches because the value cannot be any string but must be from a finite set of string values. When done intractively, the list can be provided to the user in the form of a dropdown list where only valid selections can be made. But what about data passed into a program from another source.

While this can be done using a series of `if()` statements or with the `switch()` statement, a simplier approach is to create a string of all the valid values then check whether the target string exists as a substring. This can be done with a single statement.

```cs
string targetStateCode = "OH";
bool valid = "|OH|IN|KY|".Contains($"|{targetStateCode}|"); // returns true
```

In this example, imagine getting a two character code that should represent a state code that must be either 'OH', 'IN', or 'KY'. All three state codes are included in a single string with each one surrounded by vertical bars. The purpose of the vertical bars is so that the state code to check does not match part of two different state codes that happen to be located next to each other. Here what could happen if the vertical bars (or any other symbol) is used.

Here is the same type of validity check though without the vertical bars. Now assume the state code for Hawaii (HI) is checked. It does not match 'OH', 'IN', or 'KY', but it does match the 'H' of 'OH' and the 'I' of 'IN'. This would result in a false valid return value.

```cs
string targetStateCode = "HI";
bool valid = "OHINKY".Contains($"{targetStateCode}"); // returns true incorrectly
bool valid = "-OH-IN-KY-".Contains($"-{targetStateCode}-"); // returns false
```

## Count the number of unique occurances within a collection

Given a collection of values, whether atomic values (strings, numbers, etc.) or objects (records, tuples, etc.), count the number of occurances of values for a variety of reasons. It may be to display the value that occurs the most or least frequently or it may be simply to provide the number of occurances for each value. Using a generic key/value pair collection class is a good tool to address this issue.

Assume, given a string containing letters and numbers, you are asked to count the number of occurances (case insensitive) of only each letter within the string and return the number of occurances for each letter. Numbers and symbols are skipped.

```cs
string source =
    "The Peacocks shocked the sports world by becoming the first No. 15 seed "
    + "to advance to the Elite Eight. They were also seeking to make more history "
    + "with a berth to the Final Four. Saint Peter's ultimately came up just short "
    + "of the 83-year-old tournament's semifinal round, but were successful in "
    + "inspiring fans around the country who root for the underdog.";
// declare a dictionary with a key of char and a value of int
Dictionary<char, int> charsDict = new Dictionary<char, int>();
// convert the source from a string to an array of chars
char[] chars = source.ToCharArray();
// iterate thru the chars array
foreach (var ch in chars) {
    // skip any ch that is not a letter
    if (!char.IsLetter(ch)) {
        continue;
    }
    // to treat letters case insensitive, make them all uppercase
    char upCh = ch.ToString().ToUpper()[0];
    // check if the dictionary already has the letter
    // if not, add it with a zero for the value
    if (!charsDict.ContainsKey(upCh)) {
        charsDict.Add(upCh, 0);
    }
    // we know the dictionary has the key now
    // just increment the value
    charsDict[upCh]++;
}
// now all the input has been processed
// get a list of all the keys so they can be sorted
var keys = charsDict.Keys.ToList();
// sort key in place
keys.Sort();
// use the sorted keys to retrieve the dictionary values
foreach (var key in keys) {
    Console.WriteLine($"Char {key} occurs {charsDict[key]} time(s).");
}
// The output looks like this:
Char A occurs 15 time(s).
Char B occurs 4 time(s).
Char C occurs 9 time(s).
Char D occurs 9 time(s).
Char E occurs 36 time(s).
Char F occurs 8 time(s).
Char G occurs 5 time(s).
Char H occurs 16 time(s).
Char I occurs 16 time(s).
Char J occurs 1 time(s).
Char K occurs 4 time(s).
Char L occurs 9 time(s).
Char M occurs 7 time(s).
Char N occurs 17 time(s).
Char O occurs 26 time(s).
Char P occurs 5 time(s).
Char R occurs 20 time(s).
Char S occurs 20 time(s).
Char T occurs 31 time(s).
Char U occurs 12 time(s).
Char V occurs 1 time(s).
Char W occurs 5 time(s).
Char Y occurs 6 time(s).
```

