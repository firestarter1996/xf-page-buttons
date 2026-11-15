# 💬⬆️⬇️ Page Up Down

A plugin for Nagram XF. Round buttons in every chat move the messages exactly one screen up or down per tap, jump to the first message, and can sit on either side of the chat.

## Why I made it

Long bot replies fill my chats. Flinging overshoots, and the stock button only jumps all the way to the bottom. I wanted to read a long thread one screen at a time.

## What it changes

* Page up and page down buttons sit in the chat's side button column, above the stock scroll to bottom button, in the same round style.
* Each tap moves the messages one screen, minus a small overlap so the line you were reading stays in view. Hold a button to keep paging.
* A top button jumps straight to the first message of the chat or topic. Hold it to pick a date.
* The stock end button gets an arrow with a line under it and always goes to the very bottom of the newest message.
* All four buttons stay in fixed places. Mention and reaction buttons stack above them.
* The round share arrow next to messages is hidden (a setting, on by default).
* Hold the switch side button to hide all the buttons until the topic or chat is opened again (a short tick, no popup).
* Easy to see in the sun: white arrows, a white ring with a thin dark edge around every button, and a fill in your theme's accent blue while a button is pressed.
* Every tap on top, page up, page down, end and switch side, and every tap on a topic tab, gives one very short haptic tick, the same key press tick Gboard uses by default. It follows the system touch feedback setting and Nagram's Disable vibration switch.
* Page up is inverted: a pure white circle with a black ring and a black arrow, the same contrast turned around, so the button used most is the easiest one to find.
* Height on screen is a slider that moves the whole button column up or down, from the bottom edge up to 50% of the screen, with Lowest, Low, Middle and High presets. The default is 23%.
* Send a message while you are scrolled up and the chat stays where you were reading. Jump to bottom after sending is a setting, off by default; at the bottom the chat follows your message as usual.
* Space between buttons and Button size are sliders right on the settings page, each with preset buttons under it (Tight, Roomy, Wide, Widest; Small, Normal, Large, Largest), so a thumb does not land on the wrong button.
* Works in private chats, groups, channels and forum topics.

## Swap buttons position

Off by default. On moves the whole button column to the left edge and mirrors the chat: your messages on the left, everyone else on the right, sender pictures on the right edge. Bubble tails flip too: everyone else's point right at their picture, yours point left, the way stock Telegram looks with the sides reversed.

No button ever covers a message. Every bubble, yours and everyone else's, with or without a picture, albums and stickers included, starts to the right of the button column. Service messages and dates center in the space beside the buttons. With the switch off the buttons stay on the right and the chat keeps its usual sides, with the same free strip beside the buttons: your own messages and everyone else's stop to the left of them.

A switch side button sits above the top button. One tap flips the column between right and left: the setting is saved and the open chat is laid out once on the new side.

## What's new in 1.7.4 (11-14-2026)

Messages stay clear of the buttons on the right side too. With the buttons on the right, your own bubbles sat against the right edge, under the buttons, and rows of buttons under a message ran under them as well.

* Your own bubbles now stop left of the buttons, the mirror image of the left side layout.
* Every text bubble has the same widest width on both sides, so bubbles beside a sender picture, bubbles in private chats and your own all end at the same line.
* A row of buttons under a message is held to the free width.
* The free strip follows the Button size setting.
* The first chat opened after Nagram starts gets the same spacing as every other chat.

## What's new in 1.7.3 (11-14-2026)

Fix for presses that opened the message menu. XF only takes presses for the button column inside a box 300 dp tall at the bottom of the chat. Buttons raised above that box were drawn but could not be pressed, so the press reached the message under them.

* The column now takes presses over the full height of the chat, so a button works wherever it is drawn. Only the buttons take a touch: taps, long presses, scrolling and swipe to reply beside them still reach the messages.
* The buttons take their raised place right after a chat opens, and again after the screen is rotated.
* When the plugin is switched off or reloaded it removes its own buttons and puts the column back, on the screen thread.

## What's new in 1.7.2 (11-14-2026)

Crash fix. With the column raised and the keyboard open, buttons could end up above the message list, and on some phones XF's glass effect then aborted the whole app ("Unable to create layer for glass_down_0").

* The buttons now always stay below the chat header. The plugin measures the room above the column and lowers it until page up fits. A button that still has no room is hidden until there is room again.
* Room is kept for XF's own reactions heart and mentions buttons, so they never sit on top of page up.
* The buttons are placed again whenever XF slides the column (keyboard, message box).
* A guard on XF's own glass rectangles gives any rectangle with no height or width one pixel before XF draws it, whatever caused it.
* Every callback is wrapped, so an error inside the plugin can never reach XF.
* The saved height drops by 2 once (23% becomes 21%, the Middle preset).

## What's new in 1.7.1 (11-14-2026)

The column sits another 5% of the screen higher (23% in all, the Middle preset). A saved height rises by 5 once. The High preset is now 35%.

## What's new in 1.7.0 (11-14-2026)

* New setting, Jump to bottom after sending, off by default. Off: when you send a message while scrolled up, the chat stays where you were reading and your message lands below. On: stock behavior, the chat jumps to your new message. If you are already at the bottom, the chat follows your message either way.
* The column sits another 8% of the screen higher (18% in all, the Middle preset). A saved height rises by 8 once. The Height on screen slider now reaches 50%, and its presets are Lowest (0%), Low (10%), Middle (18%) and High (30%).
* How it works: XF jumps in two places when a message of your own arrives in the open chat, `moveScrollToLastMessage` when the newest messages are loaded and `scrollToLastMessage` when they are not. Both calls are skipped while the setting is off and the list is scrolled up. The hooks run only at that moment, never per frame or per scroll.

## What's new in 1.6.1 (11-14-2026)

The column sits another 5% of the screen higher, and buttons are another 3% bigger, once, from whatever size you had.

Page up is now the exact inverse of the other buttons. They have a glass circle, a 2 dp white ring with a 1 dp dark edge outside it, and a white arrow. Page up has a white circle, a 2 dp black ring in the same place with a 1 dp white edge outside it, and a black arrow. Same size and shape, nothing else changed.

## What's new in 1.6.0 (11-14-2026)

* New Height on screen slider on the settings page, with preset buttons Lowest (0%), Low (5%, the default), Middle (15%) and High (30%). It raises the whole column together: end, page down, page up, top, switch side, and the mention and reaction buttons above them. The buttons keep their order, and Space between buttons still sets the distance from one to the next.
* The column now sits 5% of the screen height higher than before.
* Page up is a white circle with a black arrow. Page down and the other buttons keep white arrows on the glass circle. Pressed, it still fills with the accent blue.
* Buttons are 3% bigger, once, from whatever size you had.
* Turning the plugin off or reloading it puts the stock buttons back where XF had them.
* Nothing new runs while drawing or scrolling: the height is read with the other settings at most twice a second, and the page up look is a drawable set once.

## What's new in 1.5.2 (11-11-2026)

The reactions heart and the mentions button now match the page buttons: the same white ring with a dark edge, white icon, accent blue fill while pressed, and the same size.

## What's new in 1.5.1 (11-11-2026)

Fixed the reactions heart (and the mentions button) sitting far above the buttons: they were lifted twice when XF laid them out more than once. Buttons are also 5% bigger, once, from whatever size you had.

## What's new in 1.5.0 (11-11-2026)

Space between buttons is now a slider (0 to 60 dp between circles) shown right on the plugin's settings page, with the four old steps kept as preset buttons under it: Tight (10 dp), Roomy (18 dp, the default), Wide (26 dp) and Widest (36 dp). A new Button size slider (70% to 160%) has its own presets: Small, Normal, Large and Largest. The stock end button takes the same size, and the distance from one button to the next grows with the size so big buttons never overlap. The preset matching the current value lights up. Your old spacing step carries over. Both values are read at most twice a second, never per frame.

## What's new in 1.4.4 (11-11-2026)

A new setting, Space between buttons, with four steps: Tight (the old spacing, 10 dp between circles), Roomy (18 dp, the new default), Wide (26 dp) and Extra wide (36 dp). The end arrow moves apart from page down by the same amount. The value is read at most twice a second, never per frame. Reopen a chat after changing it.

## What's new in 1.4.3 (11-10-2026)

A very short haptic tick on every tap of the top, page up, page down, end and switch side buttons, and on every tap of a topic tab when you switch topics. It is Android's keyboard key press tick (`HapticFeedbackConstants.KEYBOARD_TAP`), the same feel as Gboard's default, played on the tapped view, so it follows the system touch feedback setting and Nagram's own Disable vibration switch. The tick lives only in the click handlers: nothing new runs while drawing, laying out or scrolling. Holding a page button to keep paging and the long presses work as before.

## What's new in 1.4.2 (11-08-2026)

Fixes Nagram XF force closing right after it opened. The plugin defined its own Runnable and long click classes while it loaded, and Chaquopy points the shared Java class for every Python Runnable at the newest Python class before that class is finished. Another plugin's Runnable that ran in that moment was rebuilt through the unfinished class and the app died with `AttributeError: '_Repeat' object has no attribute '_chaquopyGetDict'`. Every Runnable and long click listener is now the SDK's own, each posted run is kept until it runs and removed on unload, nothing posted can raise into Java, and the hooks are installed on the UI thread.

## Install

1. Use the plugin build of Nagram XF and turn on the plugin engine (Settings, N Settings, Plugins).
2. Download `page_buttons.plugin` from the latest release.
3. Send it to your Saved Messages, tap it and choose install. You can also use the plus button on the Plugins screen.
4. Make sure Page Up Down is switched on. Reopen a chat after changing a setting.

## How it works

The plugin hooks `ChatActivity.createView` and `onResume` and adds its buttons to the chat's `sideControlsButtonsLayout`, and hooks `checkButtonsPositionsAndVisibility` to keep them stacked in fixed places. Taps tick through `performHapticFeedback(KEYBOARD_TAP)` inside each click handler; the stock end button through a hook on `ChatActivity.onSideControlButtonOnClick` and the topic tabs through one on `TopicsTabsView.onTabClick`. A page tap scrolls by the visible message area minus the bars and an overlap. Swap mode moves each message cell once in `ChatMessageCell.onLayout` (and `ChatActionCell.onLayout` for service messages) and narrows full width bubbles in `MessageObject.getMaxMessageTextWidth`, so nothing extra runs while drawing or scrolling. Tails are flipped by mirroring each bubble outline once in `MessageDrawable.generatePath`, which stock caches per cell. The share arrow is hidden by switching on Nagram's own hide share check in memory only. Logcat tag `PageButtons`.

## Tested

Nagram XF 12.10.1 plugin build on a Pixel 6 Pro running the same build and settings as my daily phone, in a busy forum topic with long bot replies and long messages of my own. In a busy group with the buttons on the left, the sender pictures sat on the right edge and every message started right of the buttons. One tap on the switch side button moved everything back to stock, and another tap back again. With swap off the chat looks exactly like stock.

## License

MIT

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=firestarter1996/xf-page-buttons&type=Date)](https://star-history.com/#firestarter1996/xf-page-buttons&Date)
