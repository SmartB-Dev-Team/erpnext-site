# <div align="center">🚀 ERPNext Installation, Migration & Backup Guide</div>

---

## <div style="color:#4CAF50;">📦 Installation</div>

<details>
<summary><strong>Click to expand ERPNext installation steps</strong></summary>

### 1️⃣ System Update & Dependencies
```bash
sudo apt update
sudo apt install git python-is-python3 python3-dev python3-pip redis-server libmariadb-dev mariadb-server mariadb-client pkg-config xvfb libfontconfig wkhtmltopdf
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
nvm install 18 # if doesn't work either export to path or close and reopen ubuntu terminal
npm install -g yarn
```

### 2️⃣ Configure MySQL/MariaDB
```bash
sudo mysql_secure_installation
```
If you don't know root user password for MySQL/ MariaDB

Get Inside MySQL:
```bash
mysql -u root
```

Then reset the root password
```sql
ALTER USER 'root'@'localhost' IDENTIFIED BY 'yourpassword';
FLUSH PRIVILEGES;
EXIT;
```

Now restart MariaDB
``bash
sudo systemctl restart mariadb
```
### 3️⃣ Install Bench
```bash
pip install frappe-bench
```

### 4️⃣ Create Bench & Install ERPNext
```bash
bench init frappe-bench
cd frappe-bench
bench new-site smartb-erpnet.dev
bench get-app https://github.com/frappe/erpnext
bench --site smartb-erpnext.dev install-app erpnext
bench start
```

</details>

---

## <div style="color:#2196F3;">🔄 Migration Guide</div>

<details>
<summary><strong>Click to expand migration steps</strong></summary>

1. **Copy backup files to new machine**
```bash
Get from SmartB GitHub repo (both private and public directories)
```

2. **Configure local site to connect to server database**

Update smartb-erpnext.dev/site_config.json to
```bash
{
 "db_name": "_b7b8640a2d1b8b5c",
 "db_password": "0W9ixoW0V8YkDPDe",
 "db_type": "mariadb",
 "db_user": "_b7b8640a2d1b8b5c",
 "developer_mode": 1,
 "db_host": "159.223.43.125",
 "db_port": 3306
}
```
</details>

---

## <div style="color:#FF9800;">💾 Backup Process</div>

<details open>
<summary><strong>Click to expand backup commands</strong></summary>

**Step 1:** Run with `erpnext-user` privileges:
```bash
bench --site smartb.dev backup
```

**Step 2:** Then with `root` privileges:
```bash
git add .
git commit -am "Server Backup $(date +'%Y-%m-%d')"
git push
```

</details>

---
