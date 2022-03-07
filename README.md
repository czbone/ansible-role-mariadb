# MariaDB用Ansibleロール

MariaDBインストール用のAnsibleロールです。
bertvv.mariadb(https://github.com/bertvv/ansible-role-mariadb )のv2.2.0を元に作成しています。
主な改良点はMariaDBの日本語向けの対応です。サーバの文字コードやCollationの指定ができます。

## 対応OS

- CentOS Stream 8

## Ansible依存モジュール

Ansible v2.12以降に対応しています。
以下のコレクションを使用しています。

- ansible.posix
- community.mysql

## ロール設定値

### 基本定義値

| 定義名                         | デフォルト         | 意味                                                           |
| :---                           | :---               | :---                                                           |
| mariadb_version             | '10.7'             | MariaDBのバージョンを指定します。                              |
| mariadb_character_set_server | 'utf8mb4'             | サーバの文字コードを指定します。                               |
| mariadb_collation_server     | 'utf8mb4_general_ci'  | サーバのCollationを指定します。                                |

デフォルトの設定状況
-----

```
MariaDB [(none)]> show variables like 'character_%';
+--------------------------+----------------------------+
| Variable_name            | Value                      |
+--------------------------+----------------------------+
| character_set_client     | utf8mb4                    |
| character_set_connection | utf8mb4                    |
| character_set_database   | utf8mb4                    |
| character_set_filesystem | binary                     |
| character_set_results    | utf8mb4                    |
| character_set_server     | utf8mb4                    |
| character_set_system     | utf8mb3                    |
| character_sets_dir       | /usr/share/mysql/charsets/ |
+--------------------------+----------------------------+

MariaDB [(none)]> show variables like 'collation_%';
+----------------------+--------------------+
| Variable_name        | Value              |
+----------------------+--------------------+
| collation_connection | utf8mb4_general_ci |
| collation_database   | utf8mb4_general_ci |
| collation_server     | utf8mb4_general_ci |
+----------------------+--------------------+
```

使い方
------------

```yml
# requirements.yml
collections:
  - ansible.posix
  - community.mysql
roles:
  - src: https://github.com/czbone/ansible-role-mariadb
    name: mariadb
```

```yml
# main.yml
collections:
  - ansible.posix
  - community.mysql
roles:
  - mariadb
```
