# Regular Expressions (regex)

## BRE: Basic Regular Expression

| **Meta Character** | **Meaning / Use** | **Example** | **Special Notes** |
| --- | --- | --- | --- |
| `.` | Any character except newline | `a.b` matches "acb", "a1b" | Wildcard character |
| `^` | Start of string/line | `^Hello` matches "Hello world" | Anchor |
| `$` | End of string/line | `world$` matches "Hello world" | Anchor |
| `*` | 0 or more repetitions | `lo*` matches "l", "lo", "loo" | Greedy by default |
| `+` | 1 or more repetitions | `lo+` matches "lo", "loo" | Requires at least one match |
| `?` | 0 or 1 occurrence | `lo?` matches "l", "lo" | Also used for lazy quantifiers |
| `{n}` | Exactly n times | `a{3}` matches "aaa" | Precise control |
| `{n,}` | n or more times | `a{2,}` matches "aa", "aaa" |     |
| `{n,m}` | Between n and m times | `a{2,4}` matches "aa", "aaa", "aaaa" |     |
| `[]` | Character class | `[aeiou]` matches vowels | Can include ranges like `[a-z]` |
| `[^]` | Negated character class | `[^0-9]` matches non-digits | `^` inside brackets means NOT |
| `()` | Grouping and capturing | `(ab)+` matches "abab" | Can be reused in replacements |
| `(?:)` | Non-capturing group | `(?:ab)+` matches "abab" | Faster, no memory saved |
| `\|` | Alternation (OR) | `cat\|dog` matches either | Use with groups for clarity |
| `\` | Escape character | `\.` matches "." | Escapes meta characters |
| `\b` | Word boundary | `\bcat\b` matches "cat" | Useful for whole word matching |
| `\B` | Non-word boundary | `\Bcat\B` matches "educate" | Opposite of `\b` |
| `(?=...)` | Positive lookahead | `\w+(?=ing)` matches "play" in "playing" | Doesn't consume characters |
| `(?!...)` | Negative lookahead | `\w+(?!ing)` matches "run" in "running" |     |
| `(?<=...)` | Positive lookbehind | `(?<=@)\w+` matches "gmail" in "@gmail" |     |
| `(?<!...)` | Negative lookbehind | `(?<!@)\w+` excludes "gmail" in "@gmail" |     |