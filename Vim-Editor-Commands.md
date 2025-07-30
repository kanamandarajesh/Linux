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



