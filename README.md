# MariaDB用Ansibleロール

MariaDBインストール用のAnsibleロールです。
bertvv.mariadb(https://github.com/bertvv/ansible-role-mariadb)のv2.2.0を元に作成しています。
主な改良点はMariaDBの日本語向けの対応です。Collation等の指定ができます。

# 対応OS

- CentOS7

### 基本定義値

| 定義名                       | デフォルト         | 意味                                                                                                      |
| :---                           | :---            | :---                                                                                                          |
| `mariadb_version`              | '10.5'          | MariaDBのバージョンを指定します。                               |
