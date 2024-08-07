<!-- loio6d9a1b21b0714ddb8273161a496607b6 -->

# Important Notes

-   The creation of a Git repository branch creates a clone of the parent branch. If you create a branch immediately after the release decision, you have a “frozen” state. You can import this state safely into one or multiple production systems, “pre-production” systems, etc., or you may use it later for auditing.
-   In the different system setups, the production systems can either be provisioned once development starts or later on, when needed for the first time for the Go Live, which is the point in time, when the first release is used productively in the production system.
-   A classical 3-system setup comprising a development, quality assurance, and production system can be enhanced by pre-production systems, multiple test systems, etc. Test systems can be provisioned on demand \(temporary\) or permanently.

