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
* Works in private chats, groups, channels and forum topics.

## Swap buttons position

Off by default. On moves the whole button column to the left edge and mirrors the chat: your messages on the left, everyone else on the right, sender pictures on the right edge. Bubble tails flip too: everyone else's point right at their picture, yours point left, the way stock Telegram looks with the sides reversed.

No button ever covers a message. Every bubble, yours and everyone else's, with or without a picture, albums and stickers included, starts to the right of the button column. Service messages and dates center in the space beside the buttons. With the switch off nothing changes.

A switch side button sits above the top button. One tap flips the column between right and left: the setting is saved and the open chat is laid out once on the new side.

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
