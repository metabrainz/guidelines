# Guidelines for using self-hosted services in MetaBrainz projects

This is a set of guidelines for the main contributors of MetaBrainz
projects to keep their use of self-hosted services maintainable.

This document mentions general guidelines only about **documentation
requirements** for a project when using a self-hosted service so
that system adminstrators can actually understand what to do or to
avoid without having to read the code to understand an emergency
situation or to necessarily rely on the code authors to take action.

It is completed by the service-specific guidelines in this directory
which rather focus on **implementation requirements**.

See also the private system administration wiki for details about how
these self-hosted services are hosted in the MetaBrainz infrastructure.

The below lists are indicative of what should likely be documented.
Those are not exhaustive.

## Requirements to be documented

- Tolerance to connectivity issues:
  What are the consequences of connectivity issues for the project?
- Maintenance mode:
  Is there a maintenance mode that can be set for maintenance of the
  self-hosted service the project depends on?
- Data importance:
  How important is the data conveyed through the self-hosted service?
  Can it be rebuilt if missing and at which cost?
- Data persistence:
  Does the project require the self-hosted service to hold any data
  and to have backup?

## Procedures to be documented

- Start service
- Reload service configuration
- Stop service
- Restart service
- Move service
- Remove service

## Questions that can be answered for each procedure

- Does it risk any data loss? (permissible or not)
- Does it require before/during/after:
  * Announcement of a downtime or a degradation of service to users?
  * Firewall rules?
  * Setup steps?
  * Data dump?
