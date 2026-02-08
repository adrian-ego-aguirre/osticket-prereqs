<p align="center">
  <img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket Logo"/>
</p>

<h1 align="center">osTicket – Phase 1: Prerequisites & Installation</h1>

<p>
This lab documents the prerequisites, installation, and configuration of <strong>osTicket</strong>, an open-source help desk ticketing system, deployed on a Windows 10 web server using IIS.
</p>

---

<h2>🛠 Environments & Technologies Used</h2>

<ul>
  <li>Microsoft Azure (Virtual Machines)</li>
  <li>Windows Remote Desktop (RDP)</li>
  <li>Internet Information Services (IIS)</li>
  <li>PHP</li>
  <li>MySQL</li>
</ul>

---

<h2>💻 Operating Systems Used</h2>

<ul>
  <li>Windows 10 (21H2)</li>
</ul>

---

<h2>📋 Prerequisites</h2>

<ul>
  <li><strong>MySQL:</strong> Database server used to store osTicket data.</li>
  <li><strong>HeidiSQL:</strong> GUI-based database management tool for MySQL.</li>
  <li><strong>PHP:</strong> Server-side scripting language required by osTicket.</li>
  <li><strong>PHP Manager for IIS:</strong> Tool for managing PHP configuration.</li>
  <li><strong>Visual C++ Redistributable:</strong> Runtime dependency for PHP and IIS.</li>
  <li><strong>URL Rewrite Module:</strong> Enables URL rewriting and routing in IIS.</li>
</ul>

---

<h1>📌 Phase 1 Overview – Prerequisites & Installation</h1>

<ol>
  <li>Prepare Windows 10 by configuring it as a web server.</li>
  <li>Install all required prerequisite software.</li>
  <li>Install and configure osTicket as an IIS-hosted website.</li>
  <li>Enable required PHP extensions and assign permissions.</li>
  <li>Complete osTicket installation using MySQL.</li>
  <li>Verify agent and end-user access.</li>
  <li>Secure the installation by removing setup files.</li>
</ol>

---

<h2>1️⃣ Prepare Windows 10 as a Web Server</h2>

<p>
Install and enable <strong>Internet Information Services (IIS)</strong>, including:
</p>

<ul>
  <li>Web Server</li>
  <li>Application Development Features</li>
  <li>IIS Management Console</li>
</ul>

---

<h2>2️⃣ Install Prerequisite Software</h2>

<h3>Installation Steps</h3>

<ol>
  <li>Install PHP Manager for IIS.</li>
  <li>Install Visual C++ Redistributable.</li>
  <li>Install URL Rewrite Module.</li>

  <li>Install PHP:
    <ul>
      <li>Create directory: <code>C:\PHP</code></li>
      <li>Extract PHP files into <code>C:\PHP</code></li>
      <li>Register PHP within IIS</li>
      <li>Restart IIS</li>
    </ul>
  </li>

  <li>Install MySQL:
    <ul>
      <li>Typical Setup</li>
      <li>Launch Configuration Wizard</li>
      <li>Standard Configuration</li>
      <li>Create root password</li>
    </ul>
  </li>

  <li>Install HeidiSQL:
    <ul>
      <li>Create a new session using root credentials</li>
      <li>Connect to MySQL server</li>
      <li>Create database named <strong>osTicket</strong></li>
    </ul>
  </li>
</ol>

---

<h2>3️⃣ Install osTicket</h2>

<ol>
  <li>Download osTicket v1.15.8</li>
  <li>Extract and copy the <strong>upload</strong> folder to:
    <code>C:\inetpub\wwwroot</code>
  </li>
  <li>Rename <code>upload</code> to <code>osTicket</code></li>
  <li>Restart IIS</li>
</ol>

<p>
Verify installation:
</p>

<ul>
  <li>IIS → Sites → Default Web Site → osTicket → Browse *:80</li>
</ul>

---

<h2>4️⃣ Enable PHP Extensions & Assign Permissions</h2>

<h3>Enable PHP Extensions</h3>

<ul>
  <li>php_imap.dll</li>
  <li>php_intl.dll</li>
  <li>php_opcache.dll</li>
</ul>

<h3>Rename Configuration File</h3>

<ul>
  <li>From: <code>ost-sampleconfig.php</code></li>
  <li>To: <code>ost-config.php</code></li>
</ul>

<h3>Assign Permissions</h3>

<ul>
  <li>Disable inheritance</li>
  <li>Remove existing permissions</li>
  <li>Add <strong>Everyone</strong> with Full Control (temporary)</li>
</ul>

---

<h2>5️⃣ Complete osTicket Installation</h2>

<ol>
  <li>Open osTicket in browser and click <strong>Continue</strong></li>
  <li>Configure Help Desk name</li>
  <li>Set default support email</li>
  <li>Database Name: <strong>osTicket</strong></li>
  <li>Username: <strong>root</strong></li>
  <li>Password: (configured earlier)</li>
  <li>Click <strong>Install Now</strong></li>
</ol>

---

<h2>6️⃣ Verify Access</h2>

<ul>
  <li>
    <strong>Agent Login:</strong><br>
    <a href="http://localhost/osTicket/scp/login.php">
      http://localhost/osTicket/scp/login.php
    </a>
  </li>

  <li>
    <strong>End User Portal:</strong><br>
    <a href="http://localhost/osTicket/">
      http://localhost/osTicket/
    </a>
  </li>
</ul>

---

<h2>7️⃣ Post-Installation Security Cleanup</h2>

<ol>
  <li>Delete setup directory:
    <code>C:\inetpub\wwwroot\osTicket\setup</code>
  </li>
  <li>Change <code>ost-config.php</code> permissions to <strong>Read-only</strong></li>
</ol>

---

<h2>✅ Key Takeaways</h2>

<ul>
  <li>osTicket requires precise dependency configuration</li>
  <li>IIS + PHP integration is sensitive to permissions</li>
  <li>Ticketing systems rely heavily on proper backend setup</li>
  <li>Post-installation security cleanup is critical</li>
</ul>

---

<h2>📌 Conclusion</h2>

<p>
In this phase, osTicket was successfully installed and deployed on a Windows 10 system running IIS. All required dependencies—including PHP, MySQL, and supporting modules—were properly configured, and the application was verified to be accessible for both agents and end users.
</p>

<p>
Post-installation security steps were completed to reduce risk, including removing setup files and locking down configuration permissions. With the core platform installed and secured, the environment is now prepared for further configuration.
</p>

<p>
This concludes Phase 1 and establishes the foundation for Phase 2, where system roles, departments, SLAs, and workflows are configured to support real-world help desk operations.
</p>
