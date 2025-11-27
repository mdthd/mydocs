# Shell Escape Sequences

## Basic Escape Sequences

- `\n` — Newline
- `\t` — Tab
- `\\` — Backslash
- `\"` — Double quote
- `\'` — Single quote
- `\a` — Bell (alert)
- `\b` — Backspace
- `\r` — Carriage return
- `\v` — Vertical tab
- `\f` — Form feed

---

## ANSI Escape Codes

### Color codes

| **Color** | **Foreground** | **Background** |
| --- | --- | --- |
| Black | 30  | 40  |
| Red | 31  | 41  |
| Green | 32  | 42  |
| Yellow | 33  | 43  |
| Blue | 34  | 44  |
| Magenta | 35  | 45  |
| Cyan | 36  | 46  |
| White | 37  | 47  |
| default color | 39  | 49  |

:::info
We can use the code like

`\033[31m`

`\x1b[31m`

`\e[31m`

`\E[31m`

All this are similar or equivalent
:::

### Text Styles

| **Code** | **Effect** | **Example** |
| --- | --- | --- |
| 0   | Reset | `\033[0m` |
| 1   | Bold/Bright | `\033[1m` |
| 2   | Faint | `\033[2m` |
| 3   | Italic | `\033[3m` |
| 4   | Underline | `\033[4m` |
| 5/6 | Blink | `\033[5m` or `\033[6m` |
| 7   | Reverse/Inverse | `\033[7m` |
| 8   | Invisible | `\033[8m` |
| 9   | Strikethrough | `\033[9m` |
| 21  | Bold off | `\033[21m` |
| 22  | Normal intensity | `\033[22m` |
| 23  | Not italic | `\033[23m` |
| 24  | Not underlined | `\033[24m` |
| 27  | Reverse off | `\033[27m` |

### Terminal Manupulation

- `\033[2J` : Clear entire screen
- `\033[1J` : Clear from cursor to beginning of screen
- `\033[0J` : Clear from cursor to end of screen
- `\033[0m` : Reset all styles (critical after styling)
- `\033[?1049h` : Switch to alternate buffer
- `\033[?1049l` : Return to main buffer

### Symbols using escape sequences

| **Symbol** | **Unicode Code** | **Example Escape in Bash** | **Name/Description** |
| --- | --- | --- | --- |
| ©   | U+00A9 | \\u00A9 | Copyright Sign |
| ®   | U+00AE | \\u00AE | Registered Sign |
| ™   | U+2122 | \\u2122 | Trademark Sign |
| ☺   | U+263A | \\u263A | White Smiling Face |
| ☹   | U+2639 | \\u2639 | White Frowning Face |
| ☀   | U+2600 | \\u2600 | Sun With Rays |
| ☁   | U+2601 | \\u2601 | Cloud |
| ☂   | U+2602 | \\u2602 | Umbrella |
| ☃   | U+2603 | \\u2603 | Snowman |
| ⚡   | U+26A1 | \\u26A1 | High Voltage (Lightning) |
| ♥   | U+2665 | \\u2665 | Black Heart Suit (filled heart) |
| ★   | U+2605 | \\u2605 | Black Star |
| ☆   | U+2606 | \\u2606 | White Star |
| ☑   | U+2611 | \\u2611 | Ballot Box With Check |
| ✓   | U+2713 | \\u2713 | Check Mark |
| ✗   | U+2717 | \\u2717 | Ballot X |
| ✮   | U+272E | \\u272E | Black Four-Pointed Star |
| ☎   | U+260E | \\u260E | Black Telephone |
| ☘   | U+2618 | \\u2618 | Shamrock |
| ⚘   | U+2698 | \\u2698 | Flower |
| ☯   | U+262F | \\u262F | Yin Yang |
| ☸   | U+2638 | \\u2638 | Wheel of Dharma |
| ☮   | U+262E | \\u262E | Peace Symbol |
| ☢   | U+2622 | \\u2622 | Radioactive |
| ☣   | U+2623 | \\u2623 | Biohazard |
| ¶   | U+00B6 | \\u00B6 | Pilcrow (Paragraph symbol) |
| §   | U+00A7 | \\u00A7 | Section Sign |
| ♻   | U+267B | \\u267B | Recycling Symbol |
| ♂   | U+2642 | \\u2642 | Male Sign |
| ♀   | U+2640 | \\u2640 | Female Sign |

## Using `tput` command

| Task | Command Example | Description |
| --- | --- | --- |
| **Clear screen** | `tput clear` | Clears the terminal screen |
| **Move cursor** | `tput cup 5 10` | Moves cursor to row 5, column 10 |
| **Bold text** | `tput bold` | Enables bold text |
| **Underline text** | `tput smul` | Starts underlining |
| **Remove underline** | `tput rmul` | Stops underlining |
| **Reset formatting** | `tput sgr0` | Resets all text styles and colors |
| **Set foreground color** | `tput setaf 2` | Sets text color (e.g., 2 = green) |
| **Set background color** | `tput setab 4` | Sets background color (e.g., 4 = blue) |
| **Get terminal width** | `tput cols` | Returns number of columns |
| **Get terminal height** | `tput lines` | Returns number of rows |
| **Ring terminal bell** | `tput bel` | Triggers a beep or visual bell |
| **Hide cursor** | `tput civis` | Makes cursor invisible |
| **Show cursor** | `tput cnorm` | Makes cursor visible again |
| **Initialize terminal** | `tput init` | Applies terminal initialization settings |
| **Reset terminal** | `tput reset` | Resets terminal to default state |
| **Print terminal name** | `tput longname` | Displays full name of current terminal type |

## Examples

To get alert sound

```bash
echo -e "\a"
```

```bash
tput bel
```

To write bold or bright

```bash
echo -e "\x1b[1m\nThis is bold Text\x1b[0m \n"
```

To write italic text

```bash
echo -e "\x1b[3m\nThis is italic Text\x1b[0m \n"
```