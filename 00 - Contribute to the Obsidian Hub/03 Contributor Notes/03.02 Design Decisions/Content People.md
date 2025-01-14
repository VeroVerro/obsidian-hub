## Ideas to reduce the overhead of these pages

*There is some overlap between these ideas...*



### Change author template to simplify manual intervention, when running `update-releases.py`

The reasoning behind [[Content Comments]] is to greatly reduce the number of lines that need to be reverted when the author pages are updated, from minimal edits to to the authors template(s).

It will help contributors see the intention for links and `^` too...

**Change this:**

```markdown
<!-- - Website: <> ^website-->
<!-- - [[Publish sites|Publish site]]: ^publish-->
```

To this:

```markdown
<!-- - Website: <https://> ^website-->
<!-- - [[Publish sites|Publish site]]: <https://> ^publish-->
```

**Change this:**

```markdown
<!--
### Unlisted plugins

- 
-->
```

To this:

```markdown
<!--
### Unlisted plugins
-->
```

Change this:

```markdown
<!--
### Others

- 
-->
```

To this:

```markdown
<!--
### Others
-->
```

**Change this:**

```markdown
<!--
## Sponsor this author

- [[GitHub sponsors]]: [Sponsor @{{title}} on GitHub Sponsors](https://github.com/sponsors/{{title}}) ^github-sponsor
- [[Buy me a coffee]]: ^buy-me-a-coffee
- [[PayPal]]: ^paypal
- [[Patreon]]: ^patreon

-->
```

To this:

```markdown
<!--
## Sponsor this author
-->

<!-- - [[GitHub sponsors]]: [Sponsor @{{title}} on GitHub Sponsors](https://github.com/sponsors/{{title}}) ^github-sponsor -->
<!-- - [[Buy me a coffee]]: <https://> ^buy-me-a-coffee-->
<!-- - [[PayPal]]: <https://> ^paypal-->
<!-- - [[Patreon]]: <https://> ^patreon-->
```

Change this:

```markdown
<!--
## Follow this author

- [[YouTube Channels|On YouTube]]: ^youtube
- Twitter: ^twitter
- ...
-->
```

To this:

```markdown
<!--
## Follow this author
-->

<!-- - [[YouTube Channels|On YouTube]]: <https://> ^youtube-->
<!-- - Twitter: <https://> ^twitter-->
<!-- - ... -->
```

### Create-and-include separate files for machine-generated content

**Decision**: Get the same benefit by replacing chunks of code inside the single files, such as is done for MOCs and Uncategorized Plugins.

Make the Python script that creates Author pages put the generated text in to little files for inclusion in the main file.

For example, we would end up with something like this:

Part of `chrisgrieser.md`:

```markdown
## Author of

%% Hub Content: Don’t edit below %%
![[chrisgrieser.plugins]]

![[chrisgrieser.themes]]
%% Hub Content: Don’t edit above %%
```

In `chrisgrieser.plugins`:

```markdown
### Plugins
- [[obsidian-extra-md-commands|Extra Markdown Commands]]
```

In `chrisgrieser.themes`:

```markdown
### Themes
- [[Shimmering Focus]]
```

The big advantage of this is that the rest of the author file, with manual edits, will not get over-written.

For discussion:

- Would need to identify a sub-dir to put the files in
- If manually creating new author pages, would need to create the 2 extra files and put them in the right location

## Odds and Ends

- [ ] Rename [Author template](https://github.com/obsidian-community/obsidian-hub/blob/main/00%20-%20Contribute%20to%20the%20Obsidian%20Hub/01%20Templates/T%20-%20Author.md) to `T - Person.md` - and link to it...
