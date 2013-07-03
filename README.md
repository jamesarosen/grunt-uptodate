# grunt-uptodate

Help Grunt tasks avoid doing unnecessary work

## Concept

Make and its conceptual children like Rake have the idea of "tasks" and "prerequisite tasks."
If a task is a "file task" and the file is *newer* (per `mtime`) than all of its prerequisites,
the build system will not run it. If the file is older, the task can ask the build system which
of the prequisites are newer. This is a great way to avoid doing unnecessary work.

### Examples

A Handlebars task compiles `templates/*.hdbs` files to `compiled_templates/*.js`. Each output file
(e.g. `compiled_templates/foo/bar.js`) has exactly *one* prerequisite (e.g.
`templates/foo/bar.hdbs`). Running the "compile-all" task should only compile those Handlebars files
that have changed since the last time it was run.

A JSHint task could keep an empty "marker file" in the project's `tmp/` directory to indicate
the last time it ran successfully. Running the task only checks those files that have been updated
since the last run.

## Status

This is just a concept right now. You can help by commenting on or adding [issues](https://github.com/jamesarosen/grunt-uptodate/issues).
