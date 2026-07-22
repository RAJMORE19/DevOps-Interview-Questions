# **Linux & System Administration - DevOps Interview Questions**

## **Beginner Level (1-20 Questions)**

### **1. What is Linux and why is it popular in DevOps?**

**Answer:**
Linux is an open-source operating system widely used in DevOps because it is stable, secure, lightweight, and easy to automate using the command line and shell scripting. Most servers, cloud platforms, Docker, and Kubernetes run on Linux, making it the standard OS for DevOps.

### **2. What are the fundamental Linux file permissions?**

**Answer:**
Linux file permissions are Read (r=4), Write (w=2), and Execute (x=1) for Owner, Group, and Others. They are managed using the chmod command, for example, chmod 755 file.

### **3. How do you change file permissions in Linux?**

**Answer:**
Use the chmod command to change file permissions.
Numeric: chmod 755 file
Symbolic: chmod u+x file
It controls Read (r), Write (w), and Execute (x) permissions for the Owner, Group, and Others.

### **4. What is the difference between soft link and hard link in Linux?**

**Answer:**
Hard Link: Shares the same inode as the original file, cannot cross filesystems, and still works if the original file is deleted.
Soft Link (Symbolic Link): Points to the file path, can cross filesystems, and breaks if the original file is deleted. Created using ln -s.

### **5. What is a process in Linux and how do you manage processes?**

**Answer:**
A process is a running program identified by a PID (Process ID). Common commands are:
ps – view processes
top / htop – monitor processes
kill – stop a process
jobs, bg, fg – manage background and foreground processes.

### **6. What is the difference between a daemon and a regular process?**

**Answer:**
A daemon is a background service that starts automatically (e.g., sshd, httpd) and runs without user interaction. A regular process is started by a user, usually runs in the foreground, and ends when its task is complete.

### **7. Explain the Linux directory structure and key directories.**

**Answer:**
Linux follows the Filesystem Hierarchy Standard (FHS) with key directories including:
Key Linux directories:
/ – Root directory
/home – User files
/etc – Configuration files
/var – Logs and variable data
/bin – Essential commands
/usr – Applications and utilities
/tmp – Temporary files
/dev – Device files
/proc – Process and system information

### **8. What are environment variables and how do you set them in Linux?**

**Answer:**
Environment variables store system and user configuration values like PATH, HOME, and USER.
View them using env or echo $VAR. Set them using:
export VAR=value
For permanent changes, add them to ~/.bashrc or /etc/profile.

### **9. What is SSH and how do you use it securely?**

**Answer:**
SSH (Secure Shell) is used for secure remote login and file transfer between systems.
Secure practices:
Use SSH keys (ssh-keygen) instead of passwords
Disable root login
Use strong authentication and restrict users
Connect using: ssh user@hostname

### **10. What is systemd and how do you manage services with it?**

**Answer:**
systemd is a Linux service manager and init system used to control services.
Common commands:
systemctl start/stop/restart service
systemctl status service
systemctl enable service (start at boot)
journalctl -u service (view logs)

### **11. How do you schedule tasks in Linux using cron?**

**Answer:**
Cron is a Linux scheduler used to automate tasks at specific times.
Commands:
crontab -e → Create/Edit jobs
crontab -l → List jobs
crontab -r → Remove jobs
Format: minute hour day month weekday command

Example:
0 2 * * * /backup.sh → Runs backup daily at 2 AM.

### **12. How do you monitor system performance in Linux?**

**Answer:**
Linux performance can be monitored using:
top / htop → CPU and processes
free -h → Memory usage
df -h → Disk space
iostat → Disk I/O
ss → Network monitoring
sar → Historical performance data
For advanced monitoring, use tools like Prometheus and Grafana.

### **13. What is a package manager and how do you use it?**

**Answer:**
A package manager is used to install, update, and remove software in Linux.
Examples:
Ubuntu/Debian: apt
apt update
apt install package
apt upgrade
RHEL/CentOS: yum / dnf
It also manages software dependencies and repositories automatically.

### **14. What is RAID and what are the common RAID levels?**

**Answer:**
RAID combines multiple disks to improve performance and data protection.
Common levels:
RAID 0 → Striping, high performance, no redundancy
RAID 1 → Mirroring, data backup
RAID 5 → Striping with parity
RAID 6 → Double parity
RAID 10 → Mirror + Stripe, high performance and redundancy
Linux software RAID is managed using mdadm.

### **15. What is LVM and why is it useful?**

**Answer:**
LVM (Logical Volume Manager) provides flexible disk management in Linux.
It uses:
PV (Physical Volume) → Disk
VG (Volume Group) → Pool of storage
LV (Logical Volume) → Virtual partition
Benefits:
Resize storage easily
Combine multiple disks
Create snapshots for backup
Manage storage without downtime

### **16. What is the purpose of /etc/fstab file?**

**Answer:**
/etc/fstab is a Linux configuration file used to automatically mount filesystems during boot.
It contains:
Device/UUID
Mount point
Filesystem type
Mount options
Command:
mount -a → Mount all entries from /etc/fstab.

### **17. How do you troubleshoot network connectivity issues in Linux?**

**Answer:**
For Linux network troubleshooting:
ip addr → Check network interface
ping → Test connectivity
ip route → Check routing
nslookup / dig → Check DNS
ss -tulpn → Check ports
tcpdump → Analyze packets
journalctl → Check logs
Check firewall rules if needed.

### **18. How do you set up and configure a basic firewall in Linux?**

**Answer:**
A Linux firewall controls incoming and outgoing network traffic.
Common tools:
UFW (Ubuntu):
ufw allow ssh
ufw enable
firewalld (RHEL/CentOS):
firewall-cmd --add-service=ssh
Always allow SSH before enabling the firewall to avoid lockout.

### **19. What is SELinux and AppArmor? How do they enhance security?**

**Answer:**
SELinux and AppArmor are Linux security modules that provide Mandatory Access Control (MAC).
SELinux → Uses security contexts and policies (common in RHEL)
AppArmor → Uses application profiles (common in Ubuntu)
They restrict process permissions and improve security by preventing unauthorized access.

### **20. How do you manage user accounts and permissions in Linux?**

**Answer:**
Linux user management uses:
useradd / userdel → Create and remove users
passwd → Manage passwords
groupadd → Manage groups
chmod → Change permissions
chown → Change ownership
sudo → Provide admin privileges securely
ACLs can be managed using setfacl and getfacl.

## **Intermediate Level (21-40 Questions)**

### **21. How do you optimize Linux server performance?**

**Answer:**
Linux server performance optimization includes:
Monitor using top, htop, iostat, vmstat
Optimize CPU with nice/renice
Manage memory using swap and vm.swappiness
Improve disk I/O with RAID, SSD, and filesystem tuning
Tune network and kernel parameters using sysctl
Regular monitoring helps identify and fix bottlenecks.

### **22. How do you implement centralized logging in a Linux environment?**

**Answer:**
Centralized logging collects logs from multiple servers into one location for monitoring and troubleshooting.
Common tools:
ELK Stack → Elasticsearch, Logstash, Kibana + Filebeat
rsyslog → Forward logs to a central server
Benefits:

Easy log analysis
Better troubleshooting
Security and compliance monitoring
Log retention management

### **23. How do you implement backup and recovery strategies for Linux systems?**

**Answer:**
Linux backup strategies include:
rsync → File backups
tar → Archive backups
dd → Disk imaging
mysqldump / pg_dump → Database backups
Best practices:

Automate with cron
Follow 3-2-1 backup rule
Encrypt backups
Regularly test recovery procedures.

### **24. How do you secure a Linux server?**

**Answer:**
To secure a Linux server:
Keep the system updated with security patches
Use SSH keys, disable root login
Configure firewall (UFW/firewalld)
Apply least privilege with sudo
Enable SELinux/AppArmor
Monitor logs and use tools like fail2ban for protection.

### **25. How do you manage kernel parameters and modules in Linux?**

**Answer:**
Kernel parameters control Linux kernel behavior and are managed using:

sysctl -a → View parameters
sysctl -w → Temporary changes
/etc/sysctl.conf → Permanent changes
Kernel modules are managed with:

lsmod → List modules
modprobe → Load modules
rmmod → Remove modules
/etc/modules → Load modules at boot.

### **26. How do you troubleshoot high CPU, memory, or disk I/O usage in Linux?**

**Answer:**
To troubleshoot high resource usage:
CPU: top, htop, ps aux --sort=-%cpu
Memory: free -h, vmstat, ps aux --sort=-%mem
Disk I/O: iostat, iotop, df, du
Identify the process causing the issue and optimize or adjust resources.

### **27. What is load balancing and how do you implement it in Linux?**

**Answer:**
Load balancing distributes traffic across multiple servers to improve performance and availability.
Common Linux tools:
HAProxy / Nginx → Application-level load balancing
LVS + Keepalived → High-performance and high availability
Methods include:

Round-robin
Least connections
Health checks
Automatic failover using VRRP.

### **28. What is containerization and how do you use containers in Linux?**

**Answer:**
Containerization packages applications with their dependencies into lightweight containers.
In Linux, Docker is commonly used:
docker pull → Download images
docker run → Start containers
docker ps → List containers
docker build → Create images
Kubernetes is used for container orchestration, scaling, and management.

### **29. How do you implement configuration management in Linux environments?**

**Answer:**
Configuration management automates and maintains consistent server configurations.
Popular tools:
Ansible → Agentless, uses SSH and YAML
Puppet / Chef / SaltStack → Automation tools
Ansible uses:

Inventory file → Define servers
Playbooks → Automate tasks
Command: ansible-playbook playbook.yml
Benefits:

Reduces configuration drift
Enables faster and consistent deployments.

### **30. What is Software RAID and how do you implement it in Linux?**

**Answer:**
Software RAID provides disk redundancy and performance using Linux kernel RAID with mdadm.
Common levels:
RAID 1 → Mirroring
RAID 5 → Striping with parity
RAID 10 → Performance + redundancy
Commands:

mdadm --create → Create RAID
cat /proc/mdstat → Check RAID status
mdadm --detail → View details.

### **31. How do you manage disk quotas in Linux?**

**Answer:**
Linux disk quotas limit disk usage for users or groups.
Steps:
Enable quotas in /etc/fstab using usrquota,grpquota
Create quota files: quotacheck
Enable quotas: quotaon
Set limits: edquota
Check usage: repquota
It prevents users from consuming excessive disk space.

### **32. What is systemd-networkd and how do you configure networking with it?**

**Answer:**
systemd-networkd manages Linux network configuration using systemd.
Configuration files:
Location: /etc/systemd/network/
Static IP or DHCP settings are defined in .network files
Commands:
systemctl enable --now systemd-networkd
systemctl restart systemd-networkd
Used for modern Linux network management.

### **33. What are Linux namespaces and how are they used?**

**Answer:**
Linux namespaces provide resource isolation for processes and are the foundation of containers like Docker.
Types:
PID → Process isolation
NET → Network isolation
MNT → Filesystem isolation
USER → User ID isolation
Commands:
unshare → Create namespaces
nsenter → Enter namespaces
They provide lightweight virtualization without a full VM.

### **34. How do you implement disk encryption in Linux?**

**Answer:**
Linux disk encryption protects data using LUKS (Linux Unified Key Setup).
Tool:
cryptsetup → Create and manage encrypted volumes
Common commands:
cryptsetup luksFormat → Encrypt disk
cryptsetup luksOpen → Open encrypted volume
Use /etc/crypttab and /etc/fstab for automatic mounting.

### **35. What is systemd-journald and how do you use it for system logging?**

**Answer:**
systemd-journald is a Linux service that collects and manages system logs in a structured format.
Common commands:
journalctl → View logs
journalctl -u service → Service logs
journalctl -b → Current boot logs
journalctl -f → Live log monitoring
Configuration file: /etc/systemd/journald.conf.

### **36. How do you manage system time and NTP in Linux?**

**Answer:**
Linux time synchronization is managed using NTP services like systemd-timesyncd or chrony.
Commands:
timedatectl status → Check time status
timedatectl set-timezone → Set timezone
timedatectl set-ntp true → Enable NTP
chronyc tracking → Check synchronization
Accurate time is important for logs, security, and distributed systems.

### **37. What is Linux resource management with cgroups?**

**Answer:**
cgroups (Control Groups) manage and limit Linux resource usage for processes.
They control:
CPU
Memory
Disk I/O
Network resources
Commands:
systemd-cgls → View cgroup hierarchy
systemd-cgtop → Monitor usage
Used by Docker and Kubernetes for container resource limits.

### **38. How do you optimize Linux for database servers?**

**Answer:**
To optimize Linux for database servers:
Tune kernel parameters (sysctl)
Reduce swapping with vm.swappiness
Optimize disk I/O and use suitable RAID (RAID 10)
Use filesystem options like noatime
Increase file limits and configure memory properly
Use CPU affinity/cgroups for resource control
Goal: improve performance and stability.

### **39. What is Linux Traffic Control (tc) and how is it used?**

**Answer:**
Linux Traffic Control (tc) manages network traffic using QoS, shaping, and bandwidth control.
Uses:
Limit bandwidth
Prioritize important traffic
Reduce network latency
Manage traffic queues
Command example:
tc qdisc add dev eth0 ...

It helps optimize network performance and resource usage.

### **40. How do you implement high availability for Linux servers?**

**Answer:**
High Availability (HA) keeps Linux services running during failures.

Common tools:

Pacemaker + Corosync → Cluster management
HAProxy/Nginx → Load balancing
DRBD → Data replication
Galera/Patroni → Database HA
Key features:
Automatic failover
Resource monitoring
Failover testing to ensure reliability.




## **Advanced Level (41-60 Questions)**

### **41. How do you implement Linux network bonding and teaming?**

**Answer:**
Network bonding/teaming combines multiple network interfaces into one logical interface for high availability and increased bandwidth.

Common modes:

Active-Backup → Failover protection
LACP (802.3ad) → Load balancing + redundancy
Commands:

cat /proc/net/bonding/bond0 → Check bonding status
teamdctl team0 state → Check teaming status
Used to improve network reliability and performance.

### **42. How do you configure and troubleshoot IPtables firewall?**

**Answer:**
iptables is a Linux firewall used to filter and control network traffic.

Key chains:

INPUT → Incoming traffic
OUTPUT → Outgoing traffic
FORWARD → Routed traffic
Common commands:

iptables -L -v -n → View rules
iptables -A INPUT -p tcp --dport 22 -j ACCEPT → Allow SSH
iptables-save → Save rules
Troubleshoot using logs, rule counters, and connectivity tests.

### **43. How do you implement and manage SELinux policies?**

**Answer:**
SELinux provides Mandatory Access Control (MAC) to secure Linux systems.
Commands:
sestatus → Check SELinux status
setenforce 1 → Enable enforcing mode
semanage → Manage contexts and policies
restorecon → Restore file contexts
ausearch -m AVC → Check SELinux denials
It restricts processes and prevents unauthorized access.

### **44. How do you manage and monitor system logs effectively?**

**Answer:**
Effective Linux log management includes:

rsyslog / journald → Collect logs
logrotate → Rotate and compress old logs
ELK / Graylog → Centralized log analysis
Fail2ban → Detect suspicious activity
Best practices:

Monitor critical events
Set alerts
Maintain proper log retention and security.

### **45. How do you implement disk quotas in Linux?**

**Answer:**
Disk quotas limit storage usage for users and groups.
Steps:
Enable quotas in /etc/fstab using usrquota,grpquota
Run quotacheck to create quota files
Enable with quotaon
Set limits using edquota
Check usage with repquota
It prevents users from consuming all available disk space.

### **46. How do you implement and manage RAID in Linux?**

**Answer:**
RAID in Linux provides data redundancy and performance improvement using hardware RAID or software RAID with mdadm.

Common levels:

RAID 0 → Performance, no redundancy
RAID 1 → Mirroring
RAID 5/6 → Parity-based protection
RAID 10 → Performance + redundancy
Commands:

mdadm --create → Create RAID
cat /proc/mdstat → Monitor RAID
mdadm --detail → Check status
RAID improves availability but is not a replacement for backups.

### **47. How do you manage and troubleshoot systemd services?**

**Answer:**
systemd manages Linux services and startup processes.

Common commands:

systemctl start/stop/restart service → Manage services
systemctl status service → Check status
systemctl enable service → Start at boot
journalctl -u service → View service logs
systemctl daemon-reload → Reload configuration
Troubleshoot using status, logs, and unit file checks.

### **48. How do you configure and optimize Linux for database servers?**

**Answer:**
To optimize Linux for database servers:

Tune kernel parameters (sysctl)
Reduce swapping using vm.swappiness
Allocate proper memory and huge pages
Optimize storage with RAID 10, XFS, and noatime
Increase file/process limits
Use CPU affinity and cgroups for resource control
Monitor performance regularly
Goal: achieve better database speed, stability, and reliability.

### **49. How do you implement and maintain LVM (Logical Volume Management)?**

**Answer:**
LVM (Logical Volume Manager) provides flexible disk management using:

PV (Physical Volume) → Disk
VG (Volume Group) → Storage pool
LV (Logical Volume) → Virtual partition
Common commands:

pvcreate, vgcreate, lvcreate → Create LVM
lvextend → Increase volume size
resize2fs / xfs_growfs → Resize filesystem
lvs, vgs, pvs → Monitor LVM
Benefits:

Easy resizing
Snapshots
Disk expansion without downtime.

### **50. What is Linux Containers (LXC) and how do they differ from Docker?**

**Answer:**
LXC (Linux Containers) provides lightweight OS-level virtualization using namespaces and cgroups.

Difference:

LXC → Runs full Linux containers, similar to lightweight VMs
Docker → Focuses on application containers and microservices
Docker provides extra tools like:

Images
Dockerfiles
Container registry
Easy CI/CD integration
LXC is used for system containers, while Docker is common in DevOps deployments.

### **51. How do you implement and manage KVM virtualization?**

**Answer:**
KVM (Kernel-based Virtual Machine) is a Linux virtualization technology that runs multiple VMs on one host.

Components:

QEMU → Hardware emulation
libvirt → VM management
virsh / virt-manager → Administration tools
Common commands:

virt-install → Create VMs
virsh list → View VMs
virsh start/stop → Manage VMs
Optimization:

Use virtio drivers
Configure CPU, memory, and storage properly
Monitor VM performance regularly.

### **52. How do you implement and configure Linux kernel hardening?**

**Answer:**
5-second interview version:

Linux kernel hardening improves security by reducing attack surfaces and preventing exploits.

Key steps:

Apply regular kernel security patches
Harden parameters using sysctl
Enable SELinux/AppArmor
Restrict kernel modules and access
Use auditd and security monitoring tools
Goal: protect the kernel from unauthorized access and vulnerabilities.

### **53. How do you troubleshoot Linux boot problems?**

**Answer:**
Linux boot troubleshooting follows the boot stages:

Check hardware and BIOS/UEFI
Check GRUB bootloader
Check kernel and initramfs logs
Use journalctl -xb for systemd errors
Check failed services: systemctl list-units --failed
Repair filesystem using fsck
Common tools:

dmesg → Kernel messages
systemd-analyze → Boot performance analysis
Rescue mode/live USB for recovery.

### **54. How do you manage Linux kernel modules?**

**Answer:**
Linux kernel modules extend kernel functionality without rebooting.

Commands:

lsmod → List loaded modules
modinfo → Module details
modprobe → Load modules
rmmod → Remove modules
Configuration:

/etc/modules → Load at boot
/etc/modprobe.d/ → Configure or blacklist modules
Used for hardware drivers and kernel features.

### **55. How do you implement and manage user authentication with LDAP?**

**Answer:**
LDAP provides centralized user authentication and directory management for Linux systems.

Components:

LDAP Server → Stores users and groups
LDAP Client → Authenticates users using PAM/NSS
Configuration:

Update /etc/nsswitch.conf
Configure PAM for LDAP
Use TLS/SSL for secure communication
Commands:

getent passwd username → Test LDAP users
id username → Verify user details
Used for centralized login management.

### **56. How do you implement and manage DRBD (Distributed Replicated Block Device)?**

**Answer:**
DRBD (Distributed Replicated Block Device) provides block-level storage replication between Linux servers for high availability.

Key points:

Works like network-based RAID 1
Replicates data between nodes
Managed using drbdadm
Commands:

drbdadm create-md → Create metadata
drbdadm up → Start resource
drbdadm status → Check status
cat /proc/drbd → Monitor sync
Usually combined with Pacemaker/Corosync for automatic failover.

### **57. How do you configure and manage syslog in Linux?**

**Answer:**
Syslog is a Linux logging system used to collect, filter, and store system/application logs.

Common tools:

rsyslog / syslog-ng → Manage logs
/etc/rsyslog.conf → Configuration file
/etc/rsyslog.d/ → Additional rules
logrotate → Manage log files
Remote logging:

@server:514 → UDP
@@server:514 → TCP
Used for centralized logging and troubleshooting.

### **58. How do you configure and manage DNS server (BIND) in Linux?**

**Answer:**
BIND is a Linux DNS server used for domain name resolution.

Key files:

/etc/named.conf or /etc/bind/ → Configuration
Zone files → Store DNS records
Common records:

A → IPv4 address
AAAA → IPv6 address
MX → Mail server
CNAME → Alias
Commands:

systemctl restart bind9/named → Restart DNS service
rndc → Manage BIND runtime settings
Security:

Restrict zone transfers
Use DNSSEC for secure DNS.

### **59. How do you implement and manage High Availability clustering in Linux?**

**Answer:**
Linux HA clustering keeps services available by using multiple nodes with automatic failover.

Main components:

Pacemaker → Resource management
Corosync → Cluster communication
STONITH/Fencing → Prevent split-brain
Common resources:

Virtual IP
Applications
Databases
Storage
Commands:

pcs status → Check cluster status
crm_mon → Monitor cluster
Benefits:

High availability
Automatic failover
Reduced downtime.




### **60. How do you implement and manage Linux Virtual Server (LVS) for load balancing?**

**Answer:**
LVS (Linux Virtual Server) is a high-performance Linux load balancing solution using the IPVS kernel module.

Components:

Director → Distributes client traffic
Real Servers → Handle requests
VIP (Virtual IP) → Client access point
Forwarding methods:

DR (Direct Routing) → High performance
NAT → Address translation
IP Tunnel → Remote servers
Commands:

ipvsadm -L -n → Check LVS status
For high availability, use Keepalived with LVS for automatic failover.

---

## **📢 Contribute & Stay Updated**  

💡 **Want to contribute?**  
We **welcome contributions!** If you have insights, new tools, or improvements, feel free to submit a **pull request**.  

📌 **How to Contribute?**

- Read the **[CONTRIBUTING.md](https://github.com/NotHarshhaa/DevOps-Interview-Questions/blob/master/CONTRIBUTING.md)** guide.  
- Fix errors, add missing topics, or suggest improvements.  
- Submit a **pull request** with your updates.  

📢 **Stay Updated:**  
⭐ **Star the repository** to get notified about new updates and additions.  
💬 **Join discussions** in **[GitHub Issues](https://github.com/NotHarshhaa/DevOps-Interview-Questions/issues)** to suggest improvements.  

---

## **🌍 Community & Support**  

🔗 **GitHub:** [@NotHarshhaa](https://github.com/NotHarshhaa)  
📝 **Blog:** [ProDevOpsGuy](https://blog.prodevopsguy.xyz)  
💬 **Telegram Community:** [Join Here](https://t.me/prodevopsguy)  

![Follow Me](https://imgur.com/2j7GSPs.png)
