# wikEddiff
wikEd diff is a free JavaScript visual diff library for inline text comparisons. It is the only available JavaScript diff library that detects and highlights block moves and that works on the word and character level. While wikEd diff has been developed and optimized for comparing Wikipedia source texts, it works great for any type of text, including program code. The library is customizable, has Unicode and multilingual support, is fully commented and documented, and is free (public domain). The script is used by the Wikipedia/MediaWiki in-browser editor wikEd and by the gadget wikEdDiff. You can test the library by checking any of these gadgets in your English Wikipedia preferences. For easy text comparisons by copy-and-pasting you can also use the wikEd diff online tool and demo. The library has also been ported to PHP and is available as a MediaWiki extension.

# Usage
To call this library, please use the following code:
```js
 var wikEdDiff = new WikEdDiff();
 var diffHtml = wikEdDiff.diff( oldVersionString, newVersionString );
```
To raw code of the library is available under:
```js
https://en.wikipedia.org/w/index.php?title=User:Cacycle/diff.js&action=raw&ctype=text/javascript
```
To use the library in other JavaScript programs, add the following line to the HTML <head> tag:
```js
<script src="https://en.wikipedia.org/w/index.php?title=User:Cacycle/diff.js&action=raw&ctype=text/javascript"></script>
```
## Customization
The library is fully customizable. The following settings can be changed on your your User:YourUsername/common.js page. Please check the top of the diff.js program code for additional settings.Please see wikEdDiff for wikEdDiff-specific settings.

Colors can be customized by adding CSS code to your User:YourUsername/common.css page. Please check the code for available CSS classes.

Block mark symbols:
```js
var wikEdDiffConfig; if (wikEdDiffConfig === undefined) { wikEdDiffConfig = {}; }
wikEdDiffConfig.cssMarkLeft = '◀';
wikEdDiffConfig.cssMarkRight = '▶';
```
Show complete un-clipped diff text:
```js
var wikEdDiffConfig; if (wikEdDiffConfig === undefined) { wikEdDiffConfig = {}; }
wikEdDiffConfig.fullDiff = true;
```
Enable block move layout with highlighted blocks and marks at their original positions (default):
```js
var wikEdDiffConfig; if (wikEdDiffConfig === undefined) { wikEdDiffConfig = {}; }
wikEdDiffConfig.showBlockMoves = true;
```
Reject blocks if they are too short and their words are not unique, prevents fragmentated diffs for very different versions (default):
```js
var wikEdDiffConfig; if (wikEdDiffConfig === undefined) { wikEdDiffConfig = {}; }
wikEdDiffConfig.unlinkBlocks = true;
```
Reject blocks if shorter than this number of real words (default):
```js
var wikEdDiffConfig; if (wikEdDiffConfig === undefined) { wikEdDiffConfig = {}; }
wikEdDiffConfig.blockMinLength = 3;
```
Enable character-refined diff (default):
```js
var wikEdDiffConfig; if (wikEdDiffConfig === undefined) { wikEdDiffConfig = {}; }
wikEdDiffConfig.charDiff = true;
```
Enable recursive diff to resolve problematic sequences (default):
```js
var wikEdDiffConfig; if (wikEdDiffConfig === undefined) { wikEdDiffConfig = {}; }
wikEdDiffConfig.recursiveDiff = true;
```
Maximum recursion depth (default):
```js
var wikEdDiffConfig; if (wikEdDiffConfig === undefined) { wikEdDiffConfig = {}; }
wikEdDiffConfig.recursionMax = 10;
```
Display blocks in differing colors (rainbow color scheme):
```js
var wikEdDiffConfig; if (wikEdDiffConfig === undefined) { wikEdDiffConfig = {}; }
wikEdDiffConfig.coloredBlocks = false;
```
Show debug infos and stats (block and group data object) in browser console:
```js
var wikEdDiffConfig; if (wikEdDiffConfig === undefined) { wikEdDiffConfig = {}; }
wikEdDiffConfig.debug = true; }
```
Show timing results in browser console:
```js
var wikEdDiffConfig; if (wikEdDiffConfig === undefined) { wikEdDiffConfig = {}; }
wikEdDiffConfig.debugTime = true; }
```
Run unit tests to prove correct working, display results in browser console:
```js
var wikEdDiffConfig; if (wikEdDiffConfig === undefined) { wikEdDiffConfig = {}; }
wikEdDiffConfig.unitTesting = true;
```
## Text type customization
The regular expressions for splitting the texts are optimized for natural language containing wiki markup. While this default also works great for other text types such as source code, it can be customized:
```js
wikEdDiffConfig.regExp.split = {
  paragraph: new RegExp('…', 'g'),
  line: new RegExp('…', 'g'),
  sentence: new RegExp('…', 'g'),
  word: new RegExp('…', 'g'),
  character: new RegExp('…', 'g')
};
```
