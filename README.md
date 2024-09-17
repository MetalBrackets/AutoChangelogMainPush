# AutoChangelogMainPush
Automatic changelog generation each time changes are pushed to the main branch based on commits

feature 1
feature 2
feature 3

## Setup
pip install --user -U Commitizen
poetry add commitizen --group dev
cz init
```sh
Welcome to commitizen!

Answer the questions to configure your project.
For further configuration visit:

https://commitizen-tools.github.io/commitizen/config/

? Please choose a supported config file:  pyproject.toml
? Please choose a cz (commit rule): (default: cz_conventional_commits) cz_conventional_commits
? Choose the source of the version: commitizen: Fetch and set version in commitizen config (default)
? Is v0.1.0 the latest tag? No
? Please choose the latest tag:  v0.1.0
? Choose version scheme:  semver
? Is "v$version" the correct tag format? Yes
? Create changelog automatically on bump Yes
? Keep major version zero (0.x) during breaking changes Yes
? What types of pre-commit hook you want to install? (Leave blank if you don't want to install) done

You can bump the version running:

        cz bump

Configuration complete 🚀
```

## Commit and versioning step by step
```sh
# commande friend
cz infos

# commit whith conventionnal coimmt 
cz commit

# autoincremente version
cz bump

# push on your branch
git push

# push the tags
git push --tag


```

test