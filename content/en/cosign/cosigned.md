---
title: "Cosigned Admission Controller"
category: "Cosign"
position: 102
---

The `cosigned` admission controller can be used to enforce policy on a Kubernetes cluster based on verifiable supply-chain metadata from `cosign`.
The webhook can be used to automatically validate that all the container images have been signed.
The webhook also resolves the image tags to ensure the image being ran is not different from when it was admitted.


This doc will guide you through:
* Installing cosigned in your Kubernetes cluster
* Setting up policy for the admission controller
* A quick demo

# Installation

There are two options for installing `cosigned`:
1. Install via the [`cosigned helm chart`](https://github.com/sigstore/helm-charts/tree/main/charts/cosigned)
2. Installing from source

## Install via helm


## Container Images

Signed release images are available at `gcr.io/projectsigstore/cosign`.
They are tagged with the release name (e.g. `gcr.io/projectsigstore/cosign:v1.0.0`).
They can be found with `crane ls`:

```shell
$ crane ls gcr.io/projectsigstore/cosign
sha256-7e9a6ca62c3b502a125754fbeb4cde2d37d4261a9c905359585bfc0a63ff17f4.sig
v0.4.0
...
```

CI Built containers are published for every commit at `gcr.io/projectsigstore/cosign/ci/cosign`.
They are tagged with the commit.
They can be found with `crane ls`:

```shell
$ crane ls gcr.io/projectsigstore/cosign/ci/cosign
749f896
749f896bb378aca5cb45c5154fc0cb43f6728d48
```

Further details and installation instructions for `crane` available here: https://github.com/google/go-containerregistry/tree/main/cmd/crane



# Setting up Policy


# Demo

## Usage



## Comparison with Similar Tools

# TODO


`cosigned` also resolves the image tags to ensure the image being ran is not different from when it was admitted.

See the [installation instructions](installation#cosigned) for more information on usage and configuration.

**This component is still actively under development!**

Today, `cosigned` can automatically validate signatures on container images.
Enforcement is configured on a per-namespace basis, and multiple keys are supported.

We're actively working on more features here, including support for Attestations.