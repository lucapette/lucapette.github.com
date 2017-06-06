---
title: "terraform and GitHub labels"
description: A short introduction to terraform
keywords: terraform, operations, github
layout: articles
category: go
---

`terraform` is a fantastic tool to _"[Write, Plan, and Create infrastructure as
code](https://www.terraform.io/)"_. I have been playing around with it for more
than one year and decided to write about it because [twitter's
friends](https://twitter.com/lucapette/status/868106620492029956) said it was a
good idea.

The basic idea behind `terraform` is brilliant and simple: you describe your
infrastructure using a little language called
[hcl](https://github.com/hashicorp/hcl) and then use `terraform` to `apply`
your changes. The thing that strikes me the most is how productive you can be
using `terraform`. To get started, you only need to learn about how
configuration is done via
[resources](https://www.terraform.io/docs/configuration/resources.html). A
resource represents one component in your infrastructure, `terraform` provides
a great number of
[providers](https://www.terraform.io/docs/providers/index.html) to interact
with different APIs (things like AWS, DNSimple, CloudFlare and so on). You
describe your infrastructure by describing your resources.

In the past few weeks, something silly started bugging me: I have multiple
GitHub projects that share the same naming for labels. As I created those
labels manually over time, different projects have the same labels with
different colors. It's a small thing, but it hurts my visual memory and I
don't want to manually sync them. Fortunately, `terraform` has a
[GitHub](https://www.terraform.io/docs/providers/github/index.html) provider
that exposes a
[github\_issue\_label](https://www.terraform.io/docs/providers/github/r/issue\_label.html)
resource. A few days ago, I decided to try syncing labels using `terraform`.
It took literally two minutes to implement a first working configuration.

I created a `config.tf` that looks like this:

```tf
provider "github" {
  token = "REAL TOKEN HERE"
  organization = "lucapette"
}
```

and a `github.tf` file that looked like this:

```tf
resource "github_issue_label" "fakedata-gardening-label" {
  repository = "fakedata"
  name       = "gardening"
  color      = "006b75"
}

resource "github_issue_label" "fakedata-bug-label" {
  repository = "fakedata"
  name       = "bug"
  color      = "ee0701"
}

// more resources like those...
```

I ran `terraform apply` and a few seconds later
[fakedata](https://github.com/lucapette/fakedata) had labels properly
configured. It felt like magic! Just a note: running `terraform apply` will
either create or update a `terraform.tfstate`, which contains an up-to-date
version of the infrastructure. I think it makes sense to commit this file. I did
not look into good practices yet, so take the advice with a grain of salt. Of
course, the point of this experiment was to sync labels within multiple GitHub
projects. I could have replicated the `github_issue_labels` with a copy and
paste and call it a day: it surely works that way, but it's not the most
maintainable approach. Furthermore, writing the configuration manually is a
pretty boring task. While reading the documentation, I ran into
[meta-parameters](https://www.terraform.io/docs/configuration/resources.html#meta\-parameters),
which are parameters available to all the resources. With the help of the
`count` parameter and some syntax, I wrote the following:

```tf
variable repositories {
  default = {
    "0" = "fakedata"
    "1" = "another project here"
  }
}

resource "github_issue_label" "gardening-label" {
  count = "${length(var.repositories)}"
  repository = "${lookup(var.repositories, count.index)}"
  name       = "gardening"
  color      = "006b75"
}

resource "github_issue_label" "bug-label" {
  count = "${length(var.repositories)}"
  repository = "${lookup(var.repositories, count.index)}"
  name       = "bug"
  color      = "ee0701"
}

// more resources like those
```

I ran `terraform apply` once more and I had all the labels synced within
multiple projects. To recap, the entire process consisted of the following
steps:

- quick read of the documentation
- writing a first configuration
- running `terraform apply`
- writing a more general configuration
- running `terraform apply`

It took around 10 minutes from the idea to a fully automated configuration of
GitHub labels.
[Here](https://gist.github.com/lucapette/962d0cafe7edfceb9c2ba97bf7b6948f) is
the entire file if you're curious.

Of course, this was so trivial one could do it with a shell script, but I
believe it shows the huge potential of this wonderful tool. I suggest you have
a look at the providers and the syntax, because there's much more than this
simple use case I just showed you here. One great feature is [terraform
import](https://www.terraform.io/docs/import/index.html), which can help a
great deal with adoption.

Happy terraforming!
