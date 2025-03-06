```bash
# See what version is available in the repos
apt-cache show nginx

# Install with apt-get package manager
sudo apt-get install nginx

# It will be started by default. Control it with:
sudo systemctl stop nginx
sudo systemctl start nginx
sudo systemctl restart nginx

# View logs with:
journalctl -u nginx

# Get the status with:
sudo systemctl status nginx
```

[more](https://www.mongard.ir/articles/30/what-is-nginx/)
