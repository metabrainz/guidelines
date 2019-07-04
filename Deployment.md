# Deployment Practices

Most of our Python projects (ListenBrainz, AcousticBrainz and CritiqueBrainz) have beta instances
running alongside the production instances. The production instances follow the `production`
branch in the git repository, while the beta instances follow the `master` branch.
Most code (excluding very urgent hotfixes) is first merged into `master` and deployed into
beta before being officially released into production. Urgent hotfixes are generally fixed by
pull requests against the `production` branch directly.

# Steps to deploy to production

* Merge `master` into `production`, most of the code should already have been reviewed, but we still
prefer opening Pull Requests for this merge before release.
* Create a git tag of the format `v-$YEAR-$MONTH-$DATE.$VERSION`, for example `v-2019-07-04.0`.
* Push to GitHub.
* Deploy the `production` branch.
