
Link: http://mezzanine.jupo.org/docs/deployment.html

Configuration to deploy on Ubuntu 14.04

Configurable variables are implemented in the project’s local_settings.py module. Here’s an example, that leverages some existing setting names:

# Domains for public site
ALLOWED_HOSTS = ["example.com"]

FABRIC = {
    "DEPLOY_TOOL": "rsync",  # Deploy with "git", "hg", or "rsync"
    "SSH_USER": "server_user",  # VPS SSH username
    "HOSTS": ["123.123.123.123"],  # The IP address of your VPS
    "DOMAINS": ALLOWED_HOSTS,  # Edit domains in ALLOWED_HOSTS
    "REQUIREMENTS_PATH": "requirements.txt",  # Project's pip requirements
    "LOCALE": "en_US.UTF-8",  # Should end with ".UTF-8"
    "DB_PASS": "",  # Live database password
    "ADMIN_PASS": "",  # Live admin user password
    "SECRET_KEY": SECRET_KEY,
    "NEVERCACHE_KEY": NEVERCACHE_KEY,
}


Deploying to a brand new server
  Get your sever. Anything that grants you root access works. VPS’s like those from Digital Ocean work great and are cheap.
  Fill the ALLOWED_HOSTS and FABRIC settings in local_settings.py as shown in the Configuration section above. For SSH_USER provide any username you want (not root), and the fabfile will create it for you.
  Run fab secure. You simply need to know the root password to your VPS. The new user will be created and you can SSH with that from now on (if needed). For security reason, root login via SSH is disabled by this task.
  Run fab all. It will take a while to install the required environment, but after that, your Mezzanine site will be live.

File local_settings.py is not on git
