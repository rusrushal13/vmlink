# VMLINK Automounter Operation

The basic flow is as follows:

* a user references a file or directory triggering the script
* the script loads its optional configuration, if any
* the script parses the key into *vmid*, *addr*, and optionally *partition*
* next, the script looks for an available (unused) I/O address (local address)
* it attempts to link the target *vmid* and *addr* at that local address
* if the link was successful, then the script varies the new disk (local address) online
* if the online was successful, the script must find the block device assigned
* if the block device was found, the script finally attempts to mount it (or a partition)

## Clean-up:

The script should check if a disk being linked has already been linked.
That must happen before the new (redundant) link is varied online.

The script should periodically vary-off and detach (unlink) disks which
have become unmounted.

## Partitioning:

Minidisks might be unpartitioned.
For example, the CMS "EDF" minidisk filesystem occupies the entire disk.
Other filesystems may also start at offset zero and may or may not obscure the partition table.

If no partition is specified, the VMLINK automounter script must attempt both
"whole disk" and "partition one" (order to be determined). If a specific partition was
indicated, then the script must succeed in mounting that partition or must fail the operation.


