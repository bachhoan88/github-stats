# [GitHub Stats Visualization](https://github.com/jstrieb/github-stats)

<a href="https://github.com/jstrieb/github-stats">

![](https://github.com/bachhoan88/github-stats/blob/master/generated/overview.svg)
![](https://github.com/bachhoan88/github-stats/blob/master/generated/languages.svg)

</a>

Generate visualizations of GitHub user and repository statistics using GitHub
Actions.

This project is currently a work-in-progress; there will always be more
interesting stats to display.

## Background

When someone views a profile on GitHub, it is often because they are curious
about a user's open source projects and contributions. Unfortunately, that
user's stars, forks, and pinned repositories do not necessarily reflect the
contributions they make to private repositories. The data likewise does not
present a complete picture of the user's total contributions beyond the current
year.

This project aims to collect a variety of profile and repository statistics
using the GitHub API. It then generates images that can be displayed in
repository READMEs, or in a user's [Profile
README](https://docs.github.com/en/github/setting-up-and-managing-your-github-profile/managing-your-profile-readme).

Since the project runs on GitHub Actions, no server is required to regularly
regenerate the images with updated statistics. Likewise, since the user runs
the analysis code themselves via GitHub Actions, they can use their GitHub
access token to collect statistics on private repositories that an external
service would be unable to access.

## Disclaimer

If the project is used with an access token that has sufficient permissions to
read private repositories, it may leak details about those repositories in
error messages. For example, the `aiohttp` library—used for asynchronous API
requests—may include the requested URL in exceptions, which can leak the name
of private repositories. If there is an exception caused by `aiohttp`, this
exception will be viewable in the Actions tab of the repository fork, and
anyone may be able to see the name of one or more private repositories.

Due to some issues with the GitHub statistics API, there are some situations
where it returns inaccurate results. Specifically, the repository view count
statistics and total lines of code modified are probably somewhat inaccurate.
Unexpectedly, these values will become more accurate over time as GitHub
caches statistics for your repositories. Additionally, repositories that were
last contributed to more than a year ago may not be included in the statistics
due to limitations in the results returned by the API.

For more information on inaccuracies, see issue
[#2](https://github.com/jstrieb/github-stats/issues/2),
[#3](https://github.com/jstrieb/github-stats/issues/3), and
[#13](https://github.com/jstrieb/github-stats/issues/13).

