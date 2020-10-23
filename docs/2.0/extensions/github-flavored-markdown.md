---
layout: default
title: Github-Flavored Markdown
description: The GithubFlavoredMarkdownExtension class includes all the GFM addons
---

# Github-Flavored Markdown

You can manually add the GFM extension to your environment like this:

```php
use League\CommonMark\CommonMarkConverter;
use League\CommonMark\Environment\Environment;
use League\CommonMark\Extension\GithubFlavoredMarkdownExtension;

$environment = Environment::createCommonMarkEnvironment();
$environment->addExtension(new GithubFlavoredMarkdownExtension());

$converter = new CommonMarkConverter([], $environment);
echo $converter->convertToHtml('Hello GFM!');
```

This will automatically include all of these sub-extensions/features for you:

- [Autolinks](/2.0/extensions/autolinks/)
- [Disallowed Raw HTML](/2.0/extensions/disallowed-raw-html/)
- [Strikethrough](/2.0/extensions/strikethrough/)
- [Tables](/2.0/extensions/tables/)
- [Task Lists](/2.0/extensions/task-lists/)

Or, if you only want a subset of GFM extensions, you can add them individually like this instead:

```php
use League\CommonMark\CommonMarkConverter;
use League\CommonMark\Environment\Environment;
use League\CommonMark\Extension\Autolink\AutolinkExtension;
use League\CommonMark\Extension\DisallowedRawHtml\DisallowedRawHtmlExtension;
use League\CommonMark\Extension\Strikethrough\StrikethroughExtension;
use League\CommonMark\Extension\Table\TableExtension;
use League\CommonMark\Extension\TaskList\TaskListExtension;

$environment = Environment::createCommonMarkEnvironment();
// Remove any of the lines below if you don't want a particular feature
$environment->addExtension(new AutolinkExtension());
$environment->addExtension(new DisallowedRawHtmlExtension());
$environment->addExtension(new StrikethroughExtension());
$environment->addExtension(new TableExtension());
$environment->addExtension(new TaskListExtension());

$converter = new CommonMarkConverter([], $environment);
echo $converter->convertToHtml('Hello GFM!');
```

This extension relies on the `CommonMarkCoreExtension` being enabled, so [don't forget to include that](/2.0/extensions/commonmark/) too.