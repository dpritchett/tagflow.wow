Circle can trigger workflows on the creation of tags matching specified patterns. 

For instance:
* `built-078fe3`
* `unit-tested-078fe3`
* `integ-tested-078fe3`
* `packaged-078fe3`

This means we can break our pipelines into simpler, more cohesive chunks. 

At the end of a successful build workflow, we should add a tag to denote that completion. 

This tag can trigger the next phase in the release cycle. 

We could consider removing intermediate tags as a commit moves from one phase to the next (e.g. packaged implies integration and unit are done, so we could scrub those at the conclusion of the packaging workflow.

We could also tag the md5sum of an artifact

    Note: Webhook payloads from GitHub are capped at 5MB and for some events a maximum of 3 tags. If you push several tags at once, CircleCI may not receive all of them.
