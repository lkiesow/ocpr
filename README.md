# ocpr

A quick Jira ticket and pull request creator for [Opencast
](http://opencast.org).


## Configuration

Create a configuration file `~/.ocpr` to supply your credentials:

```bash
# Jira
USER=jdoe
PASSWORD=...

# Github
GH_REPO=jdoe/opencast
```

Note that this is interpreted as shell script. That means you can easily
integrate your password manager if he supports shell commands. For example you
could use gopass like this:

```bash
PASSWORD="$(gopass show -o private/opencast.jira.com)"
```


## Usage

Just call `ocpr` and answer the questions.

```sh
% ocpr
Using issue type: Bug
Requesting form options…
Summary: Something is broken
Assignee: lkiesow
Allowed components:
  Administrative User Interface
  Backend Software
  ...
  Tests
  Third Party Software
  Workspace Implementation
Component: Tests
...
```

### Automatically create Github pull requests

To create a pull request including the file `somefile.ext` against the `develop`
branch, run the following:

```sh
git checkout develop
# edit somefile.ext
git add somefile.ext
ocpr
```

`ocpr` will automatically use the Jira ticket information for the commit
message, the branch name and the pull request.

### Task vs Bug

By default, `ocpr` will create a Bug-type Jira ticket.
To create a Task instead, run `ocpr -t`.

```sh
% ocpr
Using issue type: Bug
...
```

```
% ocpr -t
Using issue type: Task
...
```

## Example

The following recording shows an example of starting with a patch, creating a
task in Jira, using the data from Jira to commit the patch, push the commit to
your remote repository and finally opening Github's pull request window in your
browser to create a pullrequest:

[![asciicast](https://asciinema.org/a/2wBAC6mRSMfiepvp4iGUznGHT.png)
](https://asciinema.org/a/2wBAC6mRSMfiepvp4iGUznGHT)
