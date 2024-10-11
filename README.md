## Initial Server Setup

1. Launch an EC2 instance with Ubuntu 22.04 LTS.
    -  Hardware Requirements
      1.  4GB RAM
      2.  40GB Hard Disk
2. Connect to your instance via SSH.
3. Update the system:
   ```
   sudo apt update && sudo apt upgrade -y
   ```

## Installing Frapper

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

## Configuring Frapper

1. Create a new site:
   ```
   bench new-site <site-name>
   ```

2. Set the site as default:
   ```
   bench use <site-name>
   ```

3. Install ERPNext app:
   ```
   bench get-app --branch version-15 erpnext
   bench --site <site-name> install-app erpnext
   ```

4. Start the Frappe server:
   ```
   bench start
   ```


   ## Installing Additional Modules

1. Install the Payment module:
   ```
   bench get-app payments
   bench --site <site-name> install-app payments
   ```

2. Install the HRMS module:
   ```
   bench get-app hrms
   bench --site <site-name> install-app hrms
   ```

## Accessing and Managing Modules

1. Access the Frappe/ERPNext web interface by navigating to `http://ec2-instance-ip:8000` in the web browser.
2. Log in with the admin credentials you created.
3. To manage user permissions:
   - Go to "User" doctype
   - Select a user
   - Scroll down to "Roles" section
   - Add or remove roles as needed

## Troubleshooting

- If you encounter any issues, check the Frappe log files located in `~/frappe-bench/logs/`.