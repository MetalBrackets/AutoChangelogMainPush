# AutoChangelogMainPush

Automatic changelog generation each time changes are pushed to the main branch based on commits

## Setup

### Install Commitizen

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

### GitHub : Créer un personal access token

**1. Générer un token**
Aller dans le compte Github > Settings > Developer Settings > Personal access tokens
-> Donner les droits au workflow pour l'accès au repos
-> Copier le token

**2. Ajouter le token au repo**
Aller dans Settings > Secrets > Actions > New reporitory secret
-> coller le token
-> Name : PERSONAL_ACCESS_TOKEN

## Github Action

Créer le .github/workflows/bumpversion.yml  
-> Documentation [ici](https://commitizen-tools.github.io/commitizen/tutorials/github_actions/)

```yml
name: Bump version

on:
  push:
    branches:
      - main

jobs:
  bump-version:
    if: "!startsWith(github.event.head_commit.message, 'bump:')"
    runs-on: ubuntu-latest
    name: "Bump version and create changelog with commitizen"
    steps:
      - name: Check out
        uses: actions/checkout@v3
        with:
          token: "${{ secrets.PERSONAL_ACCESS_TOKEN }}"
          fetch-depth: 0
      - name: Create bump and changelog
        uses: commitizen-tools/commitizen-action@master
        with:
          github_token: ${{ secrets.PERSONAL_ACCESS_TOKEN }}
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

- > regarder s'il n'y a pas une commande pour le tester à la main
  > -> regarder si un . cz.toml marche mieux
