# Do

File-backed command-line issue tracking.

## Overview

*Do* is a command-line issue and task tracking tool, backed by a single human-
readable text file intended to be checked into a version control repository. It
lets you define and use issue types, statuses, and priorities without leaving
the comfort--and efficiency--of the command line.

## Usage

### init

    do init

Initializes a new **Do** repository. If `path` is specified, the repository
will be created at that location. Otherwise, it is created in the current
directory.


### add

    do add {type} {title}

Creates a new issue with the specified *issue type* and `title`. See Issue
Types for the valid types.

#### Options

* `--init`  
  Create a `.do` file if it does not already exist.
* `-p {priority}`, `--priority {priority}`  
  Sets the priority of the new issue to `priority`.  
  See Priorities for the valid priorities.
* `-t {tag}`, `--tag {tag}`  
  Adds the specified `tag` to the new issue. This option may be specified
  multiple times to add additional tags.

### comment

	do comment {issue number} [comment text]

Adds a comment to an issue specified by issue number. If comment text is
omitted, it will be read from STDIN.

### set

    do set {id} [status]

Sets the status of the specified issue. If *status* is not specified, it will
be left unchanged. In this way, the `set` command can be used to set other
attributes of the issue (see available options, below).

#### Options

* **-p --priority**
* **-t --tag**
* **-u --untag**

### describe

	do describe {issue number} [description]

Sets the description of an issue specified by issue number. If description text
is omitted, it will be read from STDIN.

### tag

    do tag {id} [tags...]

Adds a set of tags to the specified issue. Multiple tags can be added at once.

### untag

    do untag {id} [tags...]

Removes the specified tags from an issue. Multiple tags can be removed at once.

#### Options

* **-a --all**  
  Removes all tags from the issue. If the *all* option is specified, individual
  tags cannot be specified.

### list

	do list [options]

Lists all issues matching the specified criteria.

#### Options

TODO - Filter criteria, display formats.

### show

	do show {issue number}

Displays the specified issue.

#### Options

TODO - Display formats

### Global Options ###

* **-P --path**  
  Process the command in the specified directory, rather than the current
  working directory.

## Configuration

**Do** checks for a configuration file named `.doer` in (1) the current user's
home directory and (2) the location of the current `.do` file. Configuration
settings specified in (2) override those in (1). Settings are key-value pairs
of the form `KEY: VALUE`, where `VALUE` is any text until the end of the line.
The space after the colon is required. Whitespace around the key is ignored.
Keys are not case sensitive.

Recognized configuration settings include:

* **name**  
  The full name of the user.
* **email**  
  The email address of the user.
* **url**  
  A web address for the user.
