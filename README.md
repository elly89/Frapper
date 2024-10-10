## Initial Server Setup

1. Launch an EC2 instance with Ubuntu 22.04 LTS.
2. Connect to your instance via SSH.
3. Update the system:
   ```
   sudo apt update && sudo apt upgrade -y
   ```

## Installing Frappe

1. Install system dependencies:
   ```
   sudo apt-get install git python3-dev python3-pip redis-server
   ```

2. Install MariaDB:
   ```
   sudo apt-get install software-properties-common
   sudo apt-key adv --fetch-keys 'https://mariadb.org/mariadb_release_signing_key.asc'
   sudo add-apt-repository 'deb [arch=amd64,arm64,ppc64el] https://mariadb.mirror.liquidtelecom.com/repo/10.6/ubuntu jammy main'
   sudo apt update
   sudo apt install mariadb-server
   ```

3. Secure MariaDB installation:
   ```
   sudo mysql_secure_installation
   ```

4. Install Frappe Bench:
   ```
   sudo -H pip3 install frappe-bench
   ```

5. Initialize a new Frappe site:
   ```
   bench init frappe-bench --frappe-branch version-15
   cd frappe-bench
   ```