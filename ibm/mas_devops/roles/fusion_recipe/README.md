fusion_recipe
============

This role is used to create the Fusion Recipes needed for Backup and Restore of supported applications. 

Role Variables
--------------

### mas_instance_id
Defines the instance id that was used for the MAS installation

- **Required**
- Environment Variable: `MAS_INSTANCE_ID`
- Default: None

### mas_config_dir
If specified configure the destination directory where to save the generated Recipe yaml file

- Environment Variable: `MAS_CONFIG_DIR`
- Default: None

### fusion_app_id
Defines the application for recipe creation

- **Required**
- Environment Variable: `FUSION_APP_ID`
- Default: None
- Supported values: `db2`, `mongodb`, `sls`, `core`, `manage`, `kafka`

### mongodb_namespace
Defines the namespace where MongoDb was installed

- Environment Variable: `MONGODB_NAMESPACE`
- Default: `mongoce`

### db2_namespace
Defines the namespace where Db2 was installed

- Environment Variable: `DB2_NAMESPACE`
- Default: `db2u`

### db2_instance_name
The name of the db2 instance to execute the setup in

- **Required when fusion_app_id is db2**
- Environment Variable: `DB2_INSTANCE_NAME`

### kafka_namespace
Defines the namespace where AMQ-Streams was installed, which is the only supported Kafka provider for Fusion B/R

- Environment Variable: `KAFKA_NAMESPACE`
- Default: `amq-streams`

### sls_namespace
Defines the namespace where SLS was installed

- Environment Variable: `SLS_NAMESPACE`
- Default: `ibm-sls`

### reporting_operator_endpoint
Defines the Reporting operator that Maximo is using. Value needed for Core recipe.

- Environment Variable: `REPORTING_OPERATOR_ENDPOINT`
- Default: `ibm-data-reporter`
- Supported values: `ibm-data-reporter` if using DRO, `uds-endpoint` if using UDS

### reporting_operator_namespace
Defines the Reporting operator that Maximo is using. Value needed for Core recipe.

- Environment Variable: `REPORTING_OPERATOR_NAMESPACE`
- Default: `redhat-marketplace`

### fusion_namespace
Defines the namespace where IBM Storage Fusion was installed

- **Required**
- Environment Variable: `FUSION_NAMESPACE`
- Default: `ibm-spectrum-fusion-ns`

Example Playbook
----------------

```yaml
---

- hosts: localhost
  any_errors_fatal: true
  vars:
    mas_instance_id: masinst1
    mas_config_dir: ~/masconfig
    fusion_app_id: core
    reporting_operator: ibm-data-reporter
    reporting_operator_namespace: redhat-marketplace

  roles:
    - ibm.mas_devops.fusion_recipe_create
```

License
-------

EPL-2.0
