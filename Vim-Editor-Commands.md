## **Vim Editor Commands Cheat Sheet**

---

### **Basic Modes**

| Command | Description                                                       |
| ------- | ----------------------------------------------------------------- |
| `i`     | Switch to **Insert mode** before the cursor (insert text).        |
| `I`     | Switch to Insert mode at the **beginning of the current line**.   |
| `a`     | Switch to Insert mode **after** the cursor.                       |
| `A`     | Switch to Insert mode at the **end of the current line**.         |
| `o`     | Open a new line **below** the current line and enter Insert mode. |
| `O`     | Open a new line **above** the current line and enter Insert mode. |
| `v`     | Start **Visual mode** (for selecting text).                       |
| `Esc`   | Return to **Normal (Command) mode**.                              |

---

### **File Management**

| Command         | Description                   |
| --------------- | ----------------------------- |
| `:w`            | Save the file (write).        |
| `:q`            | Quit Vim.                     |
| `:q!`           | Quit without saving.          |
| `:wq`           | Save and quit.                |
| `:e <filename>` | Open or create a file in Vim. |

---

### **Cursor Movement**

| Command | Description            |
| ------- | ---------------------- |
| `h`     | Move cursor **left**.  |
| `j`     | Move cursor **down**.  |
| `k`     | Move cursor **up**.    |
| `l`     | Move cursor **right**. |

---

### **Replacing and Changing Text**

| Command     | Description                                                                                       |
| ----------- | ------------------------------------------------------------------------------------------------- |
| `r<char>`   | Replace the character under the cursor with `<char>`.                                             |
| `R`         | Enter **Replace mode** to overwrite multiple characters.                                          |
| `c<motion>` | Change (delete + insert) the text covered by the motion. Example: `cw` changes (replaces) a word. |
| `C`         | Change from the cursor to the **end of the line** (same as `c$`).                                 |

---

### **Word and Line Movement**

| Command | Description                                                    |
| ------- | -------------------------------------------------------------- |
| `w`     | Move to the **start of the next word**.                        |
| `W`     | Move to the **start of the next WORD** (ignores punctuation).  |
| `e`     | Move to the **end of the current word**.                       |
| `E`     | Move to the **end of the current WORD** (ignores punctuation). |
| `0`     | Move to the **start of the current line**.                     |
| `^`     | Move to the **first non-blank character** of the line.         |
| `$`     | Move to the **end of the line**.                               |

---

### **Deleting (Cutting) Text**

| Command     | Description                                                       |
| ----------- | ----------------------------------------------------------------- |
| `x`         | Delete the character **under the cursor**.                        |
| `X`         | Delete the character **before the cursor**.                       |
| `d<motion>` | Delete text defined by a motion (e.g., `dw`, `de`, `d$`).         |
| `D`         | Delete from the cursor to the **end of the line** (same as `d$`). |
| `dw`        | Delete from the cursor to the **start of the next word**.         |
| `de`        | Delete to the **end of the current word**.                        |
| `dd`        | Delete (cut) the **entire current line**.                         |

> **Note**: All deletions are also copies (cuts) to the unnamed register.

---

### **Yanking (Copying) and Pasting**

| Command     | Description                                              |
| ----------- | -------------------------------------------------------- |
| `y<motion>` | Yank (copy) text defined by a motion (e.g., `yw`, `y$`). |
| `yy` or `Y` | Yank the **entire current line**.                        |
| `p`         | Paste **after** the cursor.                              |
| `P`         | Paste **before** the cursor.                             |

---

### **Indentation**

| Command  | Description                                                                      |
| -------- | -------------------------------------------------------------------------------- |
| `==`     | Auto-indent the current line.                                                    |
| `>`, `<` | Shift right or left in visual mode or with motion (e.g., `>>` for current line). |

---

## ✅ **Session 07 – Count Modifiers & Skipping Lines**

| Command         | Description                                                         |
| --------------- | ------------------------------------------------------------------- |
| `:e <filename>` | Open or create a new file named `<filename>`.                       |
| `10h`           | Move cursor **10 characters left**.                                 |
| `10l`           | Move cursor **10 characters right**.                                |
| `d2w`           | Delete **2 words** from the cursor position.                        |
| `d14d`          | Delete **14 lines** from the current line. (Correct form is `14dd`) |
| `c2w`           | Change (replace) **next 2 words**.                                  |
| `gg`            | Move cursor to the **start** of the file.                           |
| `G`             | Move cursor to the **end** of the file.                             |
| `dgg`           | Delete from current line **to the top** of the file.                |
| `dG`            | Delete from current line **to the end** of the file.                |
| `17yy`          | Yank **17 lines** from the current line.                            |
| `yy`            | Yank (copy) the **current line**.                                   |
| `100p`          | Paste the yanked text **100 times**.                                |
| `5o<ESC>`       | Insert **5 new lines** **below** the cursor.                        |
| `5O<ESC>`       | Insert **5 new lines** **above** the cursor.                        |

> **Note**: For commands like `5o`, you'll enter insert mode. Press `Esc` after to return to normal mode.

---

## ✅ **Session 08 – Searching & Replacing**

| Command                   | Description                                                          |
| ------------------------- | -------------------------------------------------------------------- |
| `/pattern`                | Search **forward** for "pattern".                                    |
| `?pattern`                | Search **backward** for "pattern".                                   |
| `n`                       | Move to the **next** search match.                                   |
| `N`                       | Move to the **previous** search match.                               |
| `:nohlsearch`             | Remove search **highlighting**.                                      |
| `:1,45s/bacon/broccoli/g` | Replace all "bacon" with "broccoli" from **line 1 to 45**.           |
| `:%s/word/new/g`          | Replace all occurrences of "word" with "new" in the **entire file**. |

---

## ✅ **Session 09 – Managing Windows and Tabs**

### Splitting Windows:

| Command                 | Description                    |
| ----------------------- | ------------------------------ |
| `:split` or `:sp`       | Split window **horizontally**. |
| `:vsplit` or `:vsp`     | Split window **vertically**.   |
| `CTRL+w s`              | Shortcut for horizontal split. |
| `CTRL+w v`              | Shortcut for vertical split.   |
| `:q`                    | Quit the current window.       |
| `CTRL+w c`              | Close the current window.      |
| `CTRL+w` then `h/j/k/l` | Move between split windows.    |

### Working with Tabs:

| Command               | Description                   |
| --------------------- | ----------------------------- |
| `:tabnew`             | Open a **new tab**.           |
| `:tabclose`           | Close the **current tab**.    |
| `:tabn`               | Move to the **next tab**.     |
| `:tabp`               | Move to the **previous tab**. |
| `:tabedit <filename>` | Open a file in a **new tab**. |

---

## ✅ **Session 10 – Marking Files (Using Marks)**

| Command     | Description                                               |
| ----------- | --------------------------------------------------------- |
| `m<letter>` | **Mark** the current position with a lowercase letter.    |
| `'a`        | Move to the **start of the line** where mark `a` was set. |
| `` `a ``    | Move to the **exact cursor position** of mark `a`.        |
| `'A`        | Move to a mark **in another file** (uppercase marks).     |
| `:marks`    | Show all current marks.                                   |

---

## ✅ **Session 11 – Coding & Syntax Helpers**

| Command | Description                                                      |
| ------- | ---------------------------------------------------------------- |
| `%`     | Jump between **matching brackets**, braces, or parentheses.      |
| `<`     | **Indent left** (decrease indent).                               |
| `>`     | **Indent right** (increase indent).                              |
| `=`     | **Auto-indent** selected lines or blocks.                        |
| `~`     | Toggle **case** (uppercase/lowercase) of character under cursor. |
| `gg=G`  | Properly **indent the entire file**.                             |

---

## ✅ **Session 12 – Editor Settings (Temporary Settings)**

| Command                             | Description                                      |
| ----------------------------------- | ------------------------------------------------ |
| `:set number`                       | Show **line numbers**.                           |
| `:set relativenumber` or `:set rnu` | Show **relative line numbers**.                  |
| `:set autoindent`                   | Enable **automatic indentation**.                |
| `:set noerrorbells`                 | Disable **error bell sounds**.                   |
| `:set colorcolumn=80`               | Draw a vertical guide at column 80.              |
| `:set ruler`                        | Show **cursor position** info in status line.    |
| `:set nohlsearch`                   | Turn off **search highlight**.                   |
| `:set background=dark` or `light`   | Set background color scheme.                     |
| `:set tabstop=4`                    | Set tab width to **4 spaces**.                   |
| `:colorscheme desert`               | Set Vim **theme** to "desert".                   |
| `:set showmode`                     | Show current Vim **mode** (Insert, Visual, etc). |

---

## ✅ **Session 13 – Saving Settings in `.vimrc`**

| Command            | Description                                    |
| ------------------ | ---------------------------------------------- |
| `:e $MYVIMRC`      | Open your personal Vim config file (`.vimrc`). |
| `:source $MYVIMRC` | Reload the config after saving.                |

---

## 🔹 **Extra 1 – Macros**

| Command     | Description                                       |
| ----------- | ------------------------------------------------- |
| `q<letter>` | Start recording a macro into register `<letter>`. |
| `q`         | Stop recording.                                   |
| `@<letter>` | Play macro from register `<letter>`.              |
| `@@`        | Repeat last played macro.                         |
| `10@a`      | Run macro `a` 10 times.                           |

> Example: `qa` → record into `a` → type some commands → `q` → play with `@a`

---

## 🔹 **Extra 2 – Buffers**

| Command             | Description                         |
| ------------------- | ----------------------------------- |
| `:ls` or `:buffers` | List open buffers.                  |
| `:b <num>`          | Switch to buffer `<num>`.           |
| `:bd`               | Delete (close) current buffer.      |
| `:bnext` / `:bn`    | Go to next buffer.                  |
| `:bprev` / `:bp`    | Go to previous buffer.              |
| `:bwipeout`         | Close and completely remove buffer. |

---

