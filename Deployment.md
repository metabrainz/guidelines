# Deployment Practices

> Note: This document covers steps for deploying projects to production, which is only performed
> by MetaBrainz contractors. It includes discussion about servers and repositories which other
> contributors won't have access to.

Most of our Python projects (ListenBrainz, AcousticBrainz and CritiqueBrainz) have beta instances
running alongside the production instances. The production instances follow the `production`
branch in the git repository, while the beta instances follow the `master` branch.
Most code (excluding very urgent hotfixes) is first merged into `master` and deployed into
beta before being officially released into production. Urgent hotfixes are generally fixed by
pull requests against the `production` branch directly.

# Steps to deploy to production

* Merge `master` into `production`, most of the code should already have been reviewed, but we still
prefer opening Pull Requests for this merge before release.
* Create a git tag of the format `v-$YEAR-$MONTH-$DATE.$VERSION`, for example `v-2019-07-04.0`. If multiple releases
are made on the same day, increase `$VERSION`

      git checkout production  # assuming that this is up-to-date with what you want to release
      export VERSION=v-2019-07-04.0
      git tag $VERSION
      git push --tags 

* Make a release on github. Go to project -> releases -> Draft a new release and paste the tag into
  the _Tag version_ field, then Publish the release.

* Build and push the docker image

      # AcousticBrainz, CritiqueBrainz and ListenBrainz have a helper `push.sh` script
      # in the `docker` directory that we use.
      ./docker/push.sh prod $VERSION

* Edit `scripts/nodes/[hostname].sh` in the _docker-server-configs_ repository to update the docker tag
  used to run this service

      start_acousticbrainz_web 'prod' 'v-2019-07-04.0'

  Commit and push this change, and then pull on the node in `/root`

* On the node where you deploy, stop and remove the existing container and start all services again

      docker stop acousticbrainz-web-prod && docker rm acousticbrainz-web-prod && ./scripts/start_services.sh
