---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "confluent_invitation Data Source - terraform-provider-confluent"
subcategory: ""
description: |-
   
---

# confluent_invitation Data Source

[![General Availability](https://img.shields.io/badge/Lifecycle%20Stage-General%20Availability-%2345c6e8)](https://docs.confluent.io/cloud/current/api.html#section/Versioning/API-Lifecycle-Policy)

`confluent_invitation` describes an Invitation data source.

## Example Usage

```terraform
provider "confluent" {
  cloud_api_key    = var.confluent_cloud_api_key    # optionally use CONFLUENT_CLOUD_API_KEY env var
  cloud_api_secret = var.confluent_cloud_api_secret # optionally use CONFLUENT_CLOUD_API_SECRET env var
}

data "confluent_invitation" "main" {
  id = "i-gxxn1"
}

output "invitation" {
  value = data.confluent_invitation.main
}
```

<!-- schema generated by tfplugindocs -->
## Argument Reference

The following arguments are supported:

- `id` - (Required String) The ID of the Invitation, for example, `i-zyw30`.

## Attributes Reference

In addition to the preceding arguments, the following attributes are exported:

- `email` - (Required String) The user/invitee's email address.
- `status` - (Optional String) The status of invitations. Accepted values are: `INVITE_STATUS_SENT`,`INVITE_STATUS_STAGED`,`INVITE_STATUS_ACCEPTED`,`INVITE_STATUS_EXPIRED`, and `INVITE_STATUS_DEACTIVATED`.
- `auth_type` - (Optional String) Accepted values are: `AUTH_TYPE_LOCAL` and `AUTH_TYPE_SSO`. The user/invitee's authentication type. Note that only the [`OrganizationAdmin role`](https://docs.confluent.io/cloud/current/access-management/access-control/cloud-rbac.html#organizationadmin) can invite AUTH_TYPE_LOCAL users to SSO organizations. The user's auth_type is set as AUTH_TYPE_SSO by default if the organization has SSO enabled. Otherwise, the user's auth_type is AUTH_TYPE_LOCAL by default.
- `accepted_at` - (Optional String) The timestamp that the invitation was accepted.
- `expires_at` - (Optional String) The timestamp that the invitation will expire.
- `user` - (Required Configuration Block) supports the following:
  - `id` - (Required String) The id of user/invitee.
- `creator` - (Required Configuration Block) supports the following:
  - `id` - (Required String) The id of invitation creator.