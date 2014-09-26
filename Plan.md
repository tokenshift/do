# Release Plan

## Target Issue Format

### Overview

This target is intended to be used as a guide for development,
and is likely to change with future versions. It is designed to
support backwards-compatibility, so that upgraded versions of **do**
can operate on `.do` files created by previous versions.

### Sections

#### Header

A line of the form

	Issue {number} ({type}, {priority}) - {title}

followed by a line consisting entirely of dashes (the same number of characters
as the line above).

##### Number

Issues are numbered starting at 1.

##### Type

The type of the issue.

* **Bug**  
  A piece of functionality that is not behaving or does not appear as intended.
* **Enhancement**  
  A requested change to an existing piece of functionality.
* **Feature**  
  A new, not-yet-implemented piece of functionality.

##### Priority

The issue priority/severity.

* **Critical**  
  An issue that completely prevents normal functioning of the system, without
  any workaround.
* **High**  
  An issue that prevents some functionality from being usable, with no
  workaround.
* **Medium**  
  Default priority.
* **Low**  
  An issue that does not impact the normal functioning of the system.

##### Title

A short description of the issue.

#### Reporter

	Reported by {user} - {date/time}

The user who created the issue. See the note on Signatures, below, for the
format of the `user`. The date/time that the issue was created is an ISO8601
date/time string.

#### Status

	**{status}** - {tags}

The issue status and a comma-delimited list of tags.

##### Issue Statuses

* **Open**  
  The issue has not yet been addressed.
* **In Progress**  
  The issue is currently being worked on.
* **Closed**  
  The issue has been resolved.

#### Description (optional)

	*{description}*

A complete description of the issue. Can be omitted if the issue title is
sufficient.

#### Comment (zero or more)

A line of the form

	{date/time} - {user}

Where `date/time` is an ISO8601 date/time string and `user` is a signature as
described below; followed by any number of lines containing the comment text.

A comment will absorb all following text until a line indicating the start of a
new comment or a new issue is found. Leading and trailing whitespace around the
comment text will be truncated.

### Signatures

The standard signature combines the user's name, email and URL and is of the
form `[**John Smith**](http://wherever.com/john.smith "John Smith") <John.Smith@wherever.com>`.
These parameters are usually configured in the user's `.doer` file, and at
least one is required in order to add or comment on issues. Expected formats:

* **Full** *(name, email and URL specified)*  
  `[**user's name**](URL) - <email address>`
* **Name and Email**  
  `**user's name** - <email address>`
* **Name and URL**  
  `[**user's name**](URL "user's name")`
* **URL and Email**  
  `[URL] - <email address>`
* **Name only**  
  `**User's name**`
* **URL only**  
  `**[URL]**`
* **Email only**  
  `**<email address>**`

Note that in all cases, the component that is considered to identify the user,
whether that is a name, email address or URL, is bolded. URLs are always turned
into links, and email addresses are always turned into `mailto:` links. 

If a user changes any component of their signature, previous changes they made
*will not* be updated with the new details.

### Example

    Issue 1234 (Bug, High) - Attach the doohickey to the whatsit.
    -------------------------------------------------------------
    Reported by [**John Smith**](http://wherever.com/john.smith "John Smith") <John.Smith@wherever.com> - 2012-10-07T15:16-05:00  
    **In Progress** - whatsit, doohickey, kaleidoscope, depends-on:42

    *The whatsit is missing the contingent doohickey that ensures the fizzbuzz
	 won't kaleidoscope imprecisely.*

    * 2012-10-07T15:17-05:00 - [**John Smith**](http://wherever.com/john.smith "John Smith") <John.Smith@wherever.com>  
      We need to acquire a contingent doohickey. All we currently have are
	  primary doohickeys, which are overpowered for this application.
    * 2012-10-07T15:23-05:00 - [**Jane Doe**]((http://wherever.com/jane.doe "Jane Doe") <Jane.Doe@wherever.com>  
      We have a contingent doohickey, but it's currently attached to the lesser
	  whatchamacallit.
    * 2012-10-07T15:29-05:00 - [**John Smith**](http://wherever.com/john.smith "John Smith") <John.Smith@wherever.com>  
      The lesser whatchamaccalit doesn't technically need a doohickey; can we
	  use it for the whatsit instead?

## Versions

### Note on Numbering

**Do** version numbers consist of three components--major, minor and patch--
separated by periods. Each planned version including new functionality will be
a minor version; bug fixes will increment the patch number. The patch number
may be left off of versions where the patch version is 0. The first (and most
likely only) major release will be `1.0`, and will consist only of bug fixes
and minor enhancements to the previous minor release.


### Plan

#### 0.1 (In Progress)

Issue headers with type and title; default priority.  
`init` command.  
`add` command.  

#### 0.2 (Future)

Options for `init` and `add`: `--path`, `--priority`, `--init`

#### 0.3 (Future)

Configuration settings in `.doer` files.  
Reporter line.  

#### 0.4 (Future)

Issue statuses, and the `set` command (no tags).

#### 0.5 (Future)

`describe` command.  
`show` and `list` commands. Display formats.  
No filter criteria for the `show` command.  

#### 0.6 (Future)

Comments.

#### 0.7 (Future)

Tagging; `tag`, `untag` commands.  
Addition of `--tag`/`--untag` options to `set`, `add` commands.  

#### 0.8 (Future)

Namespaced tags (colons in tags).  
Filter criteria for the `show` command.  
