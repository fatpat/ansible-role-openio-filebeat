[![Build Status](https://travis-ci.org/open-io/ansible-role-openio-filebeat.svg?branch=master)](https://travis-ci.org/open-io/ansible-role-openio-filebeat)
# Ansible role `filebeat`

An Ansible role for install filebeat. Specifically, the responsibilities of this role are to:

- install and configure filebeat

## Requirements

- Ansible 2.9+

## Role Variables

| Variable   | Default | Comments (type)  |
| :---       | :---    | :---             |
| `openio_filebeat_namespace` | `"{{ namespace \| d('OPENIO') }}"` | OpenIO Namespace |
| `openio_filebeat_maintenance_mode` | `"{{ openio_maintenance_mode \| d(false) }}"` | Maintenance mode |
| `openio_filebeat_elasticsearch_group` | `elasticsearch` | Elasticsearch group in the inventory |
| `openio_filebeat_elasticsearch_port` | `6904` | Default port to connect to elasticsearch |
| `openio_filebeat_elasticsearch_hosts` |`generated from `openio_filebeat_elasticsearch_group` | The list of the ES hosts |
| `openio_filebeat_input_options:` | `` | List of options to apply to each input |
| `openio_filebeat_custom_inputs` | `[]` | List of customs input, see `openio_filebeat_default_inputs` for syntax |
| `openio_filebeat_openio_log_path` | `"/var/log/oio/sds/{{ openio_filebeat_namespace }}"` | Base directory of logs to parse |
| `openio_filebeat_default_inputs:` | `` | Default inputs|
| `openio_filebeat_inputs` | `"{{ openio_filebeat_default_inputs + openio_filebeat_custom_inputs }}"` | The actual inputs that is used in the configuration file template |


## Dependencies
- https://github.com/open-io/ansible-role-openio-service

## Example Playbook

```yaml
- hosts: all
  gather_facts: true
  become: true

  tasks:
    - include_role:
        name: filebeat
```

## Contributing

Issues, feature requests, ideas are appreciated and can be posted in the Issues section.

Pull requests are also very welcome.
The best way to submit a PR is by first creating a fork of this Github project, then creating a topic branch for the suggested change and pushing that branch to your own fork.
Github can then easily create a PR based on that branch.

## License
Copyright (C) 2015-2020 OpenIO SAS
