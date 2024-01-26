[← Articles](README.md#articles)

# What Makes a Great Git Commit Message

And why should I care?

## A Good Commit Message

```
Capitalized short summary (50 chars max)

More details about what your git commit accomplishes (72 chars wrap).
In Git, this is treated as the description of your commit message. It's
useful to provide more details than your short summary here.

Something even more useful is why you made this commit. Why does your
change fix the bug? What steps did you follow to reproduce it? What is
useful context that can't be gleaned from your code?

You can even use bullet points:

- Bullet points are great

- You start them with a hyphen or bullet point

- Use a hanging indent

It's often helpful to provide a link to JIRA or your issue tracker:
JIRA: https://aumni.atlassian.net/browse/DEV-1234
```

In this sample commit message, there's A LOT of information that is included past the simple `git commit -m "Capitalized short summary"`. It has paragraphs that more explain the what, it digs into the why, and provides more context.

Can you do this with a simple `git commit -m`? No. You need to get used to `git commit`. If you're not a fan of Vim, you can swap out your Git editor: `git config --global core.editor "code --wait"`.

## Why Care About Git Commit Messages

Good commit messages can:

1. Help a future reader (including yourself) understand what changed and why
2. Allow you to understand more thoroughly how a file has changed over time (ie `git blame`)
3. Make reviewing your PR easier when done commit by commit

## Rules to Follow

1. Separate subject from body with a blank line
2. Limit the subject line to 50 characters
3. Capitalize the subject line
4. Do not end the subject line with a period
5. Use the imperative mood in the subject line
6. Wrap the body at 72 characters
7. Use the body to explain what and why vs. how

---

[Comments](https://github.com/ryanolsonx/ryanolsonx/discussions/TODO)

[Subscribe to be notified of new articles](https://github.com/ryanolsonx/blog/discussions/1)

[All Articles](https://github.com/ryanolsonx/blog/blob/master/README.md#articles)

---

Copyright Ryan Olson 2024-present
