# multicloud-infra-vm

This is a blueprint, which instantiates a simple CentOS7 VM on the desired IaaS (currently only OpenStack and Azure are available).

## Blueprints included

  * [Azure Example Network](https://github.com/cloudify-examples/azure-example-network),
  * [OpenStack Example Network](https://github.com/cloudify-examples/openstack-example-network).

  By default, _openstack-example-network_ and _azure-example-network_ blueprints are supposed to be already installed in Cloudify Manager before deploying this blueprint. This setting can be modified by changing a value of an `use_existing_network_deployment`.

## Compatibility

Tested with:
  * Cloudify 4.5.5

## Pre-installation steps

Upload the required plugins:

  * [Azure Plugin](https://github.com/cloudify-incubator/cloudify-azure-plugin/releases/tag/2.1.1),
  * [OpenStack Plugin](https://github.com/cloudify-cosmo/cloudify-openstack-plugin/releases/tag/2.14.7),
  * [Utilities Plugin](https://github.com/cloudify-incubator/cloudify-utilities-plugin/releases/tag/1.11.2).

_Check the blueprint for the exact version of the plugin._

You must have these secrets on your Cloudify Manager `tenant`:
  * When deploying on *Azure*:
    * `azure_subscription_id`
    * `azure_tenant_id`
    * `azure_client_id`
    * `azure_client_secret`
    * `azure_location`
    * `resource_prefix`
    * `resource_suffix`.
  * When deploying on *OpenStack*:
    * `keystone_username`
    * `keystone_password`
    * `keystone_tenant_name`
    * `keystone_url`
    * `keystone_region`
  * In both use cases:
    * `agent_key_public`
    * `agent_key_private`

## Installation

Upload the blueprint, create the deployment and execute install workflow in one command using the CLI:

```bash
cfy install {{chosen IaaS}}.yaml
```

## Uninstallation

Navigate to the deployment and select `Uninstall`. When the uninstall workflow is finished, select `Delete deployment`. Or use the CLI:

```bash
cfy uninstall multicloud-infra-vm
```
