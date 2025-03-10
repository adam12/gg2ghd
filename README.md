# gg2ghd

This is a program to import posts extracted from Google Groups into
GitHub Discussions. It also contains a program to remove all GitHub
Discussions from a repository, useful for testing.

## Usage

First, you need to extract all Google Groups discussions to files
using https://github.com/icy/google-group-crawler.  After that
step has been completed, this will use the mbox directory created
as the source of data to import.

```
Usage: ruby import-into-github-discussions.rb owner repo token path group"
owner: GitHub account name
 repo: GitHub repository name
token: GitHub access token (see https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token)
 path: Local path to mbox dir created using https://github.com/icy/google-group-crawler
group: Name of Google Group, used for constructing URL

Usage: ruby remove-all-discussions.rb owner repo token"
owner: GitHub account name
 repo: GitHub repository name
token: GitHub access token (see https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token)
```

## Requirements

1. ruby - Programming Language
2. graphql-client gem - For using GitHub Discussions's GraphQL API
3. mail - For parsing the files in the mbox directory

## Caveats

There is very little error handling done.  There are no descriptive
comments in the source code.

Files added to Google Groups are not copied.

Only the text part of the Google Groups post are used, so there isn't
any formatting, other than how GitHub Discussions will handle the text
as markdown.

The "General" Discussion Category is used for all posts.

The author of all posts in GitHub Discussions will be the GitHub
user used to import, and the date will be the time the GitHub
Discussion was created.  This appends the original author (partially
obscured email addresses) and original post date to the body of the
discussion post or comment.  The discussion post also contains a link
back to the Google Groups post.

This was used to convert the ruby-forme Google Group posts to
Discussions for jeremyevans/forme and jeremyevans/autoforme:

* Forme: https://github.com/jeremyevans/forme/discussions
* AutoForme: https://github.com/jeremyevans/autoforme/discussions

# License

This code is licensed under the MIT license.  See the MIT-LICENSE
file for details.

# Author

Jeremy Evans <code@jeremyevans.net>
