# druid-k8s
Installing Druid on Kubernetes using druid-operator, ansible and helm

Use the following command to install a Druid cluster on Kubernetes using the [druid-operator](https://github.com/druid-io/druid-operator). The helm chart creates a default service account druid-operator. However, change the serviceaccount section in druid-operator values.yaml section to include the service account that is applicable to your cloud environment. 

For e.g., in the case of AWS EKS, create a service account using eksctl and assign a s3 ARN to the service account. This is required for publishing the segments to S3.

```bash
AWS_PROFILE=development ansible-playbook druid_provision.yml --connection=local --user=<username> --extra-vars "chart_base_path=./helm_charts cluster_type=raw kubeconfig_path=<KUBECONFIG_PATH' release_name=druid" -vvv
```
