# Branch Naming Convention

Also see Git Workflow and Management conventions of when and why to branch.

## Naming Pattern

`<author>/<category>-<branch_purpose>`

## Principle

 1. Branch Name Start Name with Category
 2. Use slash (/) to separate `branch_author/branch_name`
 3. Include Author Name in front of the branch
 4. Use lowercase letters only

## Category

- hotfix : changing code with a temporary solution
- bugfix : for fixing a bug
- feature : for adding, refactoring or removing a feature
- docs : for adding or changing documentation
- test : for writing tests outside of an issue
- wip : (rare) for a work in progress (only use for free experimentation)

## Examples

- taylor/hotfix-unable-to-generate-survey
- soumya/bugfix-creating-survey-crashes
- jerry/feature-add-new-survey-chart
- soumya/docs-installation
- tiffany/test-google-oauth-authenticate
- francis/wip-new-complexity-algorithm
