# To publish a helm package

Reference: https://medium.com/containerum/how-to-make-and-share-your-own-helm-package-50ae40f6c221

1. From root of repo run `touch index.yaml`
2. Run the following commands:

```
helm dependency update
helm package .
cd ..
helm repo index airflow-kube-helm-dconger/ --url https://dconger.github.io/airflow-kube-helm/
cd airflow-kube-helm-dconger/
git add . && git commit -m "update index yaml"
git push origin master
curl https://dconger.github.io/airflow-kube-helm/index.yaml
```
