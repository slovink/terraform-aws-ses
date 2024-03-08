<<p align="center"> <img src="https://user-images.githubusercontent.com/50652676/62349836-882fef80-b51e-11e9-99e3-7b974309c7e3.png" width="100" height="100"></p>


<h1 align="center">
    Terraform AWS  SES
</h1>


<p align="center">

<a href="https://www.terraform.io">
  <img src="https://img.shields.io/badge/Terraform-v1.7.0-green" alt="Terraform">
</a>
<a href="https://github.com/slovink/terraform-aws-ses/blob/vinod/LICENSE">
  <img src="https://img.shields.io/badge/License-APACHE-blue.svg" alt="Licence">
</a>



</p>
<p align="center">

<a href='https://www.facebook.com/Slovink.in=https://github.com/slovink/terraform-aws-ses'>
  <img title="Share on Facebook" src="https://user-images.githubusercontent.com/50652676/62817743-4f64cb80-bb59-11e9-90c7-b057252ded50.png" />
</a>
<a href='https://www.linkedin.com/company/101534993/admin/feed/posts/=https://github.com/slovink/terraform-aws-ses'>
  <img title="Share on LinkedIn" src="https://user-images.githubusercontent.com/50652676/62817742-4e339e80-bb59-11e9-87b9-a1f68cae1049.png" />
</a>



- [Introduction](#introduction)
- [Usage](#usage)
- [Module Inputs](#module-inputs)
- [Module Outputs](#module-outputs)
- [Examples](#examples)
- [License](#license)



## Prerequisites

This module has a few dependencies:

- [Terraform 1.x.x](https://learn.hashicorp.com/terraform/getting-started/install.html)
- [Go](https://golang.org/doc/install)



## Examples
For detailed examples on how to use this module, please refer to the [Examples](https://github.com/slovink/terraform-aws-ses/tree/vinod/_example) directory within this repository.

## License
This Terraform module is provided under the '[License Name]' License. Please see the [LICENSE](https://github.com/slovink/terraform-aws-ses/blob/vinod/LICENSE) file for more details.



### Simple Example
Here is an example of how you can use this module in your inventory structure:
  ```hcl

module "ses" {
  source = "https://github.com/slovink/terraform-aws-ses.git?ref=v1.0.0"

  name        = "ses"
  environment = "example"
  label_order = ["name", "environment"]

  domain   = ""
  iam_name = "ses-user1"

  enable_verification = false
  enable_mx           = false
  enable_spf_domain   = false
}

  ```



## Feedback
If you come accross a bug or have any feedback, please log it in our [issue tracker](https://github.com/slovink/terraform-aws-ses/issues), or feel free to drop us an email at [contact@slovink.com](contact@slovink.com).

If you have found it worth your time, go ahead and give us a ★ on [our GitHub](https://github.com/slovink/terraform-aws-ses)!
<!-- BEGIN_TF_DOCS -->
## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 1.6.4, < 1.7.0 |
| <a name="requirement_aws"></a> [aws](#requirement\_aws) | >= 5.13.1 |
| <a name="requirement_tls"></a> [tls](#requirement\_tls) | >= 4.0 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aws"></a> [aws](#provider\_aws) | >= 5.13.1 |

## Modules

| Name | Source | Version |
|------|--------|---------|
| <a name="module_labels"></a> [labels](#module\_labels) | git::git@github.com:slovink/terraform-aws-labels.git | 1.0.0 |

## Resources

| Name | Type |
|------|------|
| [aws_iam_access_key.default](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_access_key) | resource |
| [aws_iam_user.default](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_user) | resource |
| [aws_iam_user_policy.default](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_user_policy) | resource |
| [aws_route53_record.dkim](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/route53_record) | resource |
| [aws_route53_record.mx_receive](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/route53_record) | resource |
| [aws_route53_record.mx_send_mail_from](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/route53_record) | resource |
| [aws_route53_record.ses_verification](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/route53_record) | resource |
| [aws_route53_record.spf_domain](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/route53_record) | resource |
| [aws_route53_record.spf_mail_from](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/route53_record) | resource |
| [aws_ses_domain_dkim.default](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ses_domain_dkim) | resource |
| [aws_ses_domain_identity.default](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ses_domain_identity) | resource |
| [aws_ses_domain_identity_verification.default](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ses_domain_identity_verification) | resource |
| [aws_ses_domain_mail_from.default](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ses_domain_mail_from) | resource |
| [aws_ses_identity_policy.default](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ses_identity_policy) | resource |
| [aws_ses_receipt_filter.default](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ses_receipt_filter) | resource |
| [aws_ses_template.default](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ses_template) | resource |
| [aws_iam_policy_document.allow_iam_name_to_send_emails](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/iam_policy_document) | data source |
| [aws_iam_policy_document.document](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/iam_policy_document) | data source |
| [aws_region.current](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/region) | data source |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_cname_type"></a> [cname\_type](#input\_cname\_type) | CNAME type for Record Set. | `string` | `"CNAME"` | no |
| <a name="input_domain"></a> [domain](#input\_domain) | Domain to use for SES. | `string` | n/a | yes |
| <a name="input_enable_domain"></a> [enable\_domain](#input\_enable\_domain) | Control whether or not to enable domain. | `bool` | `true` | no |
| <a name="input_enable_filter"></a> [enable\_filter](#input\_enable\_filter) | Control whether or not to enable receipt filter. | `bool` | `false` | no |
| <a name="input_enable_mail_from"></a> [enable\_mail\_from](#input\_enable\_mail\_from) | Control whether or not to enable mail from domain. | `bool` | `false` | no |
| <a name="input_enable_mx"></a> [enable\_mx](#input\_enable\_mx) | Control whether or not to enable mx DNS recodrds. | `bool` | `false` | no |
| <a name="input_enable_policy"></a> [enable\_policy](#input\_enable\_policy) | Control whether identity policy create for SES. | `bool` | `false` | no |
| <a name="input_enable_spf_domain"></a> [enable\_spf\_domain](#input\_enable\_spf\_domain) | Control whether or not to enable enable spf domain. | `bool` | `false` | no |
| <a name="input_enable_template"></a> [enable\_template](#input\_enable\_template) | Control whether create a template for emails. | `bool` | `false` | no |
| <a name="input_enable_verification"></a> [enable\_verification](#input\_enable\_verification) | Control whether or not to verify SES DNS records. | `bool` | `false` | no |
| <a name="input_enabled"></a> [enabled](#input\_enabled) | Boolean indicating whether or not to create sns module. | `bool` | `true` | no |
| <a name="input_environment"></a> [environment](#input\_environment) | Environment (e.g. `prod`, `dev`, `staging`). | `string` | `""` | no |
| <a name="input_filter_cidr"></a> [filter\_cidr](#input\_filter\_cidr) | The IP address or address range to filter, in CIDR notation. | `string` | `""` | no |
| <a name="input_filter_policy"></a> [filter\_policy](#input\_filter\_policy) | Block or Allow filter. | `string` | `""` | no |
| <a name="input_iam_name"></a> [iam\_name](#input\_iam\_name) | IAM username. | `string` | `""` | no |
| <a name="input_label_order"></a> [label\_order](#input\_label\_order) | Label order, e.g. `name`,`application`. | `list(any)` | `[]` | no |
| <a name="input_mail_from_domain"></a> [mail\_from\_domain](#input\_mail\_from\_domain) | Subdomain (of the route53 zone) which is to be used as MAIL FROM address. | `string` | `""` | no |
| <a name="input_managedby"></a> [managedby](#input\_managedby) | ManagedBy, eg 'slovink' | `string` | `"hello@slovink.com"` | no |
| <a name="input_mx_type"></a> [mx\_type](#input\_mx\_type) | MX type for Record Set. | `string` | `"MX"` | no |
| <a name="input_name"></a> [name](#input\_name) | Name  (e.g. `app` or `cluster`). | `string` | `""` | no |
| <a name="input_repository"></a> [repository](#input\_repository) | Terraform current module repo | `string` | `"https://github.com/slovink/terrafrom-aws-ses.git"` | no |
| <a name="input_template_html"></a> [template\_html](#input\_template\_html) | The HTML body of the email. Must be less than 500KB in size, including both the text and HTML parts. | `string` | `""` | no |
| <a name="input_template_subject"></a> [template\_subject](#input\_template\_subject) | The subject line of the email. | `string` | `""` | no |
| <a name="input_text"></a> [text](#input\_text) | The email body that will be visible to recipients whose email clients do not display HTML. | `string` | `""` | no |
| <a name="input_txt_type"></a> [txt\_type](#input\_txt\_type) | Txt type for Record Set. | `string` | `"TXT"` | no |
| <a name="input_zone_id"></a> [zone\_id](#input\_zone\_id) | Route53 host zone ID to enable SES. | `string` | `""` | no |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_domain_identity_arn"></a> [domain\_identity\_arn](#output\_domain\_identity\_arn) | ARN of the SES domain identity. |
| <a name="output_id"></a> [id](#output\_id) | The domain name of the domain identity. |
<!-- END_TF_DOCS -->
