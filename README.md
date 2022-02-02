# anka-ansible-repro
Anka Ansible Test Repro

To repro issue:
- Create a Mac VM template (e.g. 12.2.0-intel)
- Set up a new user on on that VM template called `butterfly` as an Administrator with automatic login, as mentioned in the [Anka documentation](https://docs.veertu.com/anka/intel/getting-started/starting-and-accessing-your-vm).
- Log in with the butterfly user.
- Clone this repo to that VM
- From VM, run `script/bootstrap`.

Expected Result:
```
TASK [Check ansible_user_id] ***************************************************
Tuesday 01 February 2022  14:15:51 -0500 (0:00:05.405)       0:00:05.414 ******
ok: [localhost] => {
    "ansible_user_id": "butterfly"
}
```
- From host machine, run `anka run -w "/Users/butterfly/anka-ansible-repro" 12.2.0-arm bash -c './script/bootstrap'`.

Expected Result:
```
TASK [Check ansible_user_id] ***************************************************
Tuesday 01 February 2022  14:15:51 -0500 (0:00:05.405)       0:00:05.414 ******
ok: [localhost] => {
    "ansible_user_id": "butterfly"
}
```

Actual Result:
```
TASK [Check ansible_user_id] ***************************************************
Tuesday 01 February 2022  14:15:51 -0500 (0:00:05.405)       0:00:05.414 ******
ok: [localhost] => {
    "ansible_user_id": "root"
}
```
