# 💬⬆️⬇️ Page Up Down

A plugin for Nagram XF. Two round buttons in every chat move the messages exactly one screen up or down per tap.

## Why I made it

Long bot replies fill my chats. Flinging overshoots, and the stock button only jumps all the way to the bottom. I wanted to read a long thread one screen at a time.

## What it changes

* A page up button and a page down button sit in the chat's side button column, above the stock scroll to bottom button, in the same round style.
* Each tap moves the messages one screen, minus a small overlap so the line you were reading stays in view.
* Page up shows only when there are older messages above. Page down shows only when there are newer messages below. They fade in and out like the stock buttons and move out of their way.
* Works in private chats, groups, channels and forum topics.

Setting: the buttons can be switched off. Reopen a chat after changing it.

## Install

1. Use the plugin build of Nagram XF and turn on the plugin engine (Settings, N Settings, Plugins).
2. Download `page_buttons.plugin` from the latest release.
3. Send it to your Saved Messages, tap it and choose install. You can also use the plus button on the Plugins screen.
4. Make sure Page Up Down is switched on.

## How it works

The plugin hooks `ChatActivity.createView` and `onResume` and adds two `ChatActivityBlurredRoundPageDownButton` buttons to the chat's `sideControlsButtonsLayout`. It hooks `checkButtonsPositionsAndVisibility` to stack them above whatever stock buttons are showing, and the chat list's scroll listener to show each button only when `canScrollVertically` says that direction can move. A tap calls `smoothScrollBy` with the visible message area minus the top bar, the bottom bar and a 96 dp overlap. Every page move goes to logcat under the tag `PageButtons`.

## Tested

Nagram XF 12.10.1 plugin build, plugin SDK 1.4.6.7, on a Pixel 6 Pro running the same build and settings as my daily phone, in a forum topic holding 41 long bot replies.

* At the bottom only page up showed. One tap moved the view from replies 39 and 40 to replies 36 through 38, and page down appeared.
* One tap on page down brought the view back to the exact same spot, and page down hid again.
* Fifteen taps on page up reached the first message of the topic, and page up hid there.

## License

MIT

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=firestarter1996/xf-page-buttons&type=Date)](https://star-history.com/#firestarter1996/xf-page-buttons&Date)
