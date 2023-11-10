# Publish a crate on crates.io

## Prerequisites

- GitHub account (prereq for account on crates.io)
- Account on crates.io to acquire an API token
- Define the version to publish
- Check your Cargo.toml and ensure the settings are correct / meaningful:
  - name 
  - version
  - description
  - categories
  - keywords
  - homepage
  - documentation
  - repository
  - readme
  - license or license-file

## Pre-flight Checklist

- Main branch is up-to-date with remote repo
- Double check version in Cargo.toml
- Documentation:
  - From the project root, run *cargo doc*
  - Review docs locally
- Review *cargo package --list*
- Publishing Dryrun:
  - *cargo publish --dry-run*
  - Resolve any issues

## Release on GitHub

- Create a tag with pattern vx.y.z
- Release title: <project-name>-vx.y.z
- Write some release notes, mainly inspired by roadmap and git log

## Publish on crates.io

- Run *cargo login* (puts the API token in *~/.cargo/credentials*, which is not cryptographically secured!)
- Run *cargo publish* 
- Run *cargo logout* (removes the API token from *~/.cargo/credentials* (only available on nightly!))

# Links

[The Cargo Book: Publishing on crates.io](https://doc.rust-lang.org/cargo/reference/publishing.html)
