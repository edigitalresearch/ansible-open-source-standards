# Maru / EDR - Ansible Open Source Standards

[https://edigitalresearch.github.io/ansible-open-source-standards/](https://edigitalresearch.github.io/ansible-open-source-standards/)

Welcome to the Ansible OSS guide. This Github pages site serves as a living document for building EDR ready Ansible roles. It strives for best practices and uniformity between developed roles. Any developed roles should follow these principles:

* A role should be deployable as a stand alone unit
* A role should be single purpose
* A role should be fully documented

This pages site serves as a living document and like all of our open source software pull requests are welcome. The information here is intended to evolve over time as we improve our development practices, as such there are no hard and fast rules. Use them as a guide and enjoy!

## Contents

1. Role Anatomy
1. Role Coding Style
  * Global Guidelines
  * Default Variables
  * Handlers
  * Task Definitions
  * Templates
1. Role Organisation
  * Task Separation
  * Task Naming
  * Adapting other roles
1. Role Documentation
  * README Template
1. Contributing to Maru EDR (OSS)
  * Expected Workflow
  * Reporting Issues
  * Licensing

### Role Anatomy - Minimum Viable Role (MVR)

All roles should use the following minimum file structure:

```
ansible-role-{role-name}
    - defaults
      - main.yml
    - handlers
      - main.yml
    - meta
      - main.yml
    - tasks
      - main.yml
    - templates
    - files
```

* `defaults` - Define default role variables. These should be complete environment agnostic and generic
* `handlers` - Contains service notifiers for restarting systemd controlled processes. This is optional and can be omitted if unused
* `meta` - Used for role ownership and authoring information on Ansible Galaxy
* `tasks` - Contains the main functions of the role. All tasks can be placed in one `main.yml` file or for larger roles should be broken up
* `templates` - Jinja2 template files for configuration generation. This is optional and can be omitted if unused.
* `files` - Used for static files - e.g shell scripts run by a role. **This should not contain anything related to templates!**.

### Role Coding Style

This section defines rules surrounding coding style. These are here for role continuity

#### Global Guidelines

* Name the role in the format - `ansible-role-{NAME}`. For example `ansible-role-sentry`
* Always provide a complete `README.md`. For example:
* Keep the `meta.yml` up to date
* Always create a tagged release on Github - This helps for Ansible Galaxy versioning
* When naming roles in Ansible Galaxy `requirements.yml` prefix with `edr.{name}`. For example:

```
- name: edr.sentry
  scm: git
  src: git@github.com:edigitalresearch/ansible-role-bind.git
```

#### Default Variables

*TBA*

#### Handlers

*TBA*

#### Task Definitions

*TBA*

#### Templates

*TBA*

### Role Organisation

How to organise your role code

#### Task Separation

*TBA*

#### Task Naming

*TBA*

#### Adapting other roles

*TBA*

### Role Documentation

Defining documentation standards

#### README Template

Use the following README template as a scaffold:

```
# {ROLE NAME} Role for Ansible
...

## Organising hosts
...

### Example Hosts file
...

## Variables
...

## Handlers
...

## Example Task with role
...
```

### Contributing to Maru EDR (OSS)

How to get involved

#### Expected Workflow

When starting a new role or improving an existing role we use the following process:

* Explore other available roles first - often times someone will have created one already. If you find a suitable role as a base please fork it and bring it in line with these standards. Otherwise create a new repo and follow these guidelines
* Always fork the repo from `edigitalresearch` before starting work - Once forked do not work on the master branch. Create a feature branch and do development work there
* Once ready for a release to your forked `master` branch - rebase first! Nobody likes lots of commits. Please squash them to a single release commit before merging to your master branch. See [https://www.atlassian.com/git/tutorials/merging-vs-rebasing](https://www.atlassian.com/git/tutorials/merging-vs-rebasing)
* Now your work is on your forked `master` open a PR back to the upstream
* Your PR should be reviewed by x2 reviewers before being merged. Reviewers use these notes for reference.
* When a PR has been merged - tag a new release on Github and close off any relevant issues.
* Rinse and repeat - Any forks should periodically pull changes from upstream before working on new features

#### Reporting Issues

* Do open up issues with the relevant role - any features or bug requests are welcome
* Keep the opened issue focused on a single role. Problems with dependent roles should be discussed elsewhere
* Ensure PR's have closing tags attached - For example if your PR fixes issue #1 ensure it has `Closes #1` in the PR body. That way onced merged we can close issues automatically

#### Licensing

All roles are licensed under MIT and should include a `LICENSE.md` within the role.
