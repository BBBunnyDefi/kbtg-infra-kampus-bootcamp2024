# 08_setup_elk
Kibana is an open-source data visualization and exploration tool designed to work with the Elasticsearch data store. Together with Elasticsearch, Logstash, and Beats, Kibana forms what is known as the ELK Stack (Elasticsearch, Logstash, Kibana).

## Objectives
- Setup Kibana for this workshop to see Logginng on your system.
- Learn how to use Kibana to set up a Logging solution for your system.
- Learn about ELK Stack.

## Expected Outcome
- Kibana is ready to use for your group.

## Prerequisites
- no prerequisites

## Step-by-Step: How to setup dataview on Kibana
> [!NOTE]
> The following instruction for the [kibana-console] only.

### Access kibana URL
```sh
http://kibana-alb-8803233.ap-southeast-1.elb.amazonaws.com/
```

With these credential for each group.
| Username  | Password |
| ------------- | ------------- |
| group01  | group01  |
| group02  | group02  |
| group03  | group03  |
| group04  | group04  |
| group05  | group05  |

## Verify
- [ ] Ensure the Kibana Space for your group already exists.
- [ ] Ensure the Dataview is already configured on the Kibana console.