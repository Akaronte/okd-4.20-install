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