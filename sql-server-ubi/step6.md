# Checkpoint and restore the container running SQL Server

One of Podman’s features is to be able to checkpoint and restore running containers. Podman uses CRIU (Checkpoint/Restore In Userspace) to do the actual checkpointing and restoring of the processes inside of the container. 

`podman container checkpoint -l --tcp-established`{{execute T3}}

<pre class="file">
TBD1
</pre>

Without telling Podman to checkpoint the container while keeping the established TCP connection intact (--tcp-established) the checkpointing will fail. The container has been now checkpointed with all its data 

`podman container restore -l --tcp-established`{{execute T3}}

<pre class="file">
TBD2
</pre>