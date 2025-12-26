# Sensitive-Data-Exposure-Frontend-Source-Code-Analysis
This repository demonstrates a Sensitive Data Exposure vulnerability caused by insecure frontend development practices.
# Sensitive Data Exposure – Frontend Source Code Analysis

## 📌 Overview

This repository demonstrates a **Sensitive Data Exposure** vulnerability caused by insecure frontend development practices. The example shows how sensitive information such as **hardcoded credentials** can be unintentionally exposed through **HTML source code comments**, making them accessible to attackers simply by viewing the page source.

Sensitive Data Exposure occurs when a website fails to properly protect or remove sensitive clear-text information from client-side code (HTML, JavaScript, CSS). This vulnerability is commonly discovered during **web application security assessments** and **penetration testing**.

---

## 🎯 Learning Objectives

* Understand how sensitive data can be exposed in frontend source code
* Identify insecure coding practices in HTML and JavaScript
* Learn how attackers leverage exposed credentials
* Apply secure development best practices to prevent data leakage

---

## 🧠 Vulnerability Description

Web applications are built using HTML elements (tags) that are fully visible to end users via:

* **View Page Source (CTRL + U)**
* **Browser Developer Tools**

In this example, the developer accidentally left **test credentials** inside an HTML comment. Although comments are not rendered visually, they remain accessible in the page source.

### ⚠️ Exposed Information

* Username: `admin`
* Password: `pssswd`

An attacker could use these credentials to:

* Authenticate into restricted areas
* Pivot to backend systems
* Perform privilege escalation

---

## 🧪 Vulnerable Source Code Example

```html
<!--
    TODO: Remove test credentials!
        Username: admin
        Password: pssswd
-->
```

This comment is visible to anyone inspecting the source code, resulting in **Sensitive Data Exposure**.

---

## 📂 Repository Structure

```
Sensitive-Data-Exposure-Demo/
│
├── index.html          # Vulnerable HTML page
├── css/
│   └── style.css       # Styling file
├── js/
│   └── script.js       # Login logic (frontend)
├── screenshots/
│   └── view-source.png # Evidence of exposed credentials
├── README.md           # Project documentation
```

---

## 🛠️ index.html (Vulnerable Page)

```html
<html>
<head>
    <title>How websites work</title>
    <link rel="stylesheet" href="css/style.css">
</head>

<body>
    <div id="html-code-box">
        <div id="html-bar">
            <span id="html-url">https://vulnerable-site.com</span>
        </div>
        <div class="theme" id="html-code">
            <div class="logo-pos"><img src="img/logo_white.png"></div>
            <p id="login-msg">Incorrect credentials.
                <i class="hint" onclick="viewSourceCode()">Try looking at the source code</i>
            </p>
            <form method="post" id="form" autocomplete="off">
                <div class="form-field">
                    <input class="input-text" type="text" name="username" placeholder="Username..">
                </div>
                <div class="form-field">
                    <input class="input-text" type="password" name="password" placeholder="Password..">
                </div>
                <button onclick="login()" type="button" class="login">Login</button>

                <!--
                    TODO: Remove test credentials!
                        Username: -----------------
                        Password: -----------------
                -->
            </form>
            <div class="footer">Copyright © Vulnerable Website</div>
        </div>
    </div>
    <script src="js/script.js"></script>
</body>
</html>
```

---

## 🔍 How to Identify This Vulnerability

1. Open the webpage in a browser
2. Right-click → **View Page Source** or press **CTRL + U**
3. Search for keywords such as:

   * `password`
   * `username`
   * `TODO`
   * `admin`
4. Review HTML comments and JavaScript files

---

## ✅ Secure Coding Best Practices

* ❌ Never store credentials in frontend code
* ❌ Avoid leaving comments with sensitive data
* ✅ Use environment variables on the backend
* ✅ Enforce server-side authentication
* ✅ Perform regular code reviews
* ✅ Use automated security scanning tools (SAST)

---

## 🧩 Related OWASP Category

* **OWASP Top 10:** A02 – Cryptographic Failures (formerly Sensitive Data Exposure)

---

## 👨‍💻 Author

**Gamar**
Cybersecurity Analyst | Cloud Security & AI-ML | Web Security

---

## ⚠️ Disclaimer

This repository is for **educational and ethical security training purposes only**. Do not use these techniques on systems you do not own or have explicit permission to test.
