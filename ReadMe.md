<p align="center">
Sample repo to automatically bump a Homebrew cask
</p>
<p align="center">  
whenever a new tag is pushed on the main app repo using a GitHub actions template
</p>


## Installation

- Create a [custom GitHub access token (classic)](https://github.com/settings/tokens) with the `public_repo` scope
- Add this token to your `Repository secrets` under the name of `TOKEN` (the repo is the one that will run this workflow, e.g., the one that has the main app that needs a cask 'github.com/YOUR_NAME/YOUR_APP_REPO/settings/secrets/actions')
- Add [this bump_homebrew_cask.yml workflow][https://github.com/eugenesvk/homebrew-bump/blob/main/.github/workflows/bump_homebrew_cask.yml] from this repo to yours
- Change it to reference your Homebrew cask tap
```yaml
        tap 	: your_name/tap_name	# [opt] |homebrew/core|
        cask	: cask_name         	# [req] Cask name
```

## Usage

- Release your app as usual by pushing a `tag`
- Wait for the workflow to finish and merge the hopefully correct Pull Request on your Homebrew cask tap repo

## Known issues

- Not sure how to merge the PRs automatically
- The original [action-homebrew-bump-cask](https://github.com/eugenesvk/action-homebrew-bump-cask/blob/master/action.yml) this workflow relies on monkey-patching the Homebrew repo to work with GitHub APIs, so might stop working if the patched code is change
