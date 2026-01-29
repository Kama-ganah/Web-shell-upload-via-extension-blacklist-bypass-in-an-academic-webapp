# Overview
During testing of the application’s avatar upload feature, a high‑severity file upload vulnerability was discovered. The system attempted to prevent malicious uploads using an extension blacklist, but this control was bypassed by leveraging .htaccess directives to treat a custom extension (.l33t) as executable PHP. This allowed the upload and execution of a web shell, leading to remote code execution and unauthorized access to sensitive files.

# Steps Undertaken

Step 1: Logged in with valid credentials and intercepted the avatar upload request using Burp Suite.

Step 2: Attempted to upload a .php shell, which was blocked by the server’s blacklist.

Step 3: Uploaded a .htaccess file configuring the server to execute .l33t files as PHP.

Step 4: Uploaded the web shell using a .l33t extension.

Step 5: Accessed and executed the payload to retrieve sensitive server files (e.g., /home/user/secret).

# Conclusion

This assessment confirmed a critical web shell upload vulnerability caused by relying on extension blacklisting and allowing .htaccess overrides. The flaw enabled arbitrary code execution, compromising server integrity and sensitive data. Immediate remediation—such as extension whitelisting, disabling .htaccess in upload directories, and storing uploads outside the web root—is required to prevent exploitation.
