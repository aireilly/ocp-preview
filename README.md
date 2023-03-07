# ocp-preview

Script to build and deploy openshift docs to a file server.

Prerequisites: 

* Request access to a local Red Hat file share server, for example, `file.emea.redhat.com`, and configure passwordless SSH access to the server.

To install the script: 

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

Using the ocp-preview script:

```
Usage: ocp-preview [OPTION] [DISTRO]
Usage: [DISTRO] is optional, build default is openshift-enterprise. Specify 'all' to build all distros.
-b, --build
               does a full clean build and rsync. Use this option if your PR does not update an assembly.
-r, --refresh
               builds and rsyncs updated assemblies only.
-l, --local-build
               does a full clean build locally, does not rsync. Use this option if your PR does not update an assembly.
-f, --local-refresh
               builds and updated assemblies locally, does not rsync.
-d, --delete
               deletes the current pull request build from the file server.
```
