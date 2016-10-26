# NRK iOS Best Practices

"Always leave code cleaner than you found it", [Uncle Bob](http://programmer.97things.oreilly.com/wiki/index.php/The_Boy_Scout_Rule)  
Write code like you care - both for the whole app and your individual part  
Refactor old sins to best of your current knowledge

## Xcode

### Version

The recommended version of Xcode (and Swift) for all purposes is the current available [in the App Store](https://itunes.apple.com/no/app/xcode/id497799835?mt=12).

## Documentation

* Confluence is used for general documentation
* [HeaderDoc](https://www.raywenderlich.com/66395/documenting-in-xcode-with-headerdoc-tutorial) can be used for classes, structs, methods
* Code should be self explanatory and self explainatory as much as possible
  * If it is: Don't write comments for such code
  * If it isn't: Write comments for exceptional and complex code
* Readability trumps coolness

## Spacing and Indentation

* Indent using 4 spaces rather than tabs. This should be [configured on the project](https://raw.githubusercontent.com/nrkno/best-practice/master/assets/xcode spacing.png)
* Method braces and other braces (`if`/`else`/`switch`/`while` etc.) always open on the same line as the statement but close on a new line.
* Don't use parentheses.
* Tip: You can re-indent by selecting some code (or ⌘A to select all) and then Control-I (or Editor\Structure\Re-Indent in the menu).

**Preferred**
```swift
if video.isPlaying {
    // Do something
} else {
    // Do something else
}
```
**Not Preferred**
```swift
if video.isPlaying
{
  // Do something
}
else {
  // Do something else
}
```

## Comments

 When they are needed, comments should be used to explain **why** a particular piece of code does something instead of **what**. Any comments that are used must be kept up-to-date or deleted.

**Preferred**
```swift
/**
  so far this is the scroll-to-bottom method that works best with proper animation
  and no issues so far regardless of a scrollviews content size. if this looks and
  feels like a hack, it's because it is. by creating a rect that's 1x1, pointed at
  the bottom-right side of the scrollview's content and telling it to scroll there
  regardless of insets and offsets it will scroll to the very bottom.
*/
func scrollToBottom() {
    let attemptsToRecreateUploadTasksForBackgroundSessions = self.collectionView.contentSize
    let bottomRect = CGRect(x: contentSize.width - 1, y: contentSize.height - 1, width: 1, height: 1)
    let visibleRect = self.collectionView.layer.visibleRect
    if !visibleRect.intersects(bottomRect) {
        self.collectionView.scrollRectToVisible(bottomRect, animated: true)
    }
}
```

**Not Preferred**
```swift
// scrolls to the bottom of the view
func scrollToBottom() {
    let contentSize = self.collectionView.contentSize
    let bottomRect = CGRect(x: contentSize.width - 1, y: contentSize.height - 1, width: 1, height: 1)
    let visibleRect = self.collectionView.layer.visibleRect
    if !visibleRect.intersects(bottomRect) {
        self.collectionView.scrollRectToVisible(bottomRect, animated: true)
    }
}
```

## Discussions

Accountability/ownership of code

## Inspiration

[iOS Good Practices](https://github.com/futurice/ios-good-practices)

[API Design Guide](http://apiguide.readthedocs.io/en/latest/)

[Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
