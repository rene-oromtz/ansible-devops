fusion_policy_assignment
============

This role is used to create the Fusion Policy Assignment. This assigns the policy and recipe to the specified application for Backup and Restore

Role Variables
--------------

### mas_instance_id
Defines the instance id that was used for the MAS installation

- **Required**
- Environment Variable: `MAS_INSTANCE_ID`
- Default: None

### mas_config_dir
If specified configure the destination directory where to save the generated BackupPolicy yaml file

- Environment Variable: `MAS_CONFIG_DIR`
- Default: None

### fusion_app_id
Defines the application for recipe creation

- **Required**
- Environment Variable: `FUSION_APP_ID`
- Default: None
- Supported values: `db2`, `mongodb`, `sls`, `core`, `manage`

### mongodb_namespace
Defines the namespace where MongoDb was installed

- Environment Variable: `MONGODB_NAMESPACE`
- Default: `mongoce`

### db2_namespace
Defines the namespace where Db2 was installed

- Environment Variable: `DB2_NAMESPACE`
- Default: `db2u`

### kafka_namespace
Defines the namespace where AMQ-Streams was installed, which is the only supported Kafka provider for Fusion B/R

- Environment Variable: `KAFKA_NAMESPACE`
- Default: `amq-streams`

### sls_namespace
Defines the namespace where SLS was installed

- Environment Variable: `SLS_NAMESPACE`
- Default: `ibm-sls`

### fusion_namespace
Defines the namespace where IBM Storage Fusion was installed

- Environment Variable: `FUSION_NAMESPACE`
- Default: `ibm-spectrum-fusion-ns`

### backup_storage_location
Defines the backup storage location where Fusion backups will be stored

- **Required**
- Environment Variable: `BACKUP_STORAGE_LOCATION`
- Default: None

### backup_policy
Defines the backup policy for the application

- Environment Variable: `BACKUP_POLICY`
- Default: <FUSION_APP_ID>-policy

### fusion_recipe
Defines the recipe to be used by the application

- Environment Variable: `FUSION_RECIPE`
- Default: maximo-<FUSION_APP_ID>-backup-restore-recipe

### core_namespace
Defines the recipe to be used by the application

- Environment Variable: `CORE_NAMESPACE`
- Default: mas-<MAS_INSTANCE_ID>-core

### manage_namespace
Defines the recipe to be used by the application

- Environment Variable: `MANAGE_NAMESPACE`
- Default: mas-<MAS_INSTANCE_ID>-manage


Example Playbook
----------------

```yaml
---

- hosts: localhost
  any_errors_fatal: true
  vars:
    mas_config_dir: ~/masconfig
    fusion_app_id: core
    fusion_namespace: custom_ns
    backup_storage_location: maximo_backup_location

  roles:
    - ibm.mas_devops.fusion_backup_policy_create
```

License
-------

EPL-2.0
