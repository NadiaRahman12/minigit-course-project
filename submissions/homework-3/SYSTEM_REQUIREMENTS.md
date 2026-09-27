## Approved UN/UR Baseline

## User needs

| ID | Stakeholder need |
|---|---|
| UN-GIT-01 | A student developer needs a way to start tracking a local project because it has no recorded history. |
| UN-GIT-02 | A student developer needs to know which project files have changed because they may forget what they edited before recording a checkpoint. |
| UN-GIT-03 | A student developer needs to inspect changed content before recording it because a file may contain unintended edits. |
| UN-GIT-04 | A student developer needs to choose the file content to include in the next checkpoint because later edits may still be unfinished. |
| UN-GIT-05 | A student developer needs to record a meaningful checkpoint because they want to preserve a known project state and explain its purpose. |
| UN-GIT-06 | A student developer needs to review earlier checkpoints because they want to understand how the project reached its current state. |
| UN-GIT-07 | A student developer needs invalid commands to explain why they failed while preserving existing project files and recorded checkpoints. |

## User requirements

| ID | User-visible capability | Need |
|---|---|---|
| UR-GIT-01 | A student developer shall be able to initialize tracking in the current local project folder without removing existing project files. | UN-GIT-01, UN-GIT-07 |
| UR-GIT-02 | A student developer shall be able to see whether project files are untracked, staged, changed after staging, modified, deleted, or clean. | UN-GIT-02 |
| UR-GIT-03 | A student developer shall be able to view differences between current working file content and the content selected for the next checkpoint. | UN-GIT-03 |
| UR-GIT-04 | A student developer shall be able to view differences between content selected for the next checkpoint and the latest recorded checkpoint. | UN-GIT-03 |
| UR-GIT-05 | A student developer shall be able to select the current content of one existing project file for the next checkpoint without selecting unrelated files. | UN-GIT-04 |
| UR-GIT-06 | A student developer shall be able to create a checkpoint of selected content with a nonempty explanation while leaving later unselected edits in the working files. | UN-GIT-05, UN-GIT-04 |
| UR-GIT-07 | A student developer shall be able to view recorded checkpoints from newest to oldest, including their identifier and explanation. | UN-GIT-06 |
| UR-GIT-08 | A student developer shall receive a useful error when a command is invalid, a requested file is unavailable, or a path is outside the allowed project files. | UN-GIT-07 |
| UR-GIT-09 | A student developer shall be able to retry an operation after a failure without losing ordinary project files or an already recorded checkpoint. | UN-GIT-07 |



## Functional System Requirements

SR-01 (source UR-GIT-01): Given a project folder that is not initialized and has existing project files, when init is used, MiniGit shall initialize tracking in the current project without removing the existing project files.

Check: A classmate can check that the repository is initialized and the existing files are still present.

SR-02 (source UR-GIT-01): Given an already initialized project with existing files, when init is used again, MiniGit shall keep the project initialized and preserve the existing project state.

Check: A classmate can check that the repository is still initialized and the existing state stays the same.

SR-03 (source UR-GIT-05): Given an initialized project with notes.txt containing ONE and plan.txt present, when add notes.txt is used, MiniGit shall stage a copy of notes.txt containing ONE without staging plan.txt.

Check: A classmate can check that notes.txt is staged with content ONE and plan.txt is not staged.

SR-04 (source UR-GIT-08): Given an initialized project with notes.txt staged with content ONE and missing.txt not present, when add missing.txt is used, MiniGit shall display an error that the file is unavailable and leave the staged notes.txt containing ONE unchanged.

Check: A classmate can check the error and verify that the staged notes.txt still contains ONE.

SR-05 (source UR-GIT-02): Given an initialized project with notes.txt staged, when status is used, MiniGit shall show that notes.txt is staged.

Check: A classmate can check the status output and see that notes.txt is staged.

SR-06(Source UR-GIT-02): Given an initialized project with an untracked file notes.txt and a modified file plan.txt when status is used, Minigit shall show the file states for notes.txt and plan.txt so the student can identify which files are untracked and modified.

Check: A classmate can check the status output and identify notes.txt as untracked and plan.txt as modified.

SR-07 (Source UR-GIT_03): Given an initialized project with notes.txt staged with content ONE and the working copy changed to TWO, when diff is used, Minigit shall show the difference between the working content TWO and the staged content ONE.

Check: A classmate can check the diff output and see the before content ONE and after content TWO.

SR-08 (source UR-GIT-04): Given an initialized project with notes.txt staged with content TWO and the latest checkpoint containing content ONE, when diff --staged is used, MiniGit shall show the difference between the staged content TWO and the latest checkpoint content ONE.

Check: A classmate can check the diff --staged output and see the before content ONE and after content TWO.

SR-09 (source UR-GIT-06): Given an initialized project with notes.txt staged with content TWO and a nonempty commit message, when commit -m "update notes" is used, MiniGit shall create a checkpoint containing the staged content with a nonempty explanation and leave later unselected working edits unchanged.

Check: A classmate can check the recorded checkpoint and verify that the staged content was recorded and a later unselected working edit is still present.

SR-10 (source UR-GIT-07): Given an initialized project with at least two recorded checkpoints, when log is used, MiniGit shall display the checkpoints from newest to oldest with each checkpoint's identifier and explanation.

Check: A classmate can check the log output and verify the order, identifiers and explanations.

SR-11 (source UR-GIT-08): Given an initialized project with an existing recorded checkpoint, when an invalid MiniGit command is used, MiniGit shall display a useful error explaining that the command is invalid and shall preserve the existing project files and recorded checkpoint.

Check: A classmate can check the error message and verify that the project files and earlier checkpoint are still present.

SR-12 (source UR-GIT-09): Given an initialized project with an existing recorded checkpoint and an ordinary project file, when an operation uses a path outside the allowed project files, MiniGit shall report an error and preserve the ordinary project file and recorded checkpoint so the student can retry.

Check: A classmate can check the error and verify that the ordinary project file and recorded checkpoint are unchanged.


