# Sublime Lines - Multisets

[![Build Status](https://travis-ci.org/evandroforks/LinesMultisets.svg?branch=master)](https://travis-ci.org/evandroforks/LinesMultisets)
[![Build status](https://ci.appveyor.com/api/projects/status/github/evandroforks/LinesMultisets?branch=master&svg=true)](https://ci.appveyor.com/project/evandroforks/LinesMultisets/branch/master)
[![codecov](https://codecov.io/gh/evandroforks/LinesMultisets/branch/master/graph/badge.svg)](https://codecov.io/gh/evandroforks/LinesMultisets)
[![Coverage Status](https://coveralls.io/repos/github/evandroforks/LinesMultisets/badge.svg?branch=master)](https://coveralls.io/github/evandroforks/LinesMultisets?branch=master)
[![Latest Release](https://img.shields.io/github/tag/evandroforks/LinesMultisets.svg?label=version)](https://github.com/evandroforks/LinesMultisets/releases)
<a href="https://packagecontrol.io/packages/LinesMultisets"><img src="https://packagecontrol.herokuapp.com/downloads/LinesMultisets.svg"></a>

This Sublime Text plugin allows you to compare, merge and manipulate lists of things,
whether they are todo items, lists of files or arrays from API responses:
![Demo - comparing a giveaway list with two wishlists](https://github.com/heldev/sublime-lines-multisets/raw/master/demo-giveaway-list.gif)


## Installation

### By Package Control

1. Download & Install **`Sublime Text 3`** (https://www.sublimetext.com/3)
1. Go to the menu **`Tools -> Install Package Control`**, then,
   wait few seconds until the installation finishes up
1. Now,
   Go to the menu **`Preferences -> Package Control`**
1. Type **`Add Channel`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
   input the following address and press <kbd>Enter</kbd>
   ```
   https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json
   ```
1. Go to the menu **`Tools -> Command Palette...
   (Ctrl+Shift+P)`**
1. Type **`Preferences:
   Package Control Settings – User`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
   find the following setting on your **`Package Control.sublime-settings`** file:
   ```js
       "channels":
       [
           "https://packagecontrol.io/channel_v3.json",
           "https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json",
       ],
   ```
1. And,
   change it to the following, i.e.,
   put the **`https://raw.githubusercontent...`** line as first:
   ```js
       "channels":
       [
           "https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json",
           "https://packagecontrol.io/channel_v3.json",
       ],
   ```
   * The **`https://raw.githubusercontent...`** line must to be added before the **`https://packagecontrol.io...`** one, otherwise,
     you will not install this forked version of the package,
     but the original available on the Package Control default channel **`https://packagecontrol.io...`**
1. Now,
   go to the menu **`Preferences -> Package Control`**
1. Type **`Install Package`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
search for **`LinesMultisets`** and press <kbd>Enter</kbd>

See also:

1. [ITE - Integrated Toolset Environment](https://github.com/evandrocoan/ITE)
1. [Package control docs](https://packagecontrol.io/docs/usage) for details.


## How to use
Switch to a file with a list you want to modify and select an operation to perform from the Command Palette
(or using `Edit -> Lines - Multisets` menu).
## Operations
### Add
The result is all items from both lists. Example:

List 1 | List 2
-------|-------
one | two
three | three
four | four
four |

Result: one, two, three, three, four, four, four

### [Union](https://en.wikipedia.org/wiki/Set_(mathematics)#Unions)
The result is items from both lists, but only one item for every match. Example:

List 1 | List 2 | Match
-------|--------|------
one | two |
three | three | :heavy_check_mark:
four | four | :heavy_check_mark:
four |  |

Result: one, two, three, four, four

### [Intersection](https://en.wikipedia.org/wiki/Set_(mathematics)#Intersections)
The result is only items that exist in both lists. Example:

List 1 | List 2 | Match | Result
-------|--------|-------|-------
one | two | |
three | three | :heavy_check_mark: | three
four | four | :heavy_check_mark: | four
four | five | |
five | five | :heavy_check_mark: | five
five | five | :heavy_check_mark: | five

### [Difference](https://en.wikipedia.org/wiki/Complement_(set_theory))
The result is items from list 1 that don't have a match in list 2. Example:

List 1 | List 2 | Match | Result
-------|--------|-------|-------
one | two | | one
three | three | :heavy_check_mark: |
four | four | :heavy_check_mark: |
four | five | | four
five | five | :heavy_check_mark: |
five | five | :heavy_check_mark: |

### [Symmetric difference](https://en.wikipedia.org/wiki/Symmetric_difference)
The result is items that exist in only one of the lists. Example:

List 1 | List 2 | Match
-------|--------|------
one | two |
three | three | :heavy_check_mark:
four | four | :heavy_check_mark:
four | five |
five | five | :heavy_check_mark:
five | five | :heavy_check_mark:

Result: one, two, four, five
