**Do not merge this branch.** 

Instead keep our `main` updated from upstream. Apply changes to the `stealthtest` branch, and keep it rebased against *a tagged release* from the upstream `blockscout/blockscout` repo.

# Update from upstream
1. Add the upstream repo as a remote
```
git remote add upstream git@github.com:blockscout/blockscout.git
```

2. Fetch the latest commits
```
git fetch upstream
```

3. Switch to `stealthtest` branch

```
git checkout stealthtest
```

4. Rebase the changes from the `stealthtest` branch against a tagged release from upstream.
```
git rebase v5.2.2-beta

git push
```


# Update docker images
Manually update images by using `docker-compose` to build/push from local.

```
PROJECT_ID=my-project DOCKER_TAG=my-custom-tag docker-compose build

docker push <tag>

# re-tag the image and push to each package repo for dev/staging/prod
```

Release tags should be in the format: `<releaseVersion>-stealthtest<stealthtestVersion>` where `releaseVersion` is the base version of `blockscout`, and `stealthtestVersion` is based on our changes.

The default tag is:
```
us-central1-docker.pkg.dev/minikube/nameless/blockscout:1.0.0-stealthtest0.1.0
```
