Terraform Provider
==================

- Website: https://www.terraform.io
- [![Gitter chat](https://badges.gitter.im/hashicorp-terraform/Lobby.png)](https://gitter.im/hashicorp-terraform/Lobby)
- Mailing list: [Google Groups](http://groups.google.com/group/terraform-tool)

<img src="https://cdn.rawgit.com/hashicorp/terraform-website/master/content/source/assets/images/logo-hashicorp.svg" width="600px">

Requirements
------------

-	[Terraform](https://www.terraform.io/downloads.html) 0.10.x
-	[Go](https://golang.org/doc/install) 1.8 (to build the provider plugin)

Downloading and install Go
---------------------

At the time of writing this article, the latest stable version of Go is version 1.13. Before downloading the tarball, visit the official Go [downloads page](https://golang.org/dl/) and check if there is a new version available.
To download the Go binary, you can use either [wget](https://linuxize.com/post/wget-command-examples/) or [curl](https://linuxize.com/post/curl-command-examples/):
```sh
$ wget https://dl.google.com/go/go1.13.linux-amd64.tar.gz
```
#### Extracting the Go tarball

Use [tar to extract](https://linuxize.com/post/how-to-create-and-extract-archives-using-the-tar-command-in-linux/) the tarball to the /usr/local directory:
```sh
$ sudo tar -C /usr/local -xzf go1.13.linux-amd64.tar.gz
```

Building The Provider
---------------------

Clone repository to: `$GOPATH/src/github.com/terraform-providers/terraform-provider-$PROVIDER_NAME`

```sh
$ mkdir -p $GOPATH/src/github.com/terraform-providers; cd $GOPATH/src/github.com/terraform-providers
$ git clone git@github.com:terraform-providers/terraform-provider-$PROVIDER_NAME
```

Enter the provider directory and build the provider

```sh
$ cd $GOPATH/src/github.com/terraform-providers/terraform-provider-$PROVIDER_NAME
$ make build
```

Using the provider
----------------------

See the [DigitalOcean Provider documentation](https://www.terraform.io/docs/providers/do/index.html) to get started using the DigitalOcean provider.

Developing the Provider
---------------------------

If you wish to work on the provider, you'll first need [Go](http://www.golang.org) installed on your machine (version 1.8+ is *required*). You'll also need to correctly setup a [GOPATH](http://golang.org/doc/code.html#GOPATH), as well as adding `$GOPATH/bin` to your `$PATH`.

To compile the provider, run `make build`. This will build the provider and put the provider binary in the `$GOPATH/bin` directory.

```sh
$ make build
...
$ $GOPATH/bin/terraform-provider-$PROVIDER_NAME
...
```

In order to test the provider, you can simply run `make test`.

```sh
$ make test
```

In order to run the full suite of Acceptance tests, run `make testacc`.

*Note:* Acceptance tests create real resources, and often cost money to run.

```sh
$ make testacc
```
