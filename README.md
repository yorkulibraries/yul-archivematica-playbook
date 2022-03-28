# YUL Archivematica Playbook

## Build

### Staging

1. `ansible-galaxy install -r requirements.yml`
2. `ansible-playbook -i inventory/staging playbook.yml --extra-vars "nodejs_version=10.x"`


