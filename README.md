# Ansible Role: artifactory_exporter

## Description

Deploy prometheus [artifactory_exporter](https://github.com/peimanja/artifactory_exporter) using ansible.

## Requirements

- Ansible >= 2.9 (It might work on previous versions, but we cannot guarantee it)

## Role Variables

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) file as well as in table below.

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| `artifactory_exporter_version` | 0.5.1 | artifactory_exporter package version |
| `artifactory_exporter_web_listen_address` | "0.0.0.0:9531" | Address on which artifactory_exporter will listen |
| `artifactory_scrape_uri` | http://localhost:8081/artifactory | URI of the Artifactory instance |
| `artifactory_auth` | basic | Authentication method to use [basic|token] |
| `artifactory_user` | prometheus | User to access Artifactory (artifactory_auth=basic) |
| `artifactory_password` | 'ChangeMe' | Password of the user accessing Artifactory (artifactory_auth=basic) |
| `artifactory_bearer_token` | xxxxxxxxxxxxxxxxxxxxx | Access token for accessing Artifactory (artifactory_auth=token) |
| `artifactory_ssl_verify` | false | Verify SSL certificate if HTTPS is used |
| `artifactory_timeout` | 5s | Scrap Timeout |
| `artifactory_exporter_config_flags_extra` | {} | Additional configuration flags passed at startup to artifactory_exporter binary |


## Example

### Playbook

Use it in a playbook as follows:
```yaml
- hosts: all
  roles:
    - artifactory_exporter
  vars:
    artifactory_scrape_uri: http://artifactory.example.com:8080
```
