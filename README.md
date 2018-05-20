# terraform-aws-ecs

Terraform module which creates AWS ECS resources

This module focuses purely on ECS and nothing else. Therefore only these resources can be created with this module:

* [ECS](https://www.terraform.io/docs/providers/aws/r/ecs_cluster.html)
* [IAM](https://www.terraform.io/docs/providers/aws/r/iam_instance_profile.html)

However, having said the above to have a proper ECS cluster up and running multiple resources are needed. In most cases creating these resources is heavily opinionated and or context-bound. That is why this module does not create these resources. But you still need them to have a production ready environment. Therefore the example area shows how to create everything needed for a production environment.

## Usage

```hcl
module "ecs" {
  source = "terraform-aws-modules/ecs/aws"

  name = "my-ecs"
}
```

## Conditional creation

Sometimes you need to have a way to create ECS resources conditionally but Terraform does not allow to use `count` inside `module` block, so the solution is to specify argument `create_ecs`.

```hcl
# ECS cluster will not be created
module "ecs" {
  source = "terraform-aws-modules/ecs/aws"

  create_ecs = false
  # ... omitted
}
```

## Examples

* [Complete ECS](https://github.com/terraform-aws-modules/terraform-aws-ecs/tree/master/examples/complete-ecs)

## License

Apache 2 Licensed. See LICENSE for full details.