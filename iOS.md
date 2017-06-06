# NRK iOS Best Practices

"Always leave code cleaner than you found it", [Uncle Bob](http://programmer.97things.oreilly.com/wiki/index.php/The_Boy_Scout_Rule)  
Write code like you care - both for the whole app and your individual part  
Refactor old sins to best of your current knowledge

## Xcode

Groups in Xcode should match folders on disk.

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

## Methods

Methods should be as short and readable as possible and do one thing  
Preferably only one return statement/one expected exit  
* Preconditioning can be one way of achieving this

## Code Quality

Fix warnings, treat warnings as errors. [How to set this in Xcode](assets/warnings-as-errors.png)  
Use named constats, enums and structs. Don't use "magical" numbers or strings
* Tip: If you have to search for strings in general code  

Put constants in its rightful place; in the class if only used in one class or in a shared class if used multiple places  
Be conscious of access control, restrict access to parts of your code that's private. Also for UI elements (IBOutlets).  

## Building User Interface

Use Storyboards for navigation and relationship between views  
Keep Storyboards maintainable sizewise - use multiple smaller ones instead of one large  
Use auto layout, contraints, size classes and stackviews to reuse interfaces between multiple screensizes  
Use designable and inspectable  
Use xibs for reusable components  


## Linting

In order to ensure both consistent code formatting and help us conform to established best practices we use linters in our projects.

#### SwiftLint
[SwiftLint](https://github.com/realm/SwiftLint) is used in Swift based projects.

#### Installation

[SwiftLint](https://github.com/realm/SwiftLint) can be installed locally (Homebrew/pre-built package) or added to your project as a CocoaPods package.

**TODO:** Decide local Installation vs CocoaPods

#### When to run
Since SwiftLint is quite fast, our recommended setup is to run linting as part of the build process in XCode (Run Script Phase).

If per build runs affect productivity, linting should at least be run as part of the CI workflow.

#### Linting rules
We aim at using the same set of linting rules for most projects.
An updated and curated SwiftLint configuration file can be found [here].

When adding linting to an existing project, it could be easier to start by disabling some of the rules. Then, as you correct more issues, move againts the agreed configuration.   


## Discussions

Accountability/ownership of code

## Inspiration

[iOS Good Practices](https://github.com/futurice/ios-good-practices)

[API Design Guide](http://apiguide.readthedocs.io/en/latest/)

[Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
