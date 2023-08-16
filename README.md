# Nutanix Role for Prism Element or Central Task Monitoring

This Ansible role will check the status of a specific task UUID for a number of retries with a defined delay between each retry.

## Role Variables

| Variable                   | Required | Default | Choices                                                                         | Comments                                                                                                                                           |
|----------------------------|----------|---------|---------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| nutanix_host               | yes      |         |                                                                                 | The IP address or FQDN for the Prism (Element or Central) to which you want to connect.                                                            |
| nutanix_username           | yes      |         |                                                                                 | A valid username with appropriate rights to access the Nutanix API.                                                                                |
| nutanix_password           | yes      |         |                                                                                 | A valid password for the supplied username.                                                                                                        |
| nutanix_port               | no       | 9440    |                                                                                 | The Prism TCP port.                                                                                                                                |
| validate_certs             | no       | no      | yes / no                                                                        | Whether to check if Prism UI certificates are valid.                                                                                               |
| nutanix_task_uuid          | yes      | ""      |                                                                                 | UUID of task to be monitored                                                                                                                       |
| nutanix_task_retries       | no       | 60      |                                                                                 | The number of times to check the task status                                                                                                       |
| nutanix_task_retry_delay   | no       | 60      |                                                                                 | The amount of time in seconds between each poll for task status                                                                                    |
| nutanix_task_allow_failure | no       | no      | yes / no                                                                        | Whether the nutanix task may fail (for example an LCM upgrade where the CVM hosting the API service gets restarted)                                |

## Dependencies

## Example Playbook

```
- hosts: localhost
  gather_facts: false
  roles:
    - role: grdavies.role_nutanix_prism_monitor_task
  vars:
    nutanix_host: 10.38.185.37
    nutanix_password: admin
    nutanix_username: nx2Tech165!
    nutanix_task_uuid: "3a54c168-b765-4ba3-4a15-5164dacf7064"
```

## License

See LICENSE.md

## Author Information

Ross Davies
