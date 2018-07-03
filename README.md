## Maru / EDR - Ansible Open Source Standards

Welcome to the Ansible OSS guide. This Github pages site serves as a living document for building EDR ready Ansible roles. It strives for best practices and uniformity between developed roles. Any developed roles should follow these principles:

* A role should be deployable as a stand alone unit
* A role should be single purpose
* A role should be fully documented - with example usage and variables defined

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
