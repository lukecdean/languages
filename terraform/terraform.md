# Terraform
- ```terraform init``` Initializing a configuration directory downloads and installs the providers defined in the configuration
- .terraform.lock.hcl: Include this file in your version control repository
- terraform fmt: formats
- terraform validate: validates syntax and checks internal consistency
- terraform apply: will print out the execution plan
  - steps to modify your infrastructure to match the config
  - 'yes' to confirm
  - it is safe to abort here
- terraform.tfstate
  - stores IDs and properties of resources so it can update/destroy them
  - store securely [remote backend page](https://developer.hashicorp.com/terraform/language/settings/backends/configuration)
- terraform show: inspect current state
- terraform state: advanced state management
  - terraform state list: lists resources in proj's state
- terraform destroy: terminates the resources managed by this terraform config
  - shows plan and asks for confirmation like apply
  - destroys dependecies in order
- [variables in terraform](https://developer.hashicorp.com/terraform/tutorials/configuration-language/variables)
- terraform outputs: displays declared outputs
  - declared with output blocks
## backend
- specify with a ```backend block```
- when changing backend config, must run ```terraform init``` again before any plan, applys, etc
  - ```init``` creates a config in ```.terraform/```
    - do not check this in to git
    - this is separate from ```terraform.tfstate```
  - when changing backends, terraform asks if you want to migrate state to the new backend
    - backup current state before doing this
- backend config file
  - *.backendname.tfbackend
  - uses top level attributes to specify
```
address = "demo.consul.io"
path    = "example_app/terraform_state"
scheme  = "https"
```
