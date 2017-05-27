1. Clone
```bash
mkdir /docker/ && cd /docker/
git clone https://github.com/night-crawler/docker-registry-portus
```
2. Replace `your.registry.fqdn`
```bash
cd docker-registry-portus
find . -type f -exec sed -i 's/your.registry.fqdn/your.registry.fqdn/g' {} +
```
3. Create certs
```bash
certbot certonly --agree-tos --standalone -d your.registry.fqdn --email admin@registry.fqdn
cp /etc/letsencrypt/live/your.registry.fqdn/* /docker/docker-registry-portus/certs/ 
```
4. Tune mail config in `portus/config-local.yml`
5. Run
```bash
docker-compose up
```

Special thanks https://github.com/Djelibeybi/Portus-On-OracleLinux7

