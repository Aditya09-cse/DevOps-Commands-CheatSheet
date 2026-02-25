# 🚀 90 Days of DevOps -- Phase 1 Advanced Command Cheat Sheet

**Author: Aditya Singh Tomar**

This cheat sheet is enhanced with practical explanations and real usage
examples so beginners understand not just the command --- but how and
when to use it.

------------------------------------------------------------------------

# 🐧 LINUX COMMANDS (Practical Usage Guide)

## 📁 File & Directory Management

### `pwd`

Shows your current working directory (where you are in the system).

``` bash
pwd
```

Use this when you are unsure of your current location.

### `ls`

Lists files and directories.

``` bash
ls
ls -l      # detailed view
ls -la     # include hidden files
ls -lh     # human-readable sizes
```

Use `-la` when troubleshooting configuration files (hidden files start
with `.`).

### `cd`

Changes directory.

``` bash
cd /var/log
cd ..
cd ~
```

Use `cd ..` to move one level up.

### `mkdir`

Creates a directory.

``` bash
mkdir project
mkdir -p project/src/app
```

Use `-p` to create nested directories.

### `rm`

Deletes files or folders.

``` bash
rm file.txt
rm -r folder
rm -rf folder
```

⚠️ `-rf` force deletes --- be very careful.

------------------------------------------------------------------------

## 📄 Viewing & Searching Files

### `cat`

Displays file content.

``` bash
cat file.txt
```

### `less`

Opens file page-by-page (better for large logs).

``` bash
less /var/log/syslog
```

### `tail -f`

Monitors logs in real-time.

``` bash
tail -f /var/log/nginx/access.log
```

Very useful for debugging applications.

### `grep`

Searches for text inside files.

``` bash
grep "error" logfile.log
grep -i "failed" logfile.log
```

Use `-i` for case-insensitive search.

------------------------------------------------------------------------

## 👤 User & Permission Management

``` bash
whoami                  # Current user
id                      # User ID info
sudo su                 # Switch to root
useradd devops
passwd devops
chmod 755 script.sh     # Give execution permission
chown user:group file
```

`755` means: - Owner: full permission - Group: read & execute - Others:
read & execute

------------------------------------------------------------------------

## ⚙️ Process Management

``` bash
ps aux
top
htop
kill PID
kill -9 PID
pkill nginx
```

Use `top` to monitor CPU & memory usage live.

------------------------------------------------------------------------

## 💾 Disk & Storage

``` bash
lsblk
df -h
du -sh folder
mount /dev/xvdf /mnt/data
umount /dev/xvdf
mount -a
```

`df -h` → Check disk space before deploying large applications.

------------------------------------------------------------------------

# 🌐 NETWORKING COMMANDS (How to Use)

### `ip a`

Shows IP addresses assigned to your machine.

``` bash
ip a
```

### `ping`

Tests network connectivity to another host.

``` bash
ping google.com
ping -c 4 google.com
```

Use `-c 4` to send only 4 packets instead of continuous ping.

### `curl`

Fetch data from a URL (great for API testing).

``` bash
curl http://example.com
curl -I http://example.com   # Check headers only
```

### `wget`

Download files.

``` bash
wget https://example.com/file.zip
```

### `ss -tulnp`

Check open ports and services.

``` bash
ss -tulnp
```

Useful when verifying if an app is running on expected port.

------------------------------------------------------------------------

# 🖥 SHELL SCRIPTING

### Basic Script

``` bash
#!/bin/bash
echo "Hello DevOps"
```

### Variables

``` bash
name="Aditya"
echo $name
```

### User Input

``` bash
read username
echo "Welcome $username"
```

### Conditions

``` bash
if [ 10 -gt 5 ]; then
  echo "True"
else
  echo "False"
fi
```

### Loops

``` bash
for i in {1..3}; do
  echo $i
done
```

------------------------------------------------------------------------

# 🔁 GIT & GITHUB (Real Workflow)

``` bash
git init
git clone repo_url
git status
git add .
git commit -m "Added feature"
git log
git branch
git checkout -b new-feature
git merge new-feature
git pull origin main
git push origin main
git stash
git reset --soft HEAD~1
```

Typical workflow: 1. Create branch 2. Add changes 3. Commit 4. Push 5.
Merge

------------------------------------------------------------------------

# 🐳 DOCKER (Complete Lifecycle)

### Pull Image

``` bash
docker pull nginx
```

### Run Container

``` bash
docker run -d -p 80:80 nginx
```

Maps port 80 of container to port 80 of host.

### View Running Containers

``` bash
docker ps
docker ps -a
```

### Check Logs

``` bash
docker logs container_id
```

### Enter Container

``` bash
docker exec -it container_id /bin/bash
```

### Build Image

``` bash
docker build -t myapp .
```

### Remove Containers & Images

``` bash
docker stop container_id
docker rm container_id
docker rmi image_id
```

------------------------------------------------------------------------

# 💾 LVM (Storage Management)

### Check Existing LVM

``` bash
pvs
vgs
lvs
```

### Create Physical Volume

``` bash
pvcreate /dev/xvdg
```

### Create Volume Group

``` bash
vgcreate devops-vg /dev/xvdg
```

### Create Logical Volume

``` bash
lvcreate -L 1G -n app-data devops-vg
```

### Format & Mount

``` bash
mkfs.ext4 /dev/devops-vg/app-data
mount /dev/devops-vg/app-data /mnt/app-data
```

### Extend Volume

``` bash
lvextend -L +1G /dev/devops-vg/app-data
resize2fs /dev/devops-vg/app-data
```

Always update `/etc/fstab` for permanent mount.

------------------------------------------------------------------------

# 🎯 End of Enhanced Phase 1 Cheat Sheet

Keep learning. Keep building. Keep shipping.
