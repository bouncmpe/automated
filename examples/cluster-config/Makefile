requirements:
	ansible-galaxy install -r requirements.yml --force

deploy:
	ansible-playbook deploy.yml

destroy:
	ansible-playbook destroy.yml

users:
	ansible-playbook users.yml -i hosts

vcenter-credentials:
	source vcenter.secret.env
