# Pi-Cluster

## Ansible

- ping: `ansible all -i inventory -m ping`
- disk usage: `ansible all -i inventory -a "df -h"`
- memory usage: `ansible all -i inventory -a "free -m"`
- reboot: `ansible all -i inventory -m shell -a "sleep 1s; shutdown -r now" -b -B 60 -P 0`
- shutdown: `ansible all -i inventory -m shell -a "sleep 1s; shutdown -h now" -b -B 60 -P 0`