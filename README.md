# VMLINK

VMLINK Automounter for Linux on z/VM

VMLINK extends the namespace of a virtual machine to include 
devices of (specifically disks owned by) other virtual machines.

## VMLINK Automounter

Consider automounter point `/vmlink`, similar to `/misc` and `/net`.
Under `/vmlink`, one can have target directories ("keys" in automounter speak)
named *vmid.addr* where "vmid" is the owning virtual machine
and "addr" is the address of a disk on that virtual machine.

## cd /vmlink/yourvm.yourdisk

The VMLINK automounter script uses the key, here `yourvm.yourdisk`,
to "link" (at the z/VM layer) your disk, bring it online,
and then mount it at the named location under the automounter point.

## VMLINK Concept

VMLINK automates referencing disks of other virtual machines
on demand of the "client" guest. Host administrative action
is required for authorizing such references. Host administration
is not required for activating such references once authorized.

In other words, you must be granted the right to use another disk,
but once authorized you do not have to engage the administrator
to use a disk for which you are authorized.

## VMLINK Project

Rushal Verma is developing the VMLINK automounter script as an intern project
under the Linux Foundation. Weekly status is maintained here:

https://docs.google.com/document/d/1E1UOcMKoqYWU_cfNOGwl8sFxOs5APxe8CVb53m3Iv_Q

https://drive.google.com/drive/folders/1NtwHRFS1MFRy83vGJJmKNZyLxE6vVRxb?usp=sharing_eip&ts=5b0ca20f

https://www.youtube.com/watch?v=VYOXuOg9tQI






