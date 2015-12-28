# graylog2-zabbix
Basic Zabbix monitoring for Graylog2

Mainly written for my own use, please feel to fork/use and give feedback.
Written using Zabbix 2.4 and Graylog 1.3. Lightly tested, but does no harm anyway.

For specific Elasticsearch monitoring, please head over to Elastizabbix (https://github.com/mkhpalm/elastizabbix)

## Requirements
  * jq (https://github.com/stedolan/jq)
  * curl

This doesn't require anything on the agent. It is an external script curl'ing to the Graylog2 API.

## How to install
  * Create a Graylog2 user with the "reader" role
  * Enter the credentials in the check_graylog_node_creds.txt file.
  * Copy the 2 files to your zabbix's externalscripts directory
  * Make sure your files permissions are adequate
  * Import the XML template in Zabbix
  * Add template to     graylog server

## Usage
```
check_graylog_node -H <HOSTNAME> -a <ATTRIBUTE> [-p <GRAYLOG_API_PORT>] [-h] [-d]

Args:
    -H : Hostname or IP address of graylog server
    -a : Attribute to monitor. See list below.
    -p : Graylog API port (default: 12900)
    -d : Debug message to log file (default: false)
    -h : Displays help

List of attributes:
    - node_id : returns graylog node_id
    - node_transport
    - node_is_master
    - node_cluster
    - node_type
    - node_throughput
    - lb_status
    - total_message_count : return the node's message count
    - es_cluster_health : return elasticsearch's cluster health
    - journal_size
    - journal_num_segments
    - journal_uncommitted_entries
    - journal_events_read
    - journal_events_append
    - buffer_input_utilization
    - buffer_output_utilization
    - buffer_input_utilization_percent
    - buffer_output_utilization_percent
    - poll_data
    - current_deflector (not yet supported, because not accessible via regular user)
    - system_lifecycle
    - system_isprocessing
    - system_tz
    - system_version
    - system_startedat
    - cluster_stream_count
    - cluster_stream_rule_count
    - cluster_user_count
    - cluster_output_count
    - cluster_dashboard_count
    - cluster_input_count
    - cluster_global_input_count
    - cluster_extractor_count
    - cluster_contentpack_count
    - cluster_alerts_count
```
