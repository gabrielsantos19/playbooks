# playbooks


## deploy-wordpress.yml
This playbook deploys files/wordpress project. It needs to receive the 
project_name variable as in the example below.

<code> ansible-playbook deploy-wordpress.yml -e project_name=wp32 </code>

This will create a folder named project_name on the target and deploy a wordpress stack.
The folder is a copy of files/wordpress.
Change the .env file in order to define the wordpress deploy.

### files/wordpress
.env - Configuration variables. You need to define them in order to deploy.  
custom.ini - Optional file to change php directives.
docker-compose.yml - You may remove 
- ./install.php:/usr/src/wordpress/wp-admin/install.php
- ./custom.ini:/usr/local/etc/php/conf.d/custom.ini  

from "volumes" and the "env_file" definition so the deployment 
will act as Wordpress default.
**Be sure to provide unique database variables on .env for each deploy. 
Since all Wordpress will be on the same MySQL, repeat the database variables 
will grant access of a single database for multiple Wordpress, wich may cause 
problems.**

install.php - Optional file to auto-install Wordpress.  
