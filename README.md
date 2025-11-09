<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Secure WordPress wp-admin Guide</title>

<style>
  body {
    margin: 0;
    background: linear-gradient(135deg, #4D9FEC, #4158D0);
    font-family: "Segoe UI", sans-serif;
    color: #fff;
  }
  .container {
    max-width: 900px;
    background: #ffffff;
    color: #2b2b2b;
    margin: 60px auto;
    padding: 40px;
    border-radius: 14px;
    box-shadow: 0 12px 45px rgba(0,0,0,0.25);
    animation: fadeIn .7s ease-in-out;
  }
  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(20px);}
    to   { opacity: 1; transform: translateY(0);}
  }
  h1 {
    text-align: center;
    font-weight: 700;
    color: #334155;
    margin-bottom: 10px;
  }
  .sub {
    text-align: center;
    margin-bottom: 35px;
    color: #64748b;
  }
  .step {
    margin-bottom: 35px;
    padding: 20px;
    border-radius: 10px;
    background: #f8fafc;
    border-left: 5px solid #2563eb;
  }
  .step h2 {
    margin-top: 0;
    color: #1e3a8a;
  }
  pre {
    background: #0f172a;
    color: #e2e8f0;
    padding: 16px;
    border-radius: 8px;
    font-size: 15px;
    position: relative;
    overflow-x: auto;
    margin-top: 10px;
  }
  .copy-btn {
    position: absolute;
    right: 10px;
    top: 10px;
    background: #2563eb;
    color: #fff;
    border: none;
    padding: 6px 12px;
    border-radius: 6px;
    cursor: pointer;
    font-size: 13px;
    transition: 0.25s;
  }
  .copy-btn:hover {
    background: #1746b7;
  }
  .done {
    text-align: center;
    background: #d9fce6;
    border: 1px solid #63d18b;
    padding: 20px;
    margin-top: 40px;
    border-radius: 10px;
    color: #14532d;
    font-weight: 600;
  }
</style>
</head>
<body>

<div class="container">
  <h1>Secure Your WordPress wp-admin</h1>
  <p class="sub">Add additional login protection using <code>.htpasswd</code> & <code>.htaccess</code></p>

  <div class="step">
    <h2>Step 1: Create .htpasswd File</h2>
    <p>Create <code>.htpasswd</code> in your WordPress root and add credentials:</p>
    <pre><button class="copy-btn" onclick="copyCode(this)">Copy</button>username:password</pre>
  </div>

  <div class="step">
    <h2>Step 2: Locate Absolute File Path</h2>
    <p>Create <code>test.php</code> in same directory:</p>
    <pre><button class="copy-btn" onclick="copyCode(this)">Copy</button>&lt;?php
echo dirname(__FILE__) . '/.htpasswd';
?&gt;</pre>
    <p>Open in browser:</p>
    <pre><button class="copy-btn" onclick="copyCode(this)">Copy</button>https://yourdomain.com/test.php</pre>
    <p>Copy displayed path, then delete <code>test.php</code>.</p>
  </div>

  <div class="step">
    <h2>Step 3: Protect wp-admin</h2>
    <p>Inside <code>wp-admin</code>, create <code>.htaccess</code>:</p>
    <pre><button class="copy-btn" onclick="copyCode(this)">Copy</button>AuthType Basic
AuthName "Restricted Area"
AuthUserFile /path/to/.htpasswd
Require valid-user</pre>
    <p>Replace <code>/path/to/.htpasswd</code> with copied path.</p>
  </div>

  <div class="done">✔ Setup Complete. Your wp-admin is now protected.</div>
</div>

<script>
function copyCode(btn) {
  const code = btn.parentElement.innerText.replace("Copy", "").trim();
  navigator.clipboard.writeText(code);
  btn.innerText = "Copied!";
  setTimeout(() => btn.innerText = "Copy", 1400);
}
</script>

</body>
</html>
