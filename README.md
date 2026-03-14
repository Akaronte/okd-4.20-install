pfsense shell cli "pfctl -d"

apt update
apt install bind9 bind9utils bind9-doc haproxy git -y
apt install software-properties-common -y
add-apt-repository --yes --update ppa:ansible/ansible
apt install ansible -y


ansible-playbook prepare.yaml


cd kube3


ansible-playbook ignition.yaml


terraform apply -auto-approve


terraform destroy -auto-aproved