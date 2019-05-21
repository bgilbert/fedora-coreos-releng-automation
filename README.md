# coreos-koji-tagger

Source code that monitors a git repo and tags packages over into
appropriate koji tags to be consumed by Fedora CoreOS build processes.

# Rough notes for deployment

Create a new project and build the container.

```
oc new-project coreos-koji-tagger
oc new-build --strategy=docker https://pagure.io/releng/compose-tracker --to coreos-koji-tagger-img
```

Export pagure token to use as an env var and then use kedge to
get up and running in openshift:

```
export PAGURE_TOKEN=$(echo -n <pagure_token> | base64 -w 0)
kedge apply -f kedge.yaml
```
