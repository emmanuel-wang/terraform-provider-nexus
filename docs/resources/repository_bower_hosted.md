---
page_title: "Resource nexus_repository_bower_hosted"
subcategory: "Repository"
description: |-
  Use this resource to create a hosted Bower repository.
---
# Resource nexus_repository_bower_hosted
Use this resource to create a hosted Bower repository.
## Example Usage
```terraform
resource "nexus_repository_bower_hosted" "internal" {
  name   = "bower-internal"
  online = true

  storage {
    blob_store_name                = "default"
    strict_content_type_validation = true
    write_policy                   = "ALLOW"
  }
}
```
<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `name` (String) A unique identifier for this repository
- `storage` (Block List, Min: 1, Max: 1) The storage configuration of the repository (see [below for nested schema](#nestedblock--storage))

### Optional

- `cleanup` (Block List) Cleanup policies (see [below for nested schema](#nestedblock--cleanup))
- `component` (Block List, Max: 1) Component configuration for the hosted repository (see [below for nested schema](#nestedblock--component))
- `online` (Boolean) Whether this repository accepts incoming requests

### Read-Only

- `id` (String) Used to identify resource at nexus

<a id="nestedblock--storage"></a>
### Nested Schema for `storage`

Required:

- `blob_store_name` (String) Blob store used to store repository contents
- `strict_content_type_validation` (Boolean) Whether to validate uploaded content's MIME type appropriate for the repository format

Optional:

- `write_policy` (String) Controls if deployments of and updates to assets are allowed


<a id="nestedblock--cleanup"></a>
### Nested Schema for `cleanup`

Optional:

- `policy_names` (Set of String) List of policy names


<a id="nestedblock--component"></a>
### Nested Schema for `component`

Required:

- `proprietary_components` (Boolean) Components in this repository count as proprietary for namespace conflict attacks (requires Sonatype Nexus Firewall)
## Import
Import is supported using the following syntax:
```shell
# import using the name of repository
terraform import nexus_repository_bower_hosted.internal bower-internal
```