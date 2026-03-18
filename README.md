pfsense shell cli "pfctl -d"

apt update
apt install bind9 bind9utils bind9-doc haproxy git -y
apt install software-properties-common -y
add-apt-repository --yes --update ppa:ansible/ansible
apt install ansible -y

ansible-playbook prepare.yaml


ansible-playbook ignition.yaml


cd kube3


https://console.redhat.com/openshift/downloads download pull secret



tarraform init
terraform apply -auto-approve
terraform destroy -auto-aprove


https://cloud.centos.org/centos/scos/9/prod/streams/latest/x86_64/


journalctl -b -u node-image-pull.service



api-int.kube3.okd.piensoluegoinstalo.com:22623



ansible-playbook ignition.yaml


ansible-playbook nfs.yaml


---



kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.14.9/config/manifests/metallb-native.yaml


oc adm policy add-scc-to-group anyuid system:authenticated  -n metallb-system


oc adm policy add-scc-to-user privileged  -z speaker -n metallb-system


oc adm policy add-scc-to-user anyuid controller -n metallb-system


apiVersion: metallb.io/v1beta1
kind: L2Advertisement
metadata:
  name: metallb
  namespace: metallb-system


apiVersion: metallb.io/v1beta1
kind: IPAddressPool
metadata:
  name: defaults-ips
  namespace: metallb-system
spec:
  addresses:
  - 192.168.103.100-192.168.103.150
  autoAssign: true


cat << EOF | oc apply -f -
apiVersion: metallb.io/v1beta1
kind: L2Advertisement
metadata:
  name: metallb
  namespace: metallb-system
EOF


cat << EOF | oc apply -f -
apiVersion: metallb.io/v1beta1
kind: IPAddressPool
metadata:
  name: defaults-ips
  namespace: metallb-system
spec:
  addresses:
  - 192.168.103.100-192.168.103.150
  autoAssign: true
EOF


oc adm policy add-scc-to-user privileged -n metallb-system -z speaker

arping -I ens19 192.168.103.100