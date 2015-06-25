# QuickCursorKM

> A QuickCursor redux for Keyboard Maestro - http://chauncey.io/projects/quickcursor-for-keyboard-maestro/

## Inspiration and Rationale

Inspiration for QuickCursor for Keyboard Maestro ([QuickCursorKM](https://github.com/chauncey-garrett/keyboard-maestro-quickcursorkm)) comes from the deprecated [QuickCursor](https://www.youtube.com/watch?v=-bHwcyHrRGs) (killed by sandboxing) and [tjluoma's](https://github.com/tjluoma) replacement, [edit-anywhere](https://github.com/tjluoma/edit-anywhere). Thank you tjluoma for the inspiration for this macro set!

Text typically flows easily. However, there are those moments when it just. Gets. Stuck. QuickCursorKM is there to undo that log-jam by redirecting your text-flow to a better editor. A good example: say you've made a list of things but forgot to add a hyphen (-) for Markdown formatting. No worries! Activate QuickCursorKM, edit the text in MacVim[^vim-list-edit], and you're on your way.

![](/img/quickcursor-km-palette.png)

## Creation and Extensibility

I've designed this [Keyboard Maestro](http://www.stairways.com/action/kmdiscount?REF4PDX) macro set with two types of macros:

- Builder macros with specific, iterative actions (indicated by an underscore and disabled by default) AND
- Editor macros that set or determine the editor you wish to use.

The final editor macro used by the end user is comprised of these builder macros. Built this way, the macro-program is easily extensible and updated.[^macro-sets]

You, however, need do nothing but choose a shortcut for the editor macros you wish to use.[^recommendation] You'll also want to disable any of the editor-specific macros that you don't use.

Alternatively, you can just use the `QuickCursorKM` macro itself and it'll open the text in the system default editor for `txt` files.

Additionally, in the macro `QuickCursorKM`, you may assign your favorite editor to open while selecting text from a specific application. For example, I may want to use Byword for Safari forms but edit a list I started in Pages with MacVim. **To my knowledge, no other QuickCursor alternative does this!** See the default macro for examples of how to add additional editor assignments.

## Usage

To use QuickCursorKM, place your cursor on some text. If you select specific text, that text is captured; otherwise, if no text is selected, all available text is edited.

- Run the macro `QuickCursorKM` (or one of the editor-specific variants[^default-editor]) with your hotkey. The text will open in your editor.
- Make your edits, and then once you're finished, quit the editor with `⌘Q` (don't worry; as explained below, your text is safe).

QuickCursorKM then passes the edited text back to the source application and that's all there is to it!

If for some reason the macro fails, your work has been safely saved from the beginning in one of two locations: `~/.quickcursor_km.txt` or (less likely) in the Trash can with the date appended to the filename. You should also receive an error message that can be useful in debugging.

## Supported text editors

I primarily use this QuickCursor replacement with MacVim. Here's a list of all supported QuickCursorKM editors (with affiliate links):

<ul class="inline-list">
  <li><a class="ignore-external-link-icon" href="https://atom.io">Atom</a></li>
  <li><a class="ignore-external-link-icon" href="http://www.barebones.com/products/bbedit/">BBEdit</a></li>
  <li><a class="ignore-external-link-icon" href="http://brackets.io">Brackets</a></li>
  <li><a class="ignore-external-link-icon" href="https://itunes.apple.com/us/app/byword/id420212497?mt=12&amp;uo=4&amp;at=10lKXh">Byword</a></li>
  <li><a class="ignore-external-link-icon" href="https://itunes.apple.com/us/app/foldingtext/id540003654?mt=12&amp;uo=4&amp;at=10lKXh">FoldingText</a></li>
  <li><a class="ignore-external-link-icon" href="https://itunes.apple.com/us/app/ia-writer/id439623248?mt=12&amp;uo=4&amp;at=10lKXh">iA Writer</a></li>
  <li><a class="ignore-external-link-icon" href="https://itunes.apple.com/us/app/ia-writer-pro/id775737590?mt=12&amp;uo=4&amp;at=10lKXh">iA Writer Pro</a></li>
  <li><a class="ignore-external-link-icon" href="https://github.com/macvim-dev/macvim">MacVim</a></li>
  <li><a class="ignore-external-link-icon" href="https://itunes.apple.com/us/app/marked-2/id890031187?ls=1&mt=12&at=10lKXh">Marked</a></li>
  <li><a class="ignore-external-link-icon" href="https://itunes.apple.com/us/app/multimarkdown-composer-2/id593294811?mt=12&amp;uo=4&amp;at=10lKXh">MultiMarkdown Composer</a></li>
  <li><a class="ignore-external-link-icon" href="http://www.ommwriter.com">OmmWriter</a></li>
  <li><a class="ignore-external-link-icon" href="https://developer.apple.com/library/mac/releasenotes/InterapplicationCommunication/RN-JavaScriptForAutomation/">Script Editor</a></li>
  <li><a class="ignore-external-link-icon" href="https://itunes.apple.com/us/app/smultron-7/id921128244?mt=12&amp;uo=4&amp;at=10lKXh">Smultron</a></li>
  <li><a class="ignore-external-link-icon" href="https://itunes.apple.com/us/app/taskpaper/id424281111?mt=12&amp;uo=4&amp;at=10lKXh">TaskPaper</a></li>
  <li><a class="ignore-external-link-icon" href="https://macromates.com">TextMate</a></li>
  <li><a class="ignore-external-link-icon" href="http://www.texts.io">Texts</a></li>
  <li><a class="ignore-external-link-icon" href="https://itunes.apple.com/us/app/textwrangler/id404010395?mt=12&amp;uo=4&amp;at=10lKXh">TextWrangler</a></li>
  <li><a class="ignore-external-link-icon" href="https://itunes.apple.com/us/app/ulysses/id623795237?mt=12&amp;uo=4&amp;at=10lKXh">Ulysses</a></li>
  <li><a class="ignore-external-link-icon" href="https://itunes.apple.com/us/app/writeroom/id417967324?mt=12&amp;uo=4&amp;at=10lKXh">WriteRoom</a></li>
</ul>

## Adding New Text Editors

If the text editor of your choice isn't listed, it's easy to add because of the modular nature of QuickCursorKM.

To add your editor, simply duplicate any of the editor-specific macros and replace the path and the bundle-id variables with the analogous text for your app. If you don't know the bundle-id of your editor, you may leave the variable blank: QuickCursorKM should still be able to locate the app based on the path given. Alternatively, I've built a helper macro that can determine the bundle id for you.

Once you have added your editor, be sure to [submit a pull request](https://github.com/chauncey-garrett/keyboard-maestro-quickcursorkm/pulls) so that others may use it as well!

## Installation

All that's required for installation is to download `quickcursor-km.kmmacros` on the [releases](https://github.com/chauncey-garrett/keyboard-maestro-quickcursorkm/releases) page. Then open the file by double-clicking it.

## Final Words

For users of Keyboard Maestro, QuickCursorKM is an excellent QuickCursor alternative. I hope you enjoy using it!

As always, if you come across any bugs or have suggestions, feel free to [open an issue](https://github.com/chauncey-garrett/keyboard-maestro-quickcursorkm/issues). The latest release of QuickCursorKM can be found on the [releases page](https://github.com/chauncey-garrett/keyboard-maestro-quickcursorkm/releases).

This macro set was originally released on [chauncey.io](http://chauncey.io/blog/2014/09/10/a-quickcursor-redux-via-keyboard-maestro).

## Author

*The author of this module should be contacted via the [issue tracker](https://github.com/chauncey-garrett/keyboard-maestro-quickcursorkm/issues).*

| [![](http://www.gravatar.com/avatar/81e1334c20c8dc25dbf3fee88dc1879c.jpg?s=150&r=g)](http://chauncey.io) |
| :------------------------------------------------------------------------------------------------------: |
| [Chauncey Garrett](http://chauncey.io) - [@chauncey_io](http://twitter.com/chauncey_io)                  |

## Contributions

If you've found this project useful, would you consider sending your support?

- [Contribute Feedback](https://github.com/chauncey-garrett/keyboard-maestro-quickcursorkm/issues) or a [Pull Request](https://github.com/chauncey-garrett/keyboard-maestro-quickcursorkm/pulls)
- [Provide Support](http://chauncey.io/donate/)
- [Give Bitcoin](https://www.coinbase.com/ChaunceyGarrett)

[^macro-sets]: I make many of my macros sets in this manner and have found it useful in terms of managing those macros.

[^recommendation]: I recommend using the same shortcut for all of them, as I have done. In doing so you will get a useful palette from Keyboard Maestro.

[^default-editor]: The `EditAnywhere` macro will open the text in the system default editor for txt files.

[^keyboard-maestro]:  This [referral link](http://www.stairways.com/action/kmdiscount?REF4PDX) for Keyboard Maestro will save you 20%!

[^vim-list-edit]: From the beginning of the list, that's `ctrl-v`, `}`, `(`, `I`, `-`, `⎋`
