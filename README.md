# YUL Archivematica Playbook

## Build

### Dev

1. `ansible-galaxy install -r requirements.yml`
2. `vagrant up`

### Production

1. `ansible-galaxy install -r requirements.yml`
2. `ansible-playbook -i inventory/staging playbook.yml --extra-vars "nodejs_version=10.x"`

## Connect

### Dev

* Archivematica: http://localhost:8001
* Storage Service: http://localhost:8000

### Production

* Archivematica:
* Storage Service:
