# 09_setup_filebeat
You deploy Filebeat as a DaemonSet to ensure there’s a running instance on each node of the cluster.

The container logs host folder (/var/log/containers) is mounted on the Filebeat container. Filebeat starts an input for the files and begins harvesting them as soon as they appear in the folder.

Everything is deployed under the infra-logging namespace.
<!-- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -->

## Objectives
- Create a WordPress deployment as a web application.
- Create a NodePort-type service for the WordPress service.
- Create a MySQL deployment as a database.
- Create a secret named "mysql-pass" to store the password for your database.