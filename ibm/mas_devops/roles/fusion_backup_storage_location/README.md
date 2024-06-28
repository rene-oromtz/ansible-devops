fusion_backup_storage_location
============

This role is used to create the Fusion Backup Storage Location where all backups are stored. 
This role creates a BSL with the same name as the specified bucket. 

Role Variables
--------------

### mas_config_dir
If specified configure the destination directory where to save the generated BackupPolicy yaml file

- Environment Variable: `MAS_CONFIG_DIR`
- Default: None

### fusion_namespace
Defines the namespace where IBM Storage Fusion was installed

- Environment Variable: `FUSION_NAMESPACE`
- Default: `ibm-spectrum-fusion-ns`

### backup_storage_location
Defines the backup storage location where Fusion backups will be stored. 
For S3, this corresponds to the bucket name. 

- **Required**
- Environment Variable: `BACKUP_STORAGE_LOCATION`
- Default: None

### bsl_endpoint
Defines the backup storage location endpoint where Fusion backups will be stored

- **Required**
- Environment Variable: `BSL_ENDPOINT`
- Default: None

### access_key_id
Defines the access key id for the specified endpoint

- **Required**
- Environment Variable: `ACCESS_KEY_ID`
- Default: None

### secret_key
Defines the secret key for the specified endpoint

- **Required**
- Environment Variable: `SECRET_KEY`
- Default: None

### provider_type
Defines the provider for the specified endpoint

- **Required**
- Environment Variable: `PROVIDER_TYPE`
- Default: None
- Supported Values: `ibm` for IBM S3 COS

Example Playbook
----------------

```yaml
---

- hosts: localhost
  any_errors_fatal: true
  vars:
    mas_config_dir: ~/masconfig
    fusion_namespace: custom_ns
    bucket_name: maximo_storage
    bucket_enpoint: https://s3.us-south.cloud-object-storage.appdomain.cloud/
    access_key_id: 131f141xxxxxxxxxxxxxxxxxxxxx
    secret_key: ca7b6aecxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
    provider_type: ibm

  roles:
    - ibm.mas_devops.fusion_backup_storage_location
```

License
-------

EPL-2.0
