Creates a deployment, or updates an existing one.

# Environment Variables

This Action uses the Cloudify Profile environment variables described in the official
Cloudify documentation (see [More Information](#more-information) below).

# Inputs

(Certain commonly-used inputs are documented in our official website; see [More Information](#more-information) below)

| Name | Description
|------|------------
| `blueprint-id` | The ID of the blueprint to create a deployment from, or to update an existing deployment to
| `delete-old-blueprint` | If true, and the deployment was updated, then delete the old blueprint in case no other deployments exist for it
| `inputs-file` | Path to YAML/JSON inputs file
| `skip-install` | If this is a deployment update, then skip the `install` operations
| `skip-uninstall` | If this is a deployment update, then skip the `uninstall` operations
| `skip-reinstall` | If this is a deployment update, then skip reinstalling node instances that require re-installation
| `install-first` | If this is a deployment update, then run `install` operations before `uninstall` ones

# Outputs

| Name | Description
|------|------------
| `environment-data` | The environment's data, as described in the official Cloudify documentation (see below)

If `outputs-file` is specified, then the environment's data is also written into that file.

# Example

```yaml
jobs:
  test_job:
    steps:
      - name: Get Environment Data
        uses: cloudify-cosmo/install-or-update@v1.1
        with:
          environment-name: "my-environment"
          blueprint-id: "my-blueprint"
          delete-old-blueprint: "true"
          outputs-file: env-data.json
```

# More Information

Refer to [Cloudify CI/CD Integration](https://docs.cloudify.co/latest/working_with/integration/) for additional information about
Cloudify's integration with CI/CD tools.
