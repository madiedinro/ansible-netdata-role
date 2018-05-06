# Ansible role for netdata

Created for Ubuntu

## Usage

Add to ansible playbook following:

    - import_role:
        name: dr.netdata
      vars:
        drn_backend:
          enable: false
          host: 127.0.0.1:4242
          type: graphite
          prefix: netdata

        drn_stream:
          enable: false
          host: 127.0.0.1
          port: 19999
          api_key: uuid_api_key

        drn_allow:
          connections_from: '127.0.0.*'
          streaming_from: '127.0.0.*'
          dashboard_from: '127.0.0.*'
          badges_from: '127.0.0.*'
          conf_from: '127.0.0.*'

      tags: ['netdata']
      become: yes

Params:

- [**drn_backend_enable:** (yes/no)] use backend for storing metrics
- [**drn_backend_type:** (str)] backend type. Details at https://github.com/firehol/netdata/wiki/netdata-backends
- [**drn_backend_host:** (str)] backend host
- [**drn_backend_prefix:** (str)] prefix that will prepended to all metricss

- [**drn_stream_enable:**] (yes/no) stream metrics to remote netdata or receive metrics stream if backend enabled
- [**drn_stream_host:**] (str) host with netdata
- [**drn_stream_port:**] (str) netdata port (used same that web ui)
- [**drn_stream_api_key:**] (str:uuid) receiving side api key

- [**drn_allow_*:**] (str) detais at https://github.com/firehol/netdata/wiki/netdata-security

## Default parameters

Discover in `defaults/main.yml`

