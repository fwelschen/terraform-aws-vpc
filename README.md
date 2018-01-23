Modified AWS VPC Terraform module 
========================

This module is based on [AWS VPC Terrform](https://github.com/terraform-aws-modules/terraform-aws-vpc/tree/v1.17.0). The idea is to have 3 types of networks: Public, Private and Backend (where databases, redshift and elasticache will be created)

Schema:
```
+-------------------------------------------------+
|                                                 |
|                                                 |
|                                                 |
|                 Public Network                  |
|                                                 |
|                                                 |
|                                                 |
+-------------------------------------------------+
|                                                 |
|                                                 |
|                                                 |
|                 Private Network                 |
|                                                 |
|                                                 |
|                                                 |
+-------------------------------------------------+
|                                                 |
|                                                 |
|                                                 |
|                 Backend Network                 |
|          (DBs, Redshift, Elasticache)           |
|                                                 |
|                                                 |
+-------------------------------------------------+
```

If you have a VPN link between your office and the VPC, the Backend network should only be access by admin vlan.

Modifications:
- Unification of elasticache, redshift and database networks in the same network called backend
- By default, it will create the groups of networks for DB, Elasticache and Redshift.