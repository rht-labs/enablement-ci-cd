# Open Innovation Labs Enablement CI/CD Exercise

Repository hosts the Labs Enablement material. It is a working skeleton that learners will use in conjunction with the [enablement-docs](https://github.com/rht-labs/enablement-docs).

### Basic usage

1. Clone this repository.
1. Log on to an OpenShift server `oc login -u <user> https://<server>:<port>/`
1. Install the required [openshift-applier](https://github.com/redhat-cop/openshift-applier) dependency:
```bash
ansible-galaxy install -r requirements.yml --roles-path=roles
```
1. Run the play book using
```bash
ansible-playbook roles/openshift-applier/playbooks/openshift-cluster-seed.yml -i inventory/
```

## Running a Subset of the Inventory

2. See [the docs](https://github.com/redhat-cop/casl-ansible/tree/master/roles/openshift-applier#filtering-content-based-on-tags) in casl-ansible
2. The only required tag to deploy objects within the inventory is **projects**, all other tags are *optional*
2. Here is an example that runs the tags that provision projects, ci, and jenkins objects:
```bash
ansible-playbook roles/openshift-applier/playbooks/openshift-cluster-seed.yml \
     -i inventory/ \
     -e="filter_tags=jenkins,ci,projects"
```
