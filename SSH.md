## SSH

```bash
ssh root@dev-as.main.brutex.com

# Authenticate with AWS SSO
aws sso login --profile common

cd helm-whs/
mc
cd whs
./changeToDev.sh
./cleanupDev.sh
./startDev.sh dev-as

watch "kubectl get pods"
kubectl get pods
./klogs

# Restore to Initial Snapshot
cd whs-test/
./restore.sh
cd
cd helm-whs/
cd whs/
./cleanupDev.sh
./startDev.sh dev-as
```
