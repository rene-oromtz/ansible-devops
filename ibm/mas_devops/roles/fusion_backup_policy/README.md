fusion_backup_policy
============

This role is used to create the Fusion Backup Policies needed for Backup and Restore of supported applications. 
By default, the backups will be performed on defined weekday at 12 AM of the specified timezone

Role Variables
--------------

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

### fusion_namespace
Defines the namespace where IBM Storage Fusion was installed

- Environment Variable: `FUSION_NAMESPACE`
- Default: `ibm-spectrum-fusion-ns`

### backup_storage_location
Defines the backup storage location where Fusion backups will be stored

- **Required**
- Environment Variable: `BACKUP_STORAGE_LOCATION`
- Default: None

### backup_retention_days
Defines how long backups will be maintained.

- Environment Variable: `RETENTION_DAYS`
- Default: `30`

### backup_weekday
Defines when backups are going to be made

- Environment Variable: `BACKUP_WEEKDAY`
- Default: `Sunday`
- Supported Values: All weekdays name and `Daily` if wanted daily backups

### backup_timezone
Defines when backups are going to be made

- Environment Variable: `BACKUP_TIMEZONE`
- Default: `America/Mexico_City`

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
    backup_retention_days: 15
    backup_weekday: Monday
    backup_timezone: America/Phoenix

  roles:
    - ibm.mas_devops.fusion_backup_policy_create
```

License
-------

EPL-2.0
