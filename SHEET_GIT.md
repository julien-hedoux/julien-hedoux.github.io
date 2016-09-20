# Clean your local branch list
`git remote prune origin`

# Remove useless remote branches

## No merged branches   

````sh
for branch in `git branch -r --no-merged | grep -v HEAD`; do echo -e $branch \\t`git show --format="%cr" $branch | head -n 1`; done | awk '{print $1}' | egrep -v 'develop|preprod|master|paywall|abo|docker|facebook' | xargs git branch -dr
``````

## Merged branches   
`````````sh
for branch in `git branch -r --merged | grep -v HEAD`; do echo -e $branch \\t`git show --format="%cr" $branch | head -n 1`; done | awk '{print $1}' | egrep -v 'develop|preprod|master|paywall|abo|docker|facebook' | xargs git branch -dr
``````
