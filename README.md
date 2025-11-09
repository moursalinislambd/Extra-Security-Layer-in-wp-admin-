<h1>Secure WordPress wp-admin with .htpasswd</h1>

<p>This guide adds an extra login layer to your WordPress admin panel.</p>

<hr>

<h2>Step 1: Create .htpasswd File</h2>
<p>Go to your hosting file manager or FTP and open your WordPress root directory. Create a file named:</p>

<pre>.htpasswd</pre>

<p>Add your login details (example):</p>

<pre>username:password</pre>

<hr>

<h2>Step 2: Find Full Server Path</h2>
<p>Create a file named:</p>

<pre>test.php</pre>

<p>Paste this code inside:</p>

<pre>
&lt;?php
echo dirname(__FILE__) . '/.htpasswd';
?&gt;
</pre>

<p>Now open it in your browser:</p>

<pre>https://yourdomain.com/test.php</pre>

<p>Copy the full path that appears on the page. Then delete <code>test.php</code> for security.</p>

<hr>

<h2>Step 3: Protect wp-admin Directory</h2>
<p>Inside your <code>wp-admin</code> folder, create a file named:</p>

<pre>.htaccess</pre>

<p>Paste the following:</p>

<pre>
AuthType Basic
AuthName "Restricted Area"
AuthUserFile /path/to/.htpasswd
Require valid-user
</pre>

<p>Replace <code>/path/to/.htpasswd</code> with the path from Step 2.</p>

<hr>

<h2>✅ Done</h2>
<p>Your <code>wp-admin</code> is now protected with an additional login prompt.</p>
