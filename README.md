# OASg Maven library publishing for GitHub

This is a demonstration how [OASg](https://gitlab.com/team-supercharge/oasg) -
a wrapper for [openapi-generator](https://github.com/OpenAPITools/openapi-generator) -
can be used with GitHub Actions publishing jar files to GitHub repository.

This guide is written for OASg 13.0.1 (as of 2023-12-13)

## Configuration steps

- the published OASg image only supports ARM architecture that cannot be run on the default GitHub runners
  - starting from `node:18.15.0` image - OASg checks for this exact version - [install java, jq, wget](.github/workflows/build-and-publish.yaml)
- OASg provides [settings.xml](https://gitlab.com/team-supercharge/oasg/-/blob/master/targets/spring/settings.xml?ref_type=heads)
  for GitLab repository - to support GitHub, this file [is overriden](patches/@team-supercharge+oasg+13.0.1.patch) using [pactch-package](package.json)
