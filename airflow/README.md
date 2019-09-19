# Airflow helm chart (KubernetesExecutor)

Run Airflow on Kubernetes using the KubernetesExecutor.
With this executor, Airflow creates a new worker pod for each task.
Workers pod are removed as soon as their task is completed.
The deployment is a bit simpler compared to the CeleryExecutor, because no third-party components are needed.
In this way, the full potential of Kubernetes is leveraged.

Since the release of Airflow 1.10.2, the KubernetesExecutor has become stable enough to be used in production.
This repository contains a helm chart to deploy Airflow on Kubernetes with the new executor.
The core structure has been borrowed from [momoshu/kube-airflow](https://github.com/mumoshu/kube-airflow) and
Airflow's [CI scripts](https://github.com/apache/airflow/tree/master/scripts/ci/kubernetes).


## Prerequisites

Before you can run the scripts you need to install
[Helm](https://docs.helm.sh/using_helm/#installing-helm),
[kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/) and
[Docker](https://docs.docker.com/install/).
If you're installing Docker on Ubuntu, then follow the
[post-installation steps](https://docs.docker.com/install/linux/linux-postinstall/)
to be able to run Docker without `sudo`.

## Additional reading

The Docker image is based on the great work of [puckel/docker-airflow](https://github.com/puckel/docker-airflow).
Please refer to this repository if you need to make changes to the docker image.

The Helm chart was based on the [battle-tested chart](https://github.com/mumoshu/kube-airflow) for the CeleryExecutor by momoshu.
I also took a lot of ideas from the [Airflow CI scripts](https://github.com/apache/airflow/tree/master/scripts/ci/kubernetes/kube).

The KubernetesExecutor is explained in greater detail in the [docs](https://airflow.apache.org/kubernetes.html?highlight=kubernetes%20executor)
and Airflow's [confluence page](https://cwiki.apache.org/confluence/pages/viewpage.action?pageId=71013666).

Make sure that you also get familiar with the KubernetesPodOperator, which runs any script on any docker image
as a pod on the Kubernetes cluster. This solves a lot of issues with dependencies and resources.
Check out this [blog post by Kubernetes](https://kubernetes.io/blog/2018/06/28/airflow-on-kubernetes-part-1-a-different-kind-of-operator/)
and this [insightful post](https://medium.com/bluecore-engineering/were-all-using-airflow-wrong-and-how-to-fix-it-a56f14cb0753) by Bluecore
on how we're all using Airflow wrong and how to fix it.


## Contributing

Issues, comments and improvements are always welcome. Fork and PR if you want to contribute :)
