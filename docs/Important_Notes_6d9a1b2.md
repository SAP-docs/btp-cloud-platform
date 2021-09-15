<!-- loio6d9a1b21b0714ddb8273161a496607b6 -->

# Important Notes

-   The creation of a Git repository branch creates a clone of the parent branch. If you create a branch immediately after the release decision, you have a “frozen” state. You can import this state safely into a production ABAP system or multiple production ABAP systems, “pre-production” ABAP systems, etc. or you may use it later for auditing.
-   In the different system setups, the ABAP systems can either be provisioned at once upon development start or just in time when needed for the first time for the Go Live, which is the point in time, when the first release is used productively in the production ABAP system.
-   A classical 3-system setup comprising a development, quality assurance, and production ABAP system can be enhanced by pre-production ABAP systems, multiple test ABAP systems, etc. Test ABAP systems can be provisioned on demand \(temporary\) or permanently.

