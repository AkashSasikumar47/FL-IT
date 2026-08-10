# WHS App

## Test Barcodes

| Category     | Barcodes                                                                                  |
| ------------ | ----------------------------------------------------------------------------------------- |
| Login        | `ln-akash.sasikumar*`                                                                     |
| Printer      | `7ZE000*`                                                                                 |
| Piece        | `199792AACS*`, `112311AAAX*`, `138342AAPV*`, `166822AAPE*`, `171760AABL*`, `1102601AAAH*` |
| Packed Piece | `148742ACYU*`                                                                             |
| Article      | `3196347*`                                                                                |
| Package      | `42345811P1B`, `42345358P1H`                                                              |
| Stillage     | `512*`, `52*`, `57112*`                                                                   |
| Box          | `8D310654*`, `8D313048*`                                                                  |
| Location     | `2ABA*`, `2KEF*`, `291A*`, `2AAA*`                                                        |
| Invalid      | `199702AACS*`                                                                             |

## Install & Run

```bash
export NODE_AUTH_TOKEN=your-github-token
yarn install
yarn develop
yarn build
yarn test
```

- http://localhost:8000/login?tenantId=BE1
- http://BRHESDev11.main.brutex.com/

## Workflow

### Branch Setup

```bash
git checkout develop
git pull
git checkout -b WHS-XXXX-meaningful-name
```

### Commit & Push

```bash
git status
git add path/to/file
git commit -m "WHS-XXXX: short message"
git push -u origin WHS-XXXX-meaningful-name
```

### Undo / Revert

```bash
git reset --soft HEAD~1
git reset --hard
git branch -D WHS-XXXX
git push origin --delete WHS-XXXX
git revert <commit-hash>
git push
```

### Stash

```bash
git stash push -u -m "WIP: temporary stash"
git stash list
git stash pop
```

### Sync with Develop

```bash
git checkout develop
git pull
git checkout WHS-XXXX
git fetch origin
git merge origin/develop
```

### Code Quality

```bash
npx prettier --write src/file-name
yarn lint:scripts
yarn lint:styles
yarn type-check
```

### Skip Worktree

```bash
git update-index --skip-worktree <file>
git update-index --no-skip-worktree <file>
git ls-files -v | grep '^S'
```
