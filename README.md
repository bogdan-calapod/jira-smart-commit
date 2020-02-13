# JIRA Smart Commits

[![Stable Version](https://img.shields.io/npm/v/jira-smart-commit.svg)](https://www.npmjs.com/package/jira-smart-commit)
[![Build Status](https://travis-ci.org/jessedobbelaere/jira-smart-commit.svg?branch=master)](https://travis-ci.org/jessedobbelaere/jira-smart-commit)
[![Dependabot Status](https://api.dependabot.com/badges/status?host=github&repo=jessedobbelaere/fork-cms-webpack-boilerplate)](https://dependabot.com)
[![MIT license](http://img.shields.io/badge/license-MIT-brightgreen.svg)](http://opensource.org/licenses/MIT)
[![Downloads](https://img.shields.io/npm/dt/jira-smart-commit.svg)](https://www.npmjs.com/package/jira-smart-commit)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat)](http://makeapullrequest.com)

A Node.js git hook script to prefix commits automatically with the JIRA ticket, based on a branch name.

> ⚠ This fork removes the `master`/`develop`-only branch check.

## Usage

### Installation

1. Install [Husky](https://www.npmjs.com/package/husky) in your project to configure Git hooks easily

```bash
npm install --save-dev husky
```

2. Install this package in your project:

```bash
npm install --save-dev jira-smart-commit
```

3. Configure scripts in `package.json`. The script expects his first argument to be the JIRA tag of the project.

```json
    "husky": {
        "hooks": {
            "commit-msg": "jira-smart-commit SPAN",
            "pre-commit": "lint-staged"
        }
    },
```

or environment variables

- TAG_MATCHER - regular expression
- TAG_MATCH_INDEX - match index
- DEBUG - if true will console log some data about branch, matches array etc

example: if your branches have feature/SPAN-1234/some-description template

```
"commit-msg": "TAG_MATCHER=\"^[^/]+/(SPAN-[0-9]+)\" TAG_MATCH_INDEX=1 jira-smart-commit"
```

4. Do your git commits like usual. If the branch was prefixed with a JIRA tag, your commit message will get prefixed with
   the same tag.

```
Branch: TAG-411-husky-git-hooks
Commit message: "Add git hooks to project" → "TAG-411 Add git hooks to project"
```
