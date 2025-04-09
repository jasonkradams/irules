# Hangman

This was sourced from the DevCentral Article: [Hangman game (Optimized for v11.x)](https://community.f5.com/kb/codeshare/hangman-game-optimized-for-v11-x/284299). Unfortunately, that version has become mangled over time with our various DevCentral platform migrations.

This code should live on, so here we go.

## Setup

1. Create the iRule:
    > **Web UI** -> **Local Traffic** -> **iRules** -> **iRule List**
2. Create the External Data Group as a Text File on your desktop.
3. Import the External Data Group to the LTM
    > **Web UI** -> **System** -> **File Management** -> **Data Group File List** -> **Import**
    * **Name** is arbitrary.
    * File Contents = **String**
    * Data Group Name = **Hangmanwords**
4. Play!

## Word Lists for Hangman

You're welcome to use [Hangmanwords.datagroup.txt](./Hangmanwords.datagroup.txt), which was generated with this command:

```sh
grep -E '^[a-z]{4,10}$' /usr/share/dict/words | sort -u | xargs printf "%s,\n" > ~/code/github/irules/hangman/Hangmanwords.datagroup.txt
```

Here are some other sources for word lists you can use in your Hangman game. These range from basic dictionaries to themed or difficulty-based lists.

### 📚 General Word Lists

* **[dwyl/english-words](https://github.com/dwyl/english-words)**
  * 📄 [`words.txt`](https://github.com/dwyl/english-words/blob/master/words.txt) — ~370,000 English words.
  * Suitable for full dictionaries, or you can filter by word length or difficulty.

* **[first20hours/google-10000-english](https://github.com/first20hours/google-10000-english)**
  * 📄 [`20k.txt`](https://github.com/first20hours/google-10000-english/blob/master/20k.txt) — Common English words ranked by frequency.
  * Great for beginner or casual play.

### 🧪 System Dictionaries (macOS / Linux)

* Most UNIX-like systems have a built-in dictionary at:

  ```bash
  /usr/share/dict/words
  ```

  You can filter it for game-friendly word lengths:

  ```bash
  grep -E '^[a-z]{4,8}$' /usr/share/dict/words | sort -u
  ```

### 🎯 Themed or Custom Word Lists

* **[SCOWL (Spell Checker Oriented Word Lists)](http://wordlist.aspell.net)**
  * Create custom lists based on difficulty and word type.
  * Use the [Aspell Word List Builder](http://app.aspell.net/create) for more control.

* **[Wordlists.io](https://wordlists.assetnote.io/)** — Browse themed lists like animals, foods, places, and more.
* **[WordNet](https://wordnet.princeton.edu/)** — A lexical database of English (academic, powerful, but requires parsing).
