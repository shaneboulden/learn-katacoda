# Deploy and configure SQL Server

In *Terminal Server* tab of the lab interface, create a container runtime using podman which -
passes in-container accesses to /var/opt/mssql directories through to the host's /var/mssql directories, 
read-only access to the hosts /sys/fs/cgroup directory, and port mapping the host port (1433) to the container's port (1433).

Pass in the flag to programatically accept the EULA agreement, and setup SQL Server with the provided sa account password 

`podman run -v /var/mssql/data:/var/opt/mssql/data:Z -v /var/mssql/log:/var/opt/mssql/log:Z -v /var/mssql/secrets:/var/opt/mssql/secrets:Z -v /var/mssql/scripts:/var/opt/mssql/scripts:Z -v /sys/fs/cgroup:/sys/fs/cgroup:ro -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=RedHat1!' -p 1433:1433 -it mcr.microsoft.com/mssql/rhel/server:2019-latest`{{execute T2}}

<pre class="file">
SQL Server 2019 will run as non-root by default.
This container is running as user mssql.
<< OUTPUT ABRIDGED >>
</pre>

> **NOTE:** In SQL Server 2019, the container runs using a non-root user by default. The default user is mssql. In step 1, we changed user ownership of the /var/mssql directories to uid:10001 that maps to the mssql user.