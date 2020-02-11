# MetaBrainz issue tracking

MetaBrainz uses Jira to track bugs and tasks. It is hosted at https://tickets.metabrainz.org/.

Each main MetaBrainz project has [its own project in Jira](https://tickets.metabrainz.org/secure/BrowseProjects.jspa).

This document describes
For information about how to report an issue in a MetaBrainz project,
[see our wiki](https://wiki.musicbrainz.org/How_to_Report_an_Issue).

## Working on tickets

If you want to work on a ticket, you don't need to ask for permission. Just check
that the ticket hasn't been assigned to any other user, and assign it to yourself
by clicking on the _Assign_ or _Assign to me_ link.
Some tickets may have the status "Decision Required". If this is the case it requires
more discussion with the project maintainers to resolve any remaining open questions.
Make sure you resolve these questions before starting work on such a ticket.

If you want to work on a ticket which has been assigned to someone else, and it doesn't
look like any work has been done for a while, you can post a question asking them if
they are still going to complete the work.

If you have any questions about a ticket, add a comment. People who are watching
this ticket will automatically get sent an email informing them of your comment.
You do not need to contact them yourself to make sure that they recieved your comment.

When you have assigned a ticket to yourself, set its status to "In Progress" by clicking
`Start Progress`. This shows others that you are actively working on a task.

When you finish the task, open a _Pull Request_ on the relevant project.
You may instead want to open it as a _draft_ if it cannot be merged yet,
for example when it depends on another Pull Request.

If you correctly followed [how to name and submit a Pull Request](GitHub.md),
_GitHub Bot_ automatically marks in Jira that a review has been submitted,
with a link to the GitHub Pull Request in a comment.
Once a pull request has been reviewed and merged by one of the project maintainers,
it automatically marks in Jira that it has been merged into the development branch.

It is up to the project maintainers to mark tickets in beta testing or to close
these as “Fixed” when the corresponding deployment steps have been completed.
