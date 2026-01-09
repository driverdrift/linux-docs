Some vps companies don't permit user to mount customized iso, therefore transfer the rescue-mode-os to a install-iso-os is essential for concern about the preinstalled os.

Sometimes the rescue-mode-os is too outdated to run `apt update`, so change the apt source to the archieved edition (not the newest, as its architecture may not be applicable ).
```sh
cat /etc/debian_version
```
For debian 9, replace to the archieved source, then allow unsecure:
```
cat > /etc/apt/sources.list << 'EOF'
deb http://archive.debian.org/debian/ stretch main contrib non-free
deb http://archive.debian.org/debian-security/ stretch/updates main contrib non-free
EOF

echo 'Acquire::Check-Valid-Until "false";' > /etc/apt/apt.conf.d/99no-check-valid
echo 'APT::Get::AllowUnauthenticated "true";' > /etc/apt/apt.conf.d/99allow-unauth

apt update -o Acquire::AllowInsecureRepositories=true -o APT::Get::AllowUnauthenticated=true
apt install wget -y

```
