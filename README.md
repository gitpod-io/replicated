# Replicated

[Replicated](https://vendor.replicated.com) is how we deliver Gitpod to enterprise
customers.

# Getting started

You will need:
 - a Kubernetes cluster
 - a Replicated license file

Go to [our Replicated channels page](https://vendor.replicated.com/apps/gitpod-pov/channels) and
follow the installation instructions on screen.

# Terminology

Replicated uses the Kots operator for delivering software.

# Development

## Authentication

Two environment variables are required to be able to publish to our Replicated account:

 - `REPLICATED_APP`: the unique application slug
 - `REPLICATED_API_TOKEN`: a [User API Token](https://vendor.replicated.com/account-settings) with `Read/Write` permissions

## Naming conventions

- Starts with `kots` - part of the Kots configuration. Typically, this will follow the Kots documentation/conventions
- Starts with `gitpod` - part of the Gitpod application. Typically, this will be something we define/own
- Starts with `helm` - a Helm chart
- Starts with `crd` - a Custom Resource Definition

## Helm charts

Kots [requires](https://kots.io/reference/v1beta1/helmchart) Helm charts to be uploaded as a `.tgz`
file. The `make helm` command iterates through everything inside `charts`, installs the dependencies
and packages them up as a `.tgz` file.

The `.tgz` files should not be committed to the repository.

## Create an unstable release

An unstable release can be created by running `make create_unstable_release`. This builds and publishes
a new unstable release to the account. This can be then applied to your development cluster.
