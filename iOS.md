# Best practices for iOS development at NRK

Always leave code cleaner than you found it, [Uncle Bob says](http://programmer.97things.oreilly.com/wiki/index.php/The_Boy_Scout_Rule)
Write code like you care - both for the whole app and your individual part
Refactor old sins to best of your current knowledge

## Architecture

## Dokumentation

1. Confluence is used for general documentation
1. HeaderDoc can be used for classes, structs, methods 
1. Code should be self documentating and self explainatory as much as possible
  * If it is: Don't write comments for such code
  * If it isn't: Write comments for exceptional and complex code
1. Readability trumps coolness

## Spacing and Indentation

* Indent using 4 spaces rather than tabs. This should be [configured on the project](https://raw.githubusercontent.com/nrkno/best-practice/master/assets/xcode spacing.png)

* Method braces and other braces (`if`/`else`/`switch`/`while` etc.) always open on the same line as the statement but close on a new line.
* Don't use parentheses.
* Tip: You can re-indent by selecting some code (or ⌘A to select all) and then Control-I (or Editor\Structure\Re-Indent in the menu).

**Preferred:**
```swift
if video.isPlaying {
    // Do something
} else {
    // Do something else
}
```

**Not Preferred:**
```swift
if video.isPlaying
{
  // Do something
}
else {
  // Do something else
}
```

## Discussions

Accountability/ownership of code

## Inspiration

[iOS Good Practices](https://github.com/futurice/ios-good-practices)

[API Design Guide](http://apiguide.readthedocs.io/en/latest/)

[Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
