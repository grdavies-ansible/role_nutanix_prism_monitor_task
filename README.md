# Nutanix Role for Prism Element or Central Task Monitoring

This Ansible role will check the status of a specific task UUID for a number of retries with a defined delay between each retry.

## Input Variables

| Variable                                            | Required | Default | Choices                                                                         | Comments                                                                                                                                           |
|-----------------------------------------------------|----------|---------|---------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| role_nutanix_prism_monitor_task_host                | yes      |         |                                                                                 | The IP address or FQDN for the Prism (Element or Central) to which you want to connect.                                                            |
| role_nutanix_prism_monitor_task_host_username       | yes      |         |                                                                                 | A valid username with appropriate rights to access the Nutanix API.                                                                                |
| role_nutanix_prism_monitor_task_host_password       | yes      |         |                                                                                 | A valid password for the supplied username.                                                                                                        |
| role_nutanix_prism_monitor_task_host_port           | no       | 9440    |                                                                                 | The Prism TCP port.                                                                                                                                |
| role_nutanix_prism_monitor_task_host_validate_certs | no       | false   | true / false                                                                    | Whether to check if Prism UI certificates are valid.                                                                                               |
| role_nutanix_prism_monitor_task_debug               | no       | false   | true / false                                                                    | Enable debug loggingd.                                                                                                                             |
| role_nutanix_prism_monitor_task_uuid                | yes      | ""      |                                                                                 | UUID of task to be monitored                                                                                                                       |
| role_nutanix_prism_monitor_task_retries             | no       | 60      |                                                                                 | The number of times to check the task status                                                                                                       |
| role_nutanix_prism_monitor_task_retry_delay         | no       | 60      |                                                                                 | The amount of time in seconds between each poll for task status                                                                                    |
| role_nutanix_prism_monitor_task_allow_failure       | no       | false   | true / false                                                                    | Whether the nutanix task may fail (for example an LCM upgrade where the CVM hosting the API service gets restarted)                                |

## Returned Variables

| Variable                                | Values                                                                                 | Comments                                                                                                                                                                                                     |
|-----------------------------------------|----------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| role_nutanix_prism_monitor_task_result  |                                                                                        | Data for task that was monitored                                                                                                                                                                             |

## Dependencies

- grdavies.role_nutanix_prism_api

## Example Playbook

```
- hosts: localhost
  gather_facts: false
  roles:
    - role: grdavies.role_nutanix_prism_monitor_task
  vars:
    role_nutanix_prism_monitor_task_host: 10.38.185.37
    role_nutanix_prism_monitor_task_host_username: admin
    role_nutanix_prism_monitor_task_host_password: nx2Tech165!
    role_nutanix_prism_monitor_task_uuid: "3a54c168-b765-4ba3-4a15-5164dacf7064"
```

## License

See LICENSE.md

## Author Information

Ross Davies
