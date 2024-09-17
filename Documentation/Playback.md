# Playback

## Table of Contents

* [Introduction](#introduction)
* [Hotkeys](#hotkeys)
* [Controls Toolbar](#controls-toolbar)
* [Context Sensitive Hotkeys](#context-sensitive-hotkeys)
* [Playback Options](#playback-options)
* [AI-Enhanced Playback](#ai-enhanced-playback)

## Introduction

To activate the Playback Hotkeys you have to press the Play Button (unless the *Always Active* option is on, which will activate all hotkeys when the program window is not active). **Playback will not start immediately after pressing the Play Button, it will start when you press one of the Active Hotkeys**. This behavior is intended to allow the user to select the desired starting window/control/mouse position before start playing.  
You can also activate Playback Hotkeys by double-clicking the TrayIcon or right-clicking on it and selecting *Play*.  
Unchecked rows will be ignored during playback.
The *Play Current Macro* button will run the active Macro immediately without activating Hotkeys.

## Hotkeys

Hotkeys are sometimes referred to as shortcut keys and are used to run/play the macros. Playback Hotkeys are set in the hotkey toolbars in the main window or in the *Edit Macros* window (Ctrl+Shift+M).

Use `Backspace` to clear the hotkeys. Press it twice to set `Backspace` as the hotkey.

### Play

Selects the Play Hotkey to execute the currently selected Macro.  
You can make combinations with modifiers such as `Ctrl + X`.

**Note**: If you want to use a hotkey that's not supported by this control, you can go to *Edit Macros* window (Ctrl+Shift+M) and enter a valid hotkey manually. In there you can use any supported AHK hotkey, including mouse buttons and hotstrings.

**Hotstrings**: [Hotstrings](https://www.autohotkey.com/docs/Hotstrings.htm) may be configured to be used for playback in the *Edit Macros* window (Ctrl+Shift+M). To define a hotstring, the triggering abbreviation must start pairs of colons as in this example:

> ::btw

The `X` option is necessary and will be inserted automatically if not present, so the resulting hotstring would be `:X:btw` in this case. You can add other [options](https://www.autohotkey.com/docs/Hotstrings.htm#Options) between the colons.

**Windows Key**: To make combination with the Windows key, check the option *Add the Windows key to "Play" hotkey* in the Options menu or in the Options toolbar.

**Joystick Buttons**: To use a Joystick button as the Play Hotkey, check the option *Use a joystick button as hotkey* in the Options menu or in the Options toolbar.

### Manual

Selects the Manual Hotkey to execute the currently selected Macro step-by-step. This is usually used to debug the Macro. If Show Info option is on a tooltip show the last and next steps will be shown next to the mouse pointer. This hotkey cannot be a combination with modifiers.

### Stop

Selects the Hotkey to stop execution and return it to start. You can also stop Playback by double-clicking the TrayIcon or right-clicking on it and selecting *Stop*. You can make combinations with modifiers such as `Ctrl + X`.

### Pause

Selects the Hotkey to pause execution. Press the hotkey again to resume playback. You can also pause/unpause Playback by Middle-Clicking the TrayIcon. You can make combinations with modifiers such as `Ctrl + X`.

## Controls Toolbar

This small window allows you to control Playback and Recording using an interface in addition to the Hotkeys. It will be displayed when the *Playback* or *Record* button is pressed and the *Show Controls* option is checked or you can open it manually from the Macro Menu, Tray Menu and pressing Ctrl+B on the main window.

### Multiple Macros

Macro Creator supports multiple Macros / Hotkeys. Each Macro will have its own Auto and Manual Hotkey that are shown when you add/select a Macro tab.

When you press the Play Button (or when the main window is not active if "Always Active" option is on) all valid Hotkeys will be activated for all non-empty Macros. A traytip will be displayed (if *Show Info* is on) showing how many Play Hotkeys were activated. If any duplicate is found NO Hotkey will be activated.

### Debugging Macros

In addition to the Manual Hotkey you can select one of these options from the Macro menu:

### Play From Selected Row

If checked Playback will run each Macro from the first selected row in its list. Valid for all Playback commands.

### Play Until Selected Row

If checked Playback will stop each Macro when the first selected row in its list is reached. Valid for all Playback commands.

### Play Selected Rows

If checked Playback will only execute selected rows in each Macro. Valid for all Playback commands.

You can also view the list of variables and contents from the File menu and Tray Icon menu.

## Context Sensitive Hotkeys

Global option will makes all Hotkeys context-sensitive. It can also be set individually for each macro in the *Edit Macros* window. Macro context takes precedence.

Such hotkeys will only work depending on the type of window that is active or exists, or if an [expression](Variables.html#expressions) is evaluated to true.

Select the type of condition and enter the identification of the window, or use the "Get Window" button to retrieve it.

For the *#If Expression* option you can provide any valid [expression](Variables.html#expressions).

> #If MyVar ; Hotkeys will only work when MyVar evaluates to True
> #If GetKeyState("ScrollLock", "T") ; Hotkeys will only work when the ScrollLock key is on
> #If Var1 = "A" || Var1 = "B"

For an expression to be `true` it must be a number other than 0 or a non-empty string.

You can also use [User-defined functions](Functions.html#user-defined-functions) with the *#If Expression* option.

Global option affects ALL Play Hotkeys.

Both Global and Macro options are saved to the project file (.pmc).

There's a text tip at the bottom-left of the main window to show if it's active globally or for the current macro. To deactivate this option select *None* in the list.

For more information see AutoHotkey documentation: [#IfWinActive](https://www.autohotkey.com/docs/commands/_IfWinActive.htm) and [#If](https://www.autohotkey.com/docs/commands/_If.htm).

## Playback Options

To change options click the Options button on the main window or select Options Menu > Settings. Some of the options can also be accessible from the *Playback Options* button on the [Controls Toolbar](#controls-toolbar).

### Title Match Mode

Sets the matching behavior of the WinTitle parameter in commands such as WinWait.

**1**: A window's title must start with the specified WinTitle to be a match.  
**2**: A window's title can contain WinTitle anywhere inside it to be a match.  
**3**: A window's title must exactly match WinTitle to be a match.  
**RegEx**: Changes WinTitle, WinText, ExcludeTitle, and ExcludeText to be regular expressions. Do not enclose such expressions in quotes when using them with commands. For example: WinActivate Untitled.*Notepad. RegEx also applies to ahk_class.

**Fast**: This is the default behavior. Performance may be substantially better than Slow, but certain WinText elements for some types of windows may not be "seen" by the various window commands.  
**Slow**: Can be much slower, but all possible WinText is retrieved from every window as a windowing command searches through them for a match. Window Spy reveals which parts of a Window's text (if any) require the slow mode.

For more information see [AutoHotkey documentation](https://www.autohotkey.com/docs/commands/SetTitleMatchMode.htm).

### Detect Hidden Windows

Determines whether invisible windows are "seen" by the program.

For more information see [AutoHotkey documentation](https://www.autohotkey.com/docs/commands/DetectHiddenWindows.htm).

### Detect Hidden Text

Determines whether invisible text in a window is "seen" for the purpose of finding the window. This affects commands such as IfWinExist and WinActivate.

For more information see [AutoHotkey documentation](https://www.autohotkey.com/docs/commands/DetectHiddenText.htm).

### Key send mode

Sets the default method for Keyboard and Mouse actions. You can change this mid-run using the `SendMode` command available in the [Run command window](Commands/Run.html) (this will not change the default setting).

For more information see [AutoHotkey documentation](https://www.autohotkey.com/docs/commands/SendMode.htm).

### Key delay

Sets the delay that will occur after each keystroke sent by Send and ControlSend. You can change this mid-run using the `SetKeyDelay` command available in the [Run command window](Commands/Run.html) (this will not change the default setting).

For more information see [AutoHotkey documentation](https://www.autohotkey.com/docs/commands/SetKeyDelay.htm).

### Mouse delay

Sets the delay that will occur after each mouse movement or click. You can change this mid-run using the `SetMouseDelay` command available in the [Run command window](Commands/Run.html) (this will not change the default setting).

For more information see [AutoHotkey documentation](https://www.autohotkey.com/docs/commands/SetMouseDelay.htm).

### Control delay

Sets the delay that will occur after each control-modifying command. You can change this mid-run using the `SetControlDelay` command available in the [Run command window](Commands/Run.html) (this will not change the default setting).

For more information see [AutoHotkey documentation](https://www.autohotkey.com/docs/commands/SetControlDelay.htm).

### Playback Speed Hotkeys

**Speed Up**: Selects the hotkey to toggle playback speed Up/Normal. When this function is activated, delay values will be cut by value set. Does not work when *Random Sleeps* is activated.

**Slow Down**: Selects the hotkey to toggle playback speed Down/Normal. When this function is activated, delay values will be multiplied by value set. Does not work when *Random Sleeps* is activated.

### Display balloon tips

Enables displaying of tooltips and traytips during Recording/Playback.

### Do not display errors

Hides error messages from commands, assignments, functions and expressions.

### Return Mouse after playback

If checked will return the mouse to the initial position after each Macro Playback that uses mouse movement. This will not work for Manual Playback.

### Auto Hide Controls Toolbar

If checked the Controls Toolbar will be automatically shown when a Playback hotkey is pressed and hidden when execution finishes.

### Random Sleeps

If checked all delays during playback will be a random value of more or less of the defined percentage, e.g.: if percentage is set to 50, a command with a delay of 300ms will be set to any value between 150ms and 450ms. Percentage can be set in the counter.

## AI-Enhanced Playback

Pulover's Macro Creator now includes AI-enhanced playback features to make your macros more robust, adaptive, and efficient.

### Adaptive Action Execution

During playback, each action is now adapted based on the current screen content. This makes macros more resilient to UI changes in target applications. The AI analyzes the screen and adjusts mouse coordinates or identifies alternative UI elements if the original targets have moved or changed.

### Intelligent Error Handling

The playback system now includes intelligent error handling for unknown or complex actions. If an action cannot be executed as originally recorded, the AI will attempt to interpret the intended outcome and suggest alternative execution steps.

### Dynamic Delay Calculation

Delays between actions are now dynamically calculated based on system performance and AI recommendations. This ensures that macros run smoothly on different systems and adapt to varying load conditions.

### Adaptive Playback Speed

The overall playback speed is periodically adjusted based on system performance to ensure smooth execution. If the system is under heavy load, the playback might slow down slightly to maintain accuracy. Conversely, on high-performance systems, playback might speed up for efficiency.

### Using AI-Enhanced Playback

To enable AI-enhanced playback:

1. Go to Options > Settings > Playback
2. Check the "Enable AI-Enhanced Playback" option
3. Click "Apply" and "OK"

When this option is enabled, you'll see an "AI" indicator in the status bar during playback, confirming that the AI enhancements are active.

### Customizing AI Behavior

Advanced users can fine-tune the AI behavior:

1. Go to Options > Settings > Playback > AI Settings
2. Adjust the following parameters:
   - Adaptation Sensitivity: Controls how aggressively the AI adapts to screen changes
   - Error Handling Strictness: Determines how the AI handles unknown actions
   - Delay Adjustment Range: Sets the minimum and maximum delays the AI can apply
   - Speed Adjustment Frequency: Defines how often the playback speed is recalculated

### Limitations

While AI-enhanced playback significantly improves macro reliability, please note:

- It may slightly increase CPU usage during playback
- For extremely time-sensitive operations, you might need to disable some AI features
- The AI requires an initial learning period to optimize its performance for your specific system and macros

### Feedback and Improvement

The AI-enhanced playback system continuously learns from your usage. You can help improve it by:

1. Enabling anonymous usage data collection in Options > Settings > Privacy
2. Reporting any issues or unexpected behaviors through Help > Report Issue

Your feedback helps us refine the AI algorithms and improve the playback experience for all users.

