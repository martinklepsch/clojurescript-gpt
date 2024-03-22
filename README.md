# ClojureScript GPT

[![](https://badgen.net/badge/ClojureScript%20GPT/Open/10a37f)](https://bit.ly/clojurescript-gpt)

This is an attempt at creating a ClojureScript aware 'coding buddy' helping
with some of the grunt work of working in an ecosystem that has less examples
available than its base ecosystem, Javascript.

It's main feature is to generate idiomatic ClojureScript (and dialects like
squint, cherry), based on Javascript code.

It focuses on ClojureScript (and its dialects) only.

## It's not great (yet)

Currently it will still try to use `core.async` when asking for squint code and
things like that but I hope with expanding `knowledge/` that can be adjusted.

## Contribute!

This could be an interesting attempt at making ClojureScript more accessible
and mitigate some of the downside of the smaller ecosystem. If you think that's cool,
please consider contributing files in the `knowledge/` directory.

You can find the base instructions in `gpt-instructions.md`.

You can also add specific files that are available on the web by extending the `bb fetch` task.

I will try to update the GPT with new files quickly.

![XX](https://badgen.net/badge/Last%20Update/2024-03-22/10a37f)
