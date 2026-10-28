# 03 - Jenkins Installation on Ubuntu

## Objective

Install Jenkins on Ubuntu Linux, start the Jenkins service, access the web dashboard, and complete the initial setup.

## Prerequisites

- Ubuntu Linux machine.
- Internet connectivity.
- A user with sudo privileges.
- At least 1 GB RAM for a basic learning setup; more is recommended for builds and additional tools.

## Step 1: Update Ubuntu

Update the package index:

```bash
sudo apt update
```

Upgrade installed packages if needed:

```bash
sudo apt upgrade -y
```

## Step 2: Install Java 21

Jenkins requires a compatible Java runtime.

Install OpenJDK 21:

```bash
sudo apt install fontconfig openjdk-21-jre -y
```

Verify Java:

```bash
java -version
```

Check the installed Java compiler only if you also install a JDK:

```bash
javac -version
```

Note: `javac` may not be available with the JRE-only installation. Jenkins itself does not require you to install a Java compiler just to run the controller.

## Step 3: Add the Official Jenkins Repository

Create a directory for repository signing keys:

```bash
sudo mkdir -p /etc/apt/keyrings
```

Download the Jenkins repository signing key:

```bash
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
```

Add the Jenkins Debian Stable repository:

```bash
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/" \
  | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
```

Update the package index:

```bash
sudo apt update
```

## Step 4: Install Jenkins

Install Jenkins:

```bash
sudo apt install jenkins -y
```

Check the installed version:

```bash
jenkins --version
```

## Step 5: Start Jenkins

Start the Jenkins service:

```bash
sudo systemctl start jenkins
```

Enable Jenkins to start automatically after reboot:

```bash
sudo systemctl enable jenkins
```

Check the service status:

```bash
sudo systemctl status jenkins
```

Look for:

```text
Active: active (running)
```

Press `q` to exit the status screen.

## Step 6: Check Port 8080

Jenkins commonly listens on port 8080 by default.

Check whether a process is listening on that port:

```bash
sudo ss -lntp | grep ':8080'
```

If Jenkins is running, you should normally see a listening socket associated with its Java process.

## Step 7: Retrieve the Initial Administrator Password

Run:

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

Copy the password securely.

You will need it for the initial Jenkins setup wizard.

## Step 8: Open the Jenkins Dashboard

If Jenkins is installed on your local Ubuntu machine, open:

```text
http://localhost:8080
```

If Jenkins is installed on a remote server, use:

```text
http://SERVER_PUBLIC_IP:8080
```

Replace `SERVER_PUBLIC_IP` with your server's actual public IP address.

For an AWS EC2 installation, ensure that the instance's security group and the server firewall permit access as appropriate.

**Security note:** Do not expose Jenkins port 8080 to the entire internet in a production environment. For learning, prefer access from your own IP address or use an SSH tunnel.

## Step 9: Complete the Initial Setup

1. Enter the initial administrator password.
2. Select **Install suggested plugins**.
3. Wait for the installation to finish.
4. Create your first administrator account.
5. Confirm the Jenkins URL.
6. Finish the setup.

You should now see the Jenkins dashboard.

## Step 10: Verify Jenkins

Run:

```bash
sudo systemctl is-active jenkins
```

Expected output:

```text
active
```

Check the service logs if Jenkins does not start:

```bash
sudo journalctl -u jenkins -n 50 --no-pager
```

Follow the logs in real time:

```bash
sudo journalctl -u jenkins -f
```

Press `Ctrl+C` to stop following the logs.

## Common Troubleshooting

### Problem 1: Jenkins Is Not Running

Check:

```bash
sudo systemctl status jenkins
```

Review the logs:

```bash
sudo journalctl -u jenkins -n 100 --no-pager
```

### Problem 2: Port 8080 Is Not Listening

Check:

```bash
sudo ss -lntp | grep ':8080'
```

Check the Jenkins service and logs:

```bash
sudo systemctl status jenkins
sudo journalctl -u jenkins -n 50 --no-pager
```

### Problem 3: Jenkins Webpage Is Not Opening

Check these items:

- Jenkins service is running.
- The URL uses the correct IP address.
- TCP port 8080 is listening.
- The server firewall permits the connection.
- For EC2, the security group allows inbound TCP 8080 from your authorized client IP.

### Problem 4: Java Version Issues

Verify Java:

```bash
java -version
```

If multiple Java versions are installed, check the selected runtime:

```bash
sudo update-alternatives --config java
```

Choose a Java version compatible with your installed Jenkins release.

## Important Paths

| Path | Purpose |
|---|---|
| `/var/lib/jenkins` | Jenkins home directory and data |
| `/var/log/jenkins` | Traditional log location when configured |
| `/etc/default/jenkins` | Legacy package configuration location; not used by every current package setup |
| `/usr/share/java/jenkins.war` | Common WAR file location for Debian package installations |

The actual log location and configuration mechanism can vary by package version. Use `systemctl cat jenkins` and `journalctl -u jenkins` to inspect your installation.

## Hands-On Assignment

Complete these tasks:

- [ ] Install Java.
- [ ] Install Jenkins.
- [ ] Start the Jenkins service.
- [ ] Enable Jenkins at boot.
- [ ] Verify the service status.
- [ ] Check port 8080.
- [ ] Retrieve the initial administrator password.
- [ ] Open the Jenkins dashboard.
- [ ] Install suggested plugins.
- [ ] Create an administrator account.
- [ ] Explain how you would troubleshoot a Jenkins service that fails to start.

## Next Topic

Proceed to [Jenkins Dashboard](../04-jenkins-dashboard/README.md).
