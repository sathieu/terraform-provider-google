---
# ----------------------------------------------------------------------------
#
#     ***     AUTO GENERATED CODE    ***    Type: MMv1     ***
#
# ----------------------------------------------------------------------------
#
#     This file is automatically generated by Magic Modules and manual
#     changes will be clobbered when the file is regenerated.
#
#     Please read more about how to change this file in
#     .github/CONTRIBUTING.md.
#
# ----------------------------------------------------------------------------
subcategory: "Artifact Registry"
page_title: "Google: google_artifact_registry_repository"
description: |-
  A repository for storing artifacts
---

# google\_artifact\_registry\_repository

A repository for storing artifacts


To get more information about Repository, see:

* [API documentation](https://cloud.google.com/artifact-registry/docs/reference/rest/v1/projects.locations.repositories)
* How-to Guides
    * [Official Documentation](https://cloud.google.com/artifact-registry/docs/overview)

<div class = "oics-button" style="float: right; margin: 0 0 -15px">
  <a href="https://console.cloud.google.com/cloudshell/open?cloudshell_git_repo=https%3A%2F%2Fgithub.com%2Fterraform-google-modules%2Fdocs-examples.git&cloudshell_working_dir=artifact_registry_repository_basic&cloudshell_image=gcr.io%2Fgraphite-cloud-shell-images%2Fterraform%3Alatest&open_in_editor=main.tf&cloudshell_print=.%2Fmotd&cloudshell_tutorial=.%2Ftutorial.md" target="_blank">
    <img alt="Open in Cloud Shell" src="//gstatic.com/cloudssh/images/open-btn.svg" style="max-height: 44px; margin: 32px auto; max-width: 100%;">
  </a>
</div>
## Example Usage - Artifact Registry Repository Basic


```hcl
resource "google_artifact_registry_repository" "my-repo" {
  location      = "us-central1"
  repository_id = "my-repository"
  description   = "example docker repository"
  format        = "DOCKER"
}
```
<div class = "oics-button" style="float: right; margin: 0 0 -15px">
  <a href="https://console.cloud.google.com/cloudshell/open?cloudshell_git_repo=https%3A%2F%2Fgithub.com%2Fterraform-google-modules%2Fdocs-examples.git&cloudshell_working_dir=artifact_registry_repository_cmek&cloudshell_image=gcr.io%2Fgraphite-cloud-shell-images%2Fterraform%3Alatest&open_in_editor=main.tf&cloudshell_print=.%2Fmotd&cloudshell_tutorial=.%2Ftutorial.md" target="_blank">
    <img alt="Open in Cloud Shell" src="//gstatic.com/cloudssh/images/open-btn.svg" style="max-height: 44px; margin: 32px auto; max-width: 100%;">
  </a>
</div>
## Example Usage - Artifact Registry Repository Cmek


```hcl
resource "google_artifact_registry_repository" "my-repo" {
  location      = "us-central1"
  repository_id = "my-repository"
  description   = "example docker repository with cmek"
  format        = "DOCKER"
  kms_key_name  = "kms-key"
}
```

## Argument Reference

The following arguments are supported:


* `repository_id` -
  (Required)
  The last part of the repository name, for example:
  "repo1"

* `format` -
  (Required)
  The format of packages that are stored in the repository. Supported formats
  can be found [here](https://cloud.google.com/artifact-registry/docs/supported-formats).
  You can only create alpha formats if you are a member of the
  [alpha user group](https://cloud.google.com/artifact-registry/docs/supported-formats#alpha-access).


- - -


* `location` -
  (Optional)
  The name of the location this repository is located in.

* `description` -
  (Optional)
  The user-provided description of the repository.

* `labels` -
  (Optional)
  Labels with user-defined metadata.
  This field may contain up to 64 entries. Label keys and values may be no
  longer than 63 characters. Label keys must begin with a lowercase letter
  and may only contain lowercase letters, numeric characters, underscores,
  and dashes.

* `kms_key_name` -
  (Optional)
  The Cloud KMS resource name of the customer managed encryption key that’s
  used to encrypt the contents of the Repository. Has the form:
  `projects/my-project/locations/my-region/keyRings/my-kr/cryptoKeys/my-key`.
  This value may not be changed after the Repository has been created.

* `maven_config` -
  (Optional)
  MavenRepositoryConfig is maven related repository details.
  Provides additional configuration details for repositories of the maven
  format type.
  Structure is [documented below](#nested_maven_config).

* `project` - (Optional) The ID of the project in which the resource belongs.
    If it is not provided, the provider project is used.


<a name="nested_maven_config"></a>The `maven_config` block supports:

* `allow_snapshot_overwrites` -
  (Optional)
  The repository with this flag will allow publishing the same
  snapshot versions.

* `version_policy` -
  (Optional)
  Version policy defines the versions that the registry will accept.
  Default value is `VERSION_POLICY_UNSPECIFIED`.
  Possible values are `VERSION_POLICY_UNSPECIFIED`, `RELEASE`, and `SNAPSHOT`.

## Attributes Reference

In addition to the arguments listed above, the following computed attributes are exported:

* `id` - an identifier for the resource with format `projects/{{project}}/locations/{{location}}/repositories/{{repository_id}}`

* `name` -
  The name of the repository, for example:
  "projects/p1/locations/us-central1/repositories/repo1"

* `create_time` -
  The time when the repository was created.

* `update_time` -
  The time when the repository was last updated.


## Timeouts

This resource provides the following
[Timeouts](/docs/configuration/resources.html#timeouts) configuration options:

- `create` - Default is 20 minutes.
- `update` - Default is 20 minutes.
- `delete` - Default is 20 minutes.

## Import


Repository can be imported using any of these accepted formats:

```
$ terraform import google_artifact_registry_repository.default projects/{{project}}/locations/{{location}}/repositories/{{repository_id}}
$ terraform import google_artifact_registry_repository.default {{project}}/{{location}}/{{repository_id}}
$ terraform import google_artifact_registry_repository.default {{location}}/{{repository_id}}
$ terraform import google_artifact_registry_repository.default {{repository_id}}
```

## User Project Overrides

This resource supports [User Project Overrides](https://www.terraform.io/docs/providers/google/guides/provider_reference.html#user_project_override).
