<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Development Guidance](#development-guidance)
  - [Code Structure](#code-structure)
  - [Contributing](#contributing)
    - [Fork the repo](#fork-the-repo)
    - [Clone the Repo](#clone-the-repo)
    - [Cut Branch](#cut-branch)
    - [Update](#update)
    - [Commit](#commit)
    - [Create PR](#create-pr)
    - [Delete Dev Branch](#delete-dev-branch)
    - [Rebase](#rebase)
  - [Testing](#testing)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

<!--
 Copyright 2021 guangyaliu
 
 Licensed under the Apache License, Version 2.0 (the "License");
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at
 
     http://www.apache.org/licenses/LICENSE-2.0
 
 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and
 limitations under the License.
-->

# Development Guidance

This is some guidance for how to contribute to CloudPakOps, here we are using https://github.com/cloud-pak-gitops/instana-gitops as an example.

## Contributing

### Fork the repo

Fork the repo to your own account, in this tutorial, we are using `gyiu513` as the personal account.

### Clone the Repo 

```
git clone git@github.com:gyliu513/instana-gitops.git
cd instana-gitops
git remote add upstream https://github.com/cloud-pak-gitops/instana-gitops
git fetch upstream
git rebase upstream/main
```

### Cut Branch

```
git checkout -b <Your Dev Branch>
```

### Update

Update the logic based on the [Code Structure](#code-structure).

### Commit

```
git add .
git commit -am "Your Commit Message"
git push origin <Your Dev Branch>
```

### Create PR

You can then create a PR from GitHub UI.

### Delete Dev Branch

After your PR got merged, you can delete your dev branch as follows:

```
git checkout main
git branch -D <Your Dev Branch>
```

### Rebase

You may want to rebase your local code to sync up with main branch.

```
git fetch upstream
git rebase upstream/main
```

## Testing

Follow the following guidnace for test with either Kubernetes or OpenShift Cluster, good luck!

- [Using Kubernetes GitOps](./docs/install-instana-with-k8s-gitops.md)
- [Using OpenShift GitOps](./docs/install-instana-with-ocp-gitops.md)
