# Mysql-replication-ansible

## Requirements

* Ansible
* RHEL/CentOS 7
* Disable Selinux
## Role Variables

Available variables are listed below, along with default values (see defaults/main.yml):

```
## chooses your versions
galera_major_version: 10.1 

## config user password for replication
mysql_replication_user: 
  name: replication
  password: secret 

## password for your mysql
mariadb_root_password: abx

## Choose master in you inventory.ini.
mysql_replication_master: "{{ ('databases' in groups) | ternary(groups['databases'][0], 'localhost') }}"

```
## Example template

-------------------------
You can change config mysql in templates/server.cnf.j2

## Usage
This role works with either MySQL or a compatible version of MariaDB. On RHEL/CentOS 7+, the mariadb database engine was substituted as the default MySQL replacement package. No modifications are necessary though all of the variables still reference 'mysql' instead of mariadb.
Clone this repository.

### Run

    $ git clone https://github.com/anphn/ansbile-mysql-replication.git
    $ cd ansbile-mysql-replication
    $ ansible-playbook -i inventory.ini site.yaml 
