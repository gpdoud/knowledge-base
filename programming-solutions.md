# Progamming Solutions

This document was created to help provide solution to those less experienced programmers who may have significant knowledge of the programming language syntax, but not the experience of how to construct solutions to functional problems.

## Table of Contents

- [Generate the Fibonacci sequence](#generate-the-fibonacci-sequence)
- [Count the number of unique occurances within a collection](#count-the-number-of-unique-occurances-within-a-collection)

## Generate the Fibonacci sequence

The Fibonacci numbers are a sequence of numbers starting with 1, 1 where the next number is the sum of the previous two numbers: `1, 1, 2, 3, 5, 8, etc.`. It is relatively easy to generate but the sequence is somewhat unique and does not occur that often in other applications.

```cs
// generate the number up to 1000
const int maxNbr = 1000;
// a & b are the last two numbers generated
// both are initialized to 1 
int a = 1;
int b = 1;
// c is the most current generated number
int c = -1;
// output the first two numbers
Console.Write($"{a}, {b}");
// infinite loop will break
while(true) {
    // calculate the next number
    c = a + b;
    // check if the number if greater than the max
    if (c > maxNbr) break;
    // if not, output the number
    Console.Write($", {c}");
    // set a & b to the values of b & c
    a = b;
    b = c;
}
// output
1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610, 987
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