# nomad_jobs

#файл свойств фабио
mkdir -p /mnt/mycephfs/apps/config/fabio
vi  /mnt/mycephfs/apps/config/fabio/fabio.properties

#конфигурации
ssh bastion
/srv/salt/infrastructure/client/weave

#получение ip адреса не заходя в контейнер
docker exec grafana-d75fc557-7823-fa46-8f7d-19a55c8ddc2d ip addr show | grep -oE "inet [^ ]+"
docker exec prometheus-0a66754f-5c40-3027-0601-7e0b4d5fb87d ip addr show | grep -oE "inet [^ ]+"
