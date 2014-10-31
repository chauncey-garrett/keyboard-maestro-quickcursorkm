# QuickCursorKM

## Inspiration and Rationale

Inspiration for [QuickCursorKM][1] comes from the deprecated [QuickCursor][2] and [tjluoma's][3] replacement, [edit-anywhere][4]. Thank you tjluoma for the inspiration for this macro set!

If you do a lot of writing, text is something that often flows easily. However, there are those moments when it just. Gets. Stuck. QuickCursorKM is there to undo that log-jam by redirecting your text-flow to a better editor. A good example: Say you've made a list of things but forgot to add a hyphen (-) for Markdown formatting. No worries! Activate QuickCursorKM, edit the text in MacVim[^vim-list-edit], and you're on your way.

<!--more-->

## Creation and Extensibility
This [Keyboard Maestro][5][^keyboard maestro] macro set is broken up into two kinds of macros: builder macros with specific, iterative actions (indicated by an underscore and disabled by default) and editor macros that set or determine the editor you wish to use. I utilize the builder macros to piece-together the final editor macro that will be used by the end user (you). Built this way, the macro-program is easily extensible and updated.[^macro-sets]

You, however, need do nothing but choose a shortcut for the editor macros you wish to use.[^recommendation] You may also wish to disable any of the editor-specific macros that you don't have installed or don't use. Alternatively, you can just use the QuickCursorKM macro itself and it will open the text in the system default editor for txt files.

Additionally, in the macro `QuickCursorKM`, you may assign your favorite editor to open while selecting text from a specific application. For example, I may want to use Byword for Safari forms but edit a list I started in Pages with MacVim. **To my knowledge, no other QuickCursor-like replacement does this!** See the default macro for examples of how to add additional editor assignments.

## Usage

To use QuickCursorKM, place your cursor on some text: if you select specific text, that text will be edited; if no text is selected, all available text will be edited. Run the macro `QuickCursorKM` (or one of the editor-specific variants[^default-editor]) with your hotkey. The text will open in your editor. Make your edits, and then once you are finished, quit the editor with ⌘Q (don't worry; as explained below, your text is safe). The edited text will be returned to the source application. That's all there is to it!

![][6]

If for some reason the macro fails, your work has been safely saved from the beginning in one of two locations: `~/.quickcursor_km.txt` or in the Trash can with the date appended to the filename. You should also receive an error message that can be useful in debugging.

## Adding New Text Editors

If the text editor of your choice is not listed, it is easy to add it because of the modular nature of QuickCursorKM. To add your editor, simply duplicate any of the editor-specific macros and replace the path and the bundle-id variables with the analogous text for your app. If you do not know the bundle-id of your editor, you may leave the variable blank: QuickCursorKM should still be able to locate the app based on the path given. Alternatively, I've built a helper macro that can determine the bundle id for you. Once you've added your editor, be sure to [submit a pull request][7] so that others may use it as well!

## Final Words

If you'd like to preview the macros, you can do so [here][8].

As always, if you come across any bugs or have suggestions, feel free to [open an issue][9]. The latest release of QuickCursorKM can always be found [here][10].

This macro set was originally released on [chauncey.io][11].

## Author(s)

*The author(s) of this module should be contacted via the [issue tracker][12].*

  - [Chauncey Garrett][13]

[![][14]](http://chauncey.io/about/index.html#donate)

[^macro-sets]: I make many of my macros sets in this manner and have found it useful in terms of managing those macros.

[^recommendation]: I recommend using the same shortcut for all of them, as I have done. In doing so you will get a useful palette from Keyboard Maestro.

[^default-editor]: The `EditAnywhere` macro will open the text in the system default editor for txt files.

[^keyboard maestro]:  This [referral link][15] for Keyboard Maestro will save you 20%!

[^vim-list-edit]: From the beginning of the list, that's `ctrl-v`, `}`, `(`, `I`, ` - `, `⎋`


[1]: https://github.com/chauncey-garrett/keyboard-maestro-quickcursorkm
[2]: https://www.youtube.com/watch?v=-bHwcyHrRGs
[3]: https://github.com/tjluoma
[4]: https://github.com/tjluoma/edit-anywhere
[5]: http://http://www.keyboardmaestro.com
[6]: /img/quickcursor-km-palette.png
[7]: https://github.com/chauncey-garrett/keyboard-maestro-quickcursorkm/pulls
[8]: macros/macros.md
[9]: https://github.com/chauncey-garrett/keyboard-maestro-quickcursorkm/issues
[10]: https://github.com/chauncey-garrett/keyboard-maestro-quickcursorkm/releases
[11]: http://chauncey.io/blog/2014/09/10/a-quickcursor-redux-via-keyboard-maestro
[12]: https://github.com/tjluoma
[13]: https://github.com/tjluoma/edit-anywhere
[14]: /img/donate.png
[15]: http://www.stairways.com/action/kmdiscount?REF4PDX
