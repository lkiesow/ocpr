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
