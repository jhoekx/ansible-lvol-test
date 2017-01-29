# Integration tests for the ansible lvol module

## Prerequisites

Update the hosts file to match your test environment:

```
lvm-test ansible_ssh_host=my-vm ansible_ssh_user=root test_vg=vg_my-vm_data
```

This runs the tests on `my-vm`, as `root` and expects a volume group named `vg_my-vm_data`. It's a good idea to attach a separate disk to the VM and create the volume group on it.

Symlink your version of the `lvol` module in library to test it.

## Running

Run the tests with:

```
[jeroen@island test-lvm]$ ansible-playbook test-lvol.yml 

PLAY [Test lvol module] ********************************************************

TASK [setup] *******************************************************************
ok: [lvm-test]

TASK [Remove the logical volume] ***********************************************
ok: [lvm-test]

TASK [Create a normal logical volume] ******************************************
changed: [lvm-test]

TASK [Extend the logical volume size] ******************************************
changed: [lvm-test]

TASK [Remove the logical volume] ***********************************************
changed: [lvm-test]

TASK [Remove the logical volume] ***********************************************
ok: [lvm-test]

TASK [Create a deactivated logical volume] *************************************
changed: [lvm-test]

TASK [Activate a deactivated logical volume] ***********************************
ok: [lvm-test]

TASK [Deactivate the activated logical volume] *********************************
changed: [lvm-test]

TASK [Remove the logical volume] ***********************************************
changed: [lvm-test]

TASK [Remove the logical volume] ***********************************************
ok: [lvm-test]

TASK [Create a normal logical volume] ******************************************
changed: [lvm-test]

TASK [Create a snapshot of the volume] *****************************************
changed: [lvm-test]

TASK [Remove the logical volume] ***********************************************
changed: [lvm-test]

PLAY RECAP *********************************************************************
lvm-test                   : ok=14   changed=9    unreachable=0    failed=0
```

