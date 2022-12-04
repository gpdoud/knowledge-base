# Visual Studio Code

## Omnisharp

For VSC to format the C# code requires configuring Omnisharp.

Start by creating the omnisharp.json file:

```json
// file: omnisharp.json
{
    "FormattingOptions": {
        "newLine": "\n",
        "useTabs": false,
        "tabSize": 4,
        "indentationSize": 4,

        "NewLinesForBracesInTypes": false,
        "NewLinesForBracesInMethods": false,
        "NewLinesForBracesInProperties": false,
        "NewLinesForBracesInAccessors": false,
        "NewLinesForBracesInAnonymousMethods": false,
        "NewLinesForBracesInControlBlocks": false,
        "NewLinesForBracesInAnonymousTypes": false,
        "NewLinesForBracesInObjectCollectionArrayInitializers": false,
        "NewLinesForBracesInLambdaExpressionBody": false,

        "NewLineForElse": false,
        "NewLineForCatch": false,
        "NewLineForFinally": false,
        "NewLineForMembersInObjectInit": false,
        "NewLineForMembersInAnonymousTypes": false,
        "NewLineForClausesInQuery": false
    }
}
```

In the default folder (cd), create a folder named `.omnisharp`.

Copy the omnisharp.json file to that directory.

Open the user.settings in VSC by opening the Command Pallete and enter "open user settings (JSON)"

Add the following to the file:

    "omnisharp.enableEditorConfigSupport": false,

You may need to restart VSC.
