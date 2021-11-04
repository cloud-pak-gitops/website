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

# Code Structure

The code structure is taking https://github.com/cloud-pak-gitops/instana-gitops as an example.

- For the Instana GitOps Repo, we are using [App of Apps Pattern](https://argo-cd.readthedocs.io/en/stable/operator-manual/cluster-bootstrapping/#app-of-apps-pattern).
- Both the Argo CD Application and the Instances managed by Argo CD are wrapped in [Helm Charts](https://argo-cd.readthedocs.io/en/stable/user-guide/helm/).

```
.
├── config
    ├── argocd-apps
    │   ├── Chart.yaml
    │   ├── templates
    │   │   ├── crossplane-app.yaml
    │   │   └── crossplane-provider-app.yaml
    │   └── values.yaml
    ├── crossplane-provider
    │   ├── Chart.yaml
    │   ├── templates
    │   │   ├── clusterrolebinding.yaml
    │   │   ├── init
    │   │   │   ├── 00-crossplane-ns.yaml
    │   │   │   └── 99-postsync-job.yaml
    │   │   └── instana-provider
    │   │       ├── config.yaml
    │   │       ├── crds
    │   │       │   ├── instana.crossplane.io_instanas.yaml
    │   │       │   ├── instana.crossplane.io_providerconfigs.yaml
    │   │       │   └── instana.crossplane.io_providerconfigusages.yaml
    │   │       └── deployment.yaml
    │   └── values.yaml
    └── instana
        ├── Chart.yaml
        ├── templates
        │   ├── 99-postsync-job.yaml
        │   └── instana.yaml
        └── values.yaml
```

The application in `argocd-apps` folder will bring up the following instances in order as:
- Crossplane
- Crossplane Instana Provider
