# VI or VIM Editor

## Install `VIM` on Linux

```bash
sudo spt install vim
```

```bash
sudo yum install vim
```

```bash
sudo zypper install vim
```

```bash
sudo pacman -S vim
```

---

### Vim Mode: Normal Mode

#### Navigation in VIM in Normal Mode

| Items | Commands or Keys |
| --- | --- |
| Basic Cursor Navigation | `j` - down, `k` - up, `l` - right, `h` - left |
| Starting and ending of line | `0` - starting of line,`$` - end of line |
| Starting of file and ending of file | `gg` - starting of file, `G` - ending of file |
| Move to line number | `<:line-number>`, |
| Word by Word Navigation | `w`\- starting of next word, `b`\- starting of previous word, `e`\- end of word or next word |
| Sentence navigation | `(` - start of previous sentence, `)`\- start of next sentence |
| Paragraph navigation | `}` - next paragraph, `{`\- previous paragraph |
| Navigate on view | `H`\- top line of window, `L`\- last line of window, `M`\- middle line of window |

#### Editing Mode in VIM

| Items | Command or Keys |
| --- | --- |
| Switching modes | `i`\- enter insert mode, `ESC`\- exit insert mode |
| Append | `a`\- insert next to cursor, `A`\- insert at the end of the line, `I`\- insert in the beginning of the line |
| Insert in new line | `o`\- open new line below cursor, `O`\- open new line above cursor |
| Visual Mode | `v`\- enter visual mode, `esc`\- exit visual mode |
| Replace Mode | `R`\- enter replace mode, `esc` - exit visual mode |

#### Editing in VIM

| Keys | Effect |
| --- | --- |
| delete | `x`\- delete char at cursor, `X` - delete char before cursor, `s`\- delete char and insert mode  `dd`\- delete line (cut), `D`\- delete line after the cursor  `cw`\- delete word after cursor and insert mode, `C`\- delete line after cursor and insert mode  `cc`\- change whole line, `S`\- delete line and insert mode |
| Switch Case | `g~`\- switch case, `gu`\- lower case, `gU`\- upper case |

#### Cut, Copy and Paste in VIM

| Action | Keys |
| --- | --- |
| copy | Press `v` to enter Visual mode, move cursor to select the content, press y to copy |
| cut | Press `v` to enter visual mode, move cursor to select the conetnt, press x to cut |
| paste | Press `p` to paste before cursor, `P` to paste after cursor |

#### Adding indentation

| Item | Command or keys |
| --- | --- |
| Indent for single line | `>>`, `<<` |
| Indent multiple lines | Enter Visual Mode `v`, select lines, Press `>` to add indent, `<` remove indent |

#### Split view in view

| Item | Command or Keys |
| --- | --- |
| Open files in Split | `vim file-1 file-2 -o`\- for horizontal split  `vim file-1 file-2 -O`\- for vertical split |
| Switch between windows | `ctrl+w w` switch window  `ctrl+w l` switch to right window  `ctrl+h` switch to left window  `ctrl+k` switch to above window  `ctrl+j` switch to below window |