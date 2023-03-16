# ocp-preview

Use the `ocp-preview` script to quickly build and deploy openshift-docs HTML previews to a file server. The script picks up the current branch name, generates HTML, creates an output folder on the file server, and then deploys the output. 

Using the `-r, --refresh` option, you can **build and deploy a HTML preview in ~20 seconds**. 

**Prerequisites**

* Fork the https://github.com/openshift/openshift-docs/ repo.
* Install and configure a local asciibinder build.
* Request access to a local Red Hat file share server, for example, `file.emea.redhat.com`, and configure passwordless SSH access to the server.

**Install the script** 

* Copy `ocp-preview` script to `/usr/local/bin`
* `chmod a+x /usr/local/bin/ocp-preview`
* Create a config file: `~/.ocp-preview` and update with your file server config details, for example:

```
[user]
    name = aireilly
[server]
    name = file.emea.redhat.com
[repo]
    name = /home/aireilly/openshift-docs
```

To use the ocp-preview script, open a terminal, change to your `/openshift-docs` folder, and run `ocp-preview` passing the required variables. For example:

```
┌───── ~ 
$ cd ~/openshift-docs

┌───── ~/openshift-docs
$ ocp-preview 
Usage: ocp-preview [OPTION] [DISTRO]
Usage: [DISTRO] is optional, build default is openshift-enterprise. Specify 'all' to build all distros.
-b, --build
               does a full clean build and rsync.
-l, --local-build
               does a full clean build locally, does not rsync.
-r, --refresh
               builds and rsyncs updated files only.
-f, --local-refresh
               builds updated files locally, does not rsync.
-d, --delete
               deletes the current pull request build from the file server.

```
