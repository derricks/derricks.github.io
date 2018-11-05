# Code Review Checklist
Generated from [my code review checklist](https://github.com/derricks/code-review-checklist-plugin)

   * Commit messages conform to standards
   * Code conforms to the style of the code around it, regardless of a linter's view
    ## Code comprehension

      #### Names

       * All names are descriptive
       * Names and comments do not include spelling mistakes
       * Items that define amounts encode the unit of measurement
       * Names do not use negatives
       * In dynamic languages, types are encoded in argument names
       * Names that are changing are changed everywhere in the code base

     * Methods either do one thing or orchestrate other methods
     * Methods neither define nor use ambiguous booleans
     * Complex boolean checks are moved to methods that describe the total effect
     * Data is immutable wherever possible
     * Streams are closed by the same code that opens them
     * Constants are namespaced appropriately
     * Overly branched code is broken into methods
     * Methods are small enough to be easily grasped
     * Regexes are commented with information about what they do

    ## Defensive coding

     * Public methods check the validity of all their arguments at the beginning of the method
     * Switch statements or if/else blocks always handle the default case
     * All arguments passed to functions are either used or prefixed with underscore
     * Microclones don't have bugs in their last lines
     * Code dependencies are pinned to specific versions for production code
     * Mutable data shared across threads is protected from concurrent modifications
     * Public methods do not let mutable copies of state data escape
     * Any waits on threads or processes are guarded with a timeout
     * Waiting for some event to happen is done with a conditional rather than a simple sleep
     * Possible errors are handled or are passed back to the client with useful context
     * Exceptions do not die silently
     * Code does not assume temp files are around even for the life of the code that uses them
     * Recursive functions define an end state that is reached within a reasonable time
     * Code is backwards compatible with existing clients
     * Code that receives events from another system also has a periodic refresh

    ## Tests

     * There are tests
     * Every exit path from the code under test has a test case
     * Tests test the right thing
     * There are no obvious bugs in the tests

    ## Code Maintainability

     * No code is commented out
     * Todos in the code are tracked
     * Todos are removed when they're done
     * Function arguments are not themselves calls to other functions
     * Any magic numbers have been placed into constants or config parameters
     * Unused variables or methods have been deleted

    ## Calling Other Services

     * Open connections are closed in the same place
     * Calls to remote services at a minimum have a timeout
     * Retries are done as exponential backoff with jitter
     * Implications of caches going away are considered
     * Connections are pooled to prevent overwhelming upstream services

    ## Productionization

     * Performance changes are understood for this change
     * Metrics are in place for the change
     * Storage has a retention plan
     * Feature flags are set appropriately
     * Configuration files spell out every option rather than relying on defaults
     * No paths point to user-specific directories or anything else that only exists on one machine
     * Emails for notifications are aliases, not specific users
     * Rolling back this change is well understood and documented
     * A health check exists and incorporates the health of systems the program depends on
     * Limits, thresholds, and other constraints can be tuned via config files or environment variables
     * Query results are limited either with a LIMIT clause or in code
     * Files that are opened are closed directly (rather than trusting garbage collection and destructors)

    ## Java Specifics

     * Needless boxing and unboxing is removed

    ## Configuration Management Specifics

     * Files managed by configuration management have a comment saying that
     * Terraform resources specify useful outputs for users of the system
     * Literals in terraform modules make sense

    ## Synchronization Program Specifics

     * Configurable guard conditions prevent catastrophic changes

    ## ETL Specifics

     * Bulk load logic has checkpoints it can restart from
     * Duplicate data either can't exist or its implications are well understood


