# Project Documentation

<div align="center">
  <h1>ERPNext Server Setup</h1>
  <p>Complete guide for installation, configuration, and backup</p>
</div>

<hr/>

<h2>📦 Installation</h2>
<ol>
  <li>Update system packages:
    <pre><code>sudo apt update && sudo apt upgrade -y</code></pre>
  </li>
  <li>Install dependencies:
    <pre><code>sudo apt install python3-dev python3-setuptools python3-pip python3-distutils -y</code></pre>
  </li>
  <li>Install other required packages:
    <pre><code>sudo apt install mariadb-server mariadb-client redis-server -y</code></pre>
  </li>
</ol>

<hr/>

<h2>⚙️ Configuration</h2>
<ol>
  <li>Secure MariaDB installation:
    <pre><code>sudo mysql_secure_installation</code></pre>
  </li>
  <li>Create new database user for ERPNext</li>
  <li>Set required permissions</li>
</ol>

<hr/>

<h2>💾 Backup Instructions</h2>
<p>To backup changes:</p>
<ol>
  <li>Run (with <code>erpnext-user</code> privileges):
    <pre><code>bench --site smartb.dev backup</code></pre>
  </li>
  <li>Then with <strong>root</strong> privileges run:
    <pre><code>git add .
git commit -am "Server Backup Date"
git push</code></pre>
  </li>
</ol>

<hr/>

<h2>📄 Notes</h2>
<ul>
  <li>Ensure all commands are run in correct user context.</li>
  <li>Replace placeholders with actual values for your setup.</li>
</ul>

