---
layout: post
date: 2020-02-10
title: tmux
tags:
  - Security
  - Cloud
  - Try Hack Me
  - Beginner
publish: true
---

This is my documentation on how to use tmux which is a tool that allows users to run multiple tasks within a single window.

# Knowledge

Similar to the previous blog post, this is an addon to the Linux command-line (Bash). [Ubuntu](https://ubuntu.com/#download) and [Kali Tool](https://www.kali.org/downloads/) are recommended for this challenge.

[tmux Commands](https://i.imgur.com/bL9Dn3U.png)

# Walkthrough

### Task 1 <br/>

Firstly, you must install tmux into your linux system. This could be done through using the following command:

```
  sudo apt-get install tmux
```

You will be asked your password in order to continue the installation.

### Task 2 <br/>

After installation, you are now able to use tmux. When using the following command:

```
  tmux
```

It will open the tmux software, which is essentially another terminal but more available functions such as multitasking.

### Task 3 <br/>

All tmux commands start with two keyboard combinations. The first keyboard combination key is:

```
  Control
```

### Task 4 <br/>

The second keyboard combination key is:

```
  B
```

### Task 5 <br/>

To detach a session, firstly you press the two combination keys of "Control + B", follow by the key:

```
  D
```

What detaching does is similar in creating new windows in a internet browser. This would create multiple sessions and can be used later by "tabbing" through using "Control + B" followed by either the '(' or ')' key. Make sure to use the shift key.

### Task 6 <br/>

To list all your windows or sessions, you use the command:

```
  tmux ls
```

### Task 7 <br/>

By default; without setting the session name, the names will begin from:

```
  0
```

The numbers will increase as more sessions are created.

### Task 8 <br/>

To choose the session that you just created, you use the command:

```
  tmux a -t 0
```

If you want to use a specific session, replace the "0" in the above command with the name of your session that is listed with the "tmux ls" command.

### Task 9 <br/>

To create a new window within a session, firstly you press the two combination keys of "Control + B", follow by the key:

```
  C
```

Creating a new window within a session is essentially creating a "tab" within an internet browser. You are able to "tabbing" through using "Control + B" followed by either the 'N' or 'P' or '0-9' keys.

### Task 10 <br/>

Does not exist.

### Task 11 <br/>

Does not exist.

### Task 12 <br/>

When your tmux terminal is filled, you should use "Copy Mode" in order to scroll up and down. Firstly you press the two combination keys of "Control + B" followed by the key:

```
  [
```

### Task 13 <br/>

As of February 2020, the key does not go to the very top.

```
  g
```

### Task 14 <br/>

As of February 2020, the key does not go to the very bottom.

```
  G
```

### Task 15 <br/>

To quit "Copy Mode" you use the key:

```
  q
```

### Task 16 <br/>

To split windows vertically, you press "Control + B" followed by the key:

```
  %
```

### Task 17 <br/>

To split windows horizontally, you press "Control + B" followed by the key:

```
  "
```

### Task 18 <br/>

Does not exist.

### Task 19 <br/>

Does not exist.

### Task 20 <br/>

Does not exist.

### Task 21 <br/>

To remove a pane, you press "Control + B" followed by the key:

```
  X
```

### Task 22 <br/>

To close the tmux session, it can be done by typing within the command-line:

```
  exit
```

### Task 23 <br/>

To create new sessions with a name of "neat" you type within the command-line:

```
tmux new -s neat
```

# Conclusion

In short; to cut down all the learning, I believe that the most useful commands would be:

- tmux:
  - To initiate it within the Linux command-line.
- CTRL + B + \[RELEASE] + %:
  - Split the window vertically.
- CTRL + B + \[RELEASE] + &:
  - Split the window horizontally.
- CTRL + B + \[RELEASE] + (ARROW KEYS):
  - Swap between panels.
- CTRL + B + \[RELEASE] + C:
  - Create new tab.
- CTRL + B + \[RELEASE] + N/P:
  - Move to next/previous tab.
- exit:
  - To close a tmux window or exit out of tmux.

After learning this add-on within the Linux command-line, it has increased my productivity as I can monitor multiple tasks within one window. It is most definitely faster than "Alt-Tabbing" and it is quick to learn.
