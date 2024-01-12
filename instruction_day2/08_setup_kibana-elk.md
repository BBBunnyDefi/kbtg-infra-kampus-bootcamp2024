# 08_setup_kibana-elk
Kibana is an open-source data visualization and exploration tool designed to work with the Elasticsearch data store. Together with Elasticsearch, Logstash, and Beats, Kibana forms what is known as the ELK Stack (Elasticsearch, Logstash, Kibana).

## Objectives
- Setup Kibana for this workshop to see Logginng on your system.
- Learn how to use Kibana to set up a Logging solution for your system.
- Learn the basics of the ELK Stack

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

## Verify the following instructions
- [ ] Ensure the Kibana Space for your group already exists.
    - Check the space name (for example, Group A is named 'KBTG Bootcamp 1')
- [ ] Ensure that the index of your group has already been sent to the centralized logging system.
    - Click Stack Management >> Index Management  
- [ ] After checking the index, go to Data Views to identify the Elasticsearch data you want to explore. Create and name the index according to the index of each group.
    - In Kibana, go to the left sidebar and click on "Discover. 