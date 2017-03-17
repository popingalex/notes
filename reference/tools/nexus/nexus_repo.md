### repositories

http://172.17.38.50:8081/nexus/repository/

#### Common
| path                | blob            | privileges              |
| -                   | -               |                         |
| mvn_proxy_central   | mvn_proxy       |                         |
| mvn_hosted_3rd      | mvn_thirdparty  | admin-edit else-read    |
| mvn_group_develop   | mvn_group       | read                    |

#### CI-RD

| path                | blob            | privileges              |
| -                   | -               | -                       |
| mvn_archive_CI-RD   | mvn_archive     | qa-edit else-read       |
| mvn_release_CI-RD   | mvn_release     | develop-edit else-read  |
| mvn_snapshot_CI-RD  | mvn_snapshot    | develop-edit else-read  |
