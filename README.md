# YUL Archivematica Playbook

## Build

### Dev

1. `ansible-galaxy install -r requirements.yml`
2. `vagrant up`

### Production

1. `ansible-galaxy install -r requirements.yml`
2. `ansible-playbook --ask-vault-pass -i inventory/production playbook.yml`

## Connect

### Dev

* Archivematica: http://localhost:8001
* Storage Service: http://localhost:8000

### Production

* Archivematica: http://archivematica.library.yorku.ca
* Storage Service: http://vault.library.yorku.ca
