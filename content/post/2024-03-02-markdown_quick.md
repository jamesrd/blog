+++
author = "James DeVries"
title = "Markdown Quick Reference"
date = "2024-03-02"
description = "Quick markdown examples for things I use"
tags = [
    "markdown", "md", "blog"
]
+++
## Links:

Example for [the link to my homepage](https://www.jamesrdevries.com/):
```markdown
[the link to my homepage](https://www.jamesrdevries.com/)
```

## Captions:

Include image text and a caption block beneath:
```markdown
![Image alt text](example.png "Caption text beneath")
```

![Image alt text](example.png "Caption text beneath")


## Tables:

Formatting can even be done within tables:
```markdown
| Italics   | Bold     | Code   | Links   |
| --------  | -------- | ------ | ------- |
| *italics* | **bold** | `code` | [Link](https://www.jamesrdevries.com/) |
```

| Italics   | Bold     | Code   | Links   |
| --------  | -------- | ------ | ------- |
| *italics* | **bold** | `code` | [Link](https://www.jamesrdevries.com/) |

## Code Blocks:

Enclose in 3 ticks ``` and specify the language type on the first line
of ticks like this: 
```markdown
```rust
```
Then end with 3 more ticks at the start of a line.

```rust
#[derive(States, Debug, Clone, Copy, Eq, PartialEq, Hash, Default)]
pub enum AppState {
    #[default]
    MainMenu,
    Game,
    GameOver,
}
```

## Blockquote with attribution

> Don't communicate by sharing memory, share memory by communicating.<br>
> — <cite>Rob Pike[^1]</cite>

[^1]: The above quote is excerpted from Rob Pike's [talk](https://www.youtube.com/watch?v=PAAkCSZUG1c) during Gopherfest, November 18, 2015.

## Headings:

Headings are a series of `#` followed by a space then the text for the heading.
The heading number is determined by the number of `#`.
Example for H2:
```markdown 
## The heading text...
```

### Heading size reference for this blog:
# H1
## H2
### H3
#### H4
##### H5
###### H6

