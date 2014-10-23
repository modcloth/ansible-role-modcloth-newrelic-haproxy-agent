modcloth.newrelic_haproxy_agent
=========

This role installs and configures the Railsware New Relic HAProxy plugin.

Requirements
------------

Requires ruby to be installed.

Role Variables
--------------

```yml
newrelic_haproxy_agent_config_template: # template for config (default template is provided)

# variables for default config
new_relic_license_key: # NewRelic license key
newrelic_haproxy_agent_verbose: # 0 or 1 depending on if you want verbose output from the plugin

# list of HAProxy instances to monitor
newrelic_haproxy_agent_agents: []
# each value should be a dictionary with the following values:
# name (required): Name to send to NewRelic
# uri (required): URI to query for CSV HAProxy statistics
# proxy (required): Proxy in instance to monitor
# proxy_type (optional): Proxy type (frontend or backend) if multiple proxies have the same name
# user(optional): User to use for HTTP Basic Auth
# password(optional): Password to use for HTTP Basic Auth
```


Dependencies
------------

None.

Example Playbook
----------------

```yml
---
- hosts: all
  roles:
  - role: modcloth.newrelic_haproxy_agent
    newrelic_haproxy_agent_agents:
    - name: 'Foo'
      uri: 'www.example.com/stats;#csv'
      proxy: 'abcd'
      proxy_type: 'frontend'
```

License
-------

MIT

Author Information
------------------

ModCloth, Inc.
