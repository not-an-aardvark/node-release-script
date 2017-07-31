# node-release-script

An opinionated release script

## Usage

```
$ npm install -g @not-an-aardvark/node-release-script
$ node-release-script
```

## What does it do?

Note that this tool is very opinionated, is not intended to be a general-purpose release tool. If you're looking for that, consider using [semantic-release](https://github.com/semantic-release/semantic-release) instead.

This tool does the following:

* Generates a changelog from the git commits since last release
* Updates the version number in `package.json`, according to semantic versioning
* Creates a git commit for the release
* Creates a git tag for the release

Note that this does not push the updates anywhere. You should run `npm publish`, `git push`, and `git push --tag` afterwards to update the remotes.

The updated version number is determined based on the commit messages since the last release. Your commit messages should start one of the following prefixes:

* `Breaking`: semver-major
* `New`: semver-minor
* `Update`: semver-minor
* `Fix`: semver-patch
* `Docs`: semver-patch
* `Build`: semver-patch
* `Upgrade`: semver-patch
* `Chore`: semver-patch

The changelog will include links to issues and commits, based on the `origin` remote URL in your local git repository. To ensure that the links in the changelog work, make sure your remote is called `origin`, it uses the `https:` protocol, and it is linked to an existing reporitory on GitHub.

In order for commits to be added correctly, the changelog must be in a file called `CHANGELOG.md` in the project root. It must start with the text `# Changelog` followed by two linebreaks.

## License

MIT
