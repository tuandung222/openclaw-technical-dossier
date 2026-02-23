# 23 - AI Agent Engineer Playbook (PhD)

## Engineering loop

1. specify behavior formally (pre/post conditions)
2. encode failing tests
3. implement minimal-change patch
4. add observability for new branch
5. validate safety regressions

## High-value seams in codebase

- `pi-embedded-runner` seams for run attempts and payload transforms
- tool policy pipeline seams
- routing/session seams
- gateway method handler seams

## Anti-pattern catalog

- policy bypass for temporary unblock
- silent fallback without reason annotation
- adding tool with implicit global exposure
- merging refactor and semantic change in one PR

## PR quality bar

- include negative tests
- include risk statement
- include rollback note
- include observability impact
