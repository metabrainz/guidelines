# Using GitHub

## Submitting changes

We follow the "typical" GitHub workflow when contributing changes:

1. [Fork](https://help.github.com/articles/fork-a-repo/) a repository into your account.
2. Create a new branch and give it a meaningful name. For example, if you are going to fix issue MBS-4635, branch can be
   called `mbs-4635` or `replace-image`.
3. Make your changes and commit them with a [good description](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html)
   ([more details](https://chris.beams.io/posts/git-commit/)). *You don't need to provide a lot
   of details, but make sure that people who look at the commit history afterwards can understand what you were changing
   and why.*
4. [Create](https://help.github.com/articles/creating-a-pull-request/) a new pull request on GitHub.
   Make sure that the title of your pull request is descriptive.
   <details>
   <summary><i>Click to toggle formats for referencing ticket(s) in pull request’s title</i></summary>

     * If you are fixing an issue that exists in our bug tracker, reference it like this:
       ```
       MBS-4635: Allow replacing images
       ```
       (Not `[MBS-4635] - Allow replacing images` or `Allow replacing images (MBS-4635)` or `MBS-4635`.)
     * If you are fixing several issues at once, reference them like this:
       ```
       MBS-9477, MBS-10568, MBS-10569: DiscID tab improvements
       ```
     * In the rare case you are partially fixing an issue, reference it like this:
       ```
       MBS-10365 (III): Convert EventList to react-table
       ```
     Properly referenced tickets will be updated automatically.
   </details>
5. :shipit:

## Status checks and testing

Most of the projects have a set of tests that are run on each pull request to make sure that changes don't break the
*master* branch. These checks are mandatory in most cases.

Apart from MusicBrainz, our projects don't have a release schedule. This means that changes are released as soon as they
are ready. Keeping the *master* branch functional in this case is essential. If a change that breaks tests is merged, it
will cause issues for all the developers working on a project. It should be very easy to undo something that has been done
and rollback deployed version of a service.

Checks are run automatically by Jenkins or other services depending on what projects decide to go with.
