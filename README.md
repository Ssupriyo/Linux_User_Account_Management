# Linux User Account Management Project

![GitHub Repo Size](https://img.shields.io/github/repo-size/Ssupriyo/Linux_User_Account_Management?style=flat-square)
![GitHub Last Commit](https://img.shields.io/github/last-commit/Ssupriyo/Linux_User_Account_Management?style=flat-square)
![GitHub License](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)

---

## Project Overview

This project demonstrates user, group, and permission management in Linux, simulating a real-world System Administrator environment.
It involves creating users, managing access rights, and setting up secure shared directories for teams using Linux commands.

---

## Objective

To gain hands-on experience with:

* Linux user and group management
* File permissions and access control (`chmod`, `chgrp`, `usermod`)
* Collaboration between teams while maintaining security

---

## Real-World Use Case

A company has two teams:

* Developers
* Testers

Each team requires its own secure directory for collaboration, and both teams should have access to a shared read-only directory for reference materials.
This project simulates how a system administrator sets up and manages such an environment using Linux.

---

## Commands Used

| Task                      | Command                                                                                                           | Description                      |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------- | -------------------------------- |
| Create users              | `sudo useradd dev_user` <br> `sudo useradd test_user` <br> `sudo useradd admin_user`                              | Adds three users                 |
| Create groups             | `sudo groupadd developers` <br> `sudo groupadd testers`                                                           | Creates groups for each team     |
| Add users to groups       | `sudo usermod -aG developers dev_user` <br> `sudo usermod -aG testers test_user`                                  | Assigns users to their groups    |
| Create shared directories | `sudo mkdir -p /shared/development /shared/testing /shared/readonly`                                              | Creates shared folders           |
| Assign group ownership    | `sudo chgrp developers /shared/development` <br> `sudo chgrp testers /shared/testing`                             | Sets group ownership             |
| Set permissions           | `sudo chmod 770 /shared/development` <br> `sudo chmod 770 /shared/testing` <br> `sudo chmod 755 /shared/readonly` | Defines access levels            |
| Verify permissions        | `ls -ld /shared/*`                                                                                                | Checks directory permissions     |
| Generate report           | `ls -la /shared/ > ~/Linux_User_Account_Management/permissions_report.txt`                                        | Creates a permission report file |

---

## Observations

| User                              | Expected Access       | Result  | Observation         |
| --------------------------------- | --------------------- | ------- | ------------------- |
| `dev_user`                        | `/shared/development` | Success | Full access granted |
| `test_user`                       | `/shared/testing`     | Success | Full access granted |
| `dev_user → /shared/testing`      | Access Denied         | Success | Isolation verified  |
| `test_user → /shared/development` | Access Denied         | Success | Isolation verified  |
| `all users → /shared/readonly`    | Read-only             | Success | Working as expected |

---

## Results

* All users and groups were configured successfully.
* Permissions and access control behaved exactly as intended.
* Role-based directory access was implemented securely and verified through practical testing.

---

## Conclusion

This project demonstrates essential Linux administration skills such as user/group management, permission configuration, and access control.
These techniques are fundamental in real-world IT environments where administrators manage multiple teams securely.

---

## How to Run

1. Clone the repository:

   ```bash
   git clone https://github.com/Ssupriyo/Linux_User_Account_Management.git
   ```
2. Open the `scripts` directory and run each command in your Linux terminal.
3. Verify permissions and review the `permissions_report.txt`.

---

## Project Structure

```
Linux_User_Account_Management/
├── scripts/
│   ├── create_users.sh
│   ├── manage_groups.sh
│   ├── setup_directories.sh
│   └── verify_permissions.sh
├── permissions_report.txt
└── README.md
```
