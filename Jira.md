# MetaBrainz bug tracking

MetaBrainz uses Jira to track bugs. It is hosted at https://tickets.metabrainz.org/

Each main MetaBrainz project has its own project in Jira.

### Working on tickets

If you want to work on a ticket, you don't need to ask for permission. Just check
that the ticket hasn't been assigned to any other user, and assign it to yourself
by clicking on the _Assign_ or _Assign to me_ link.

If you want to work on a ticket which has been assigned to someone else, and it doesn't
look like any work has been done for a while, you can post a question asking them if
they are still going to complete the work.

If you have any questions about a ticket, add a comment. Project leads will automatically
get sent an email informing them of your comment, so you don't need to follow it up
yourself.

When you have assigned a ticket to yourself, set its status to in progress by clicking
`Start Progress`. This shows others that you are actively working on a task.

When you finish the task, open a Pull request on the relavent project. See [GitHub.md] with
additional information about how to name and submit a Pull Request. In Jira, click `Resolve Issue`
to mark that a review has been submitted, and paste a link to the GitHub pull request URL as
a comment.

Once a review has been successfully merged, the project admin will close the ticket.
