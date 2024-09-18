# AutoChangelogMainPush

A simple method to automatically generate a changelog each time changes are pushed to the main branch, based on commit history.
Final solution : Github Action [release-please](https://github.com/googleapis/release-please)
Note : The problem with commitizen is that it doesn't generate commit links... too bad.

## Setup

### GitHub: Create a Personal Access Token

**1. Generate a token**  
Go to your GitHub account > Settings > Developer Settings > Personal access tokens  
-> Give the workflow rights to access the repository  
-> Copy the token

**2. Add the token to the repo**  
Go to Settings > Secrets > Actions > New repository secret  
-> Token name: PERSONAL_ACCESS_TOKEN  
-> Paste the token

## Usage

"Release Please automates CHANGELOG generation, the creation of GitHub releases, and version bumps for your projects.
Release Please does so by parsing your git history, looking for [Conventional Commit messages](https://www.conventionalcommits.org/en/v1.0.0/), and creating release PRs."

> [Documentation](https://github.com/googleapis/release-please)

**How to auto-increment versions with commits?**

| version | commit type                           | description                                 |
| ------- | ------------------------------------- | ------------------------------------------- |
| major   | `feat!:`, `fix!:`, `refactor!:`, etc. | SemVer major : represents a breaking change |
| minor   | `feat:`                               | SemVer minor : Represents a new feature     |
| patch   | `fix:`                                | SemVer patch : Represents bug fixes         |

🤖 And voilà, it's automated!
