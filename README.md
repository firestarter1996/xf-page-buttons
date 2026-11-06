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
* Works in private chats, groups, channels and forum topics.

## Swap buttons position

Off by default. On moves the whole button column to the left edge and mirrors the chat: your messages on the left, everyone else on the right, sender pictures on the right edge.

Sender pictures move with the mirror: in groups they sit on the right edge, beside the other person's bubble, exactly where stock puts them on the left.

Since 1.3.2 no button ever covers a bubble (1.3.3 widens the gap a little more for photo albums). Bubbles that stock gives the full width (your own, and everyone's in private chats) are narrowed by the same 52 dp stock takes from group bubbles for the sender picture, and every bubble starts to the right of the button column and ends before the right edge or the sender pictures. With the switch off nothing changes.

## Install

1. Use the plugin build of Nagram XF and turn on the plugin engine (Settings, N Settings, Plugins).
2. Download `page_buttons.plugin` from the latest release.
3. Send it to your Saved Messages, tap it and choose install. You can also use the plus button on the Plugins screen.
4. Make sure Page Up Down is switched on. Reopen a chat after changing a setting.

## How it works

The plugin hooks `ChatActivity.createView` and `onResume` and adds its buttons to the chat's `sideControlsButtonsLayout`, and hooks `checkButtonsPositionsAndVisibility` to keep them stacked in fixed places. A page tap scrolls by the visible message area minus the bars and an overlap. Swap mode moves each message cell once in `ChatMessageCell.onLayout` and narrows full width bubbles in `MessageObject.getMaxMessageTextWidth`, so nothing extra runs while drawing or scrolling. Logcat tag `PageButtons`.

## Tested

Nagram XF 12.10.1 plugin build on a Pixel 6 Pro running the same build and settings as my daily phone, in a busy forum topic with long bot replies and long messages of my own. With swap on, the buttons end about 50 dp from the left edge and every bubble, mine and the bot's, starts past them. In a busy group the sender pictures sat on the right edge next to their bubbles. With swap off the chat looks exactly like stock.

## License

MIT

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=firestarter1996/xf-page-buttons&type=Date)](https://star-history.com/#firestarter1996/xf-page-buttons&Date)
