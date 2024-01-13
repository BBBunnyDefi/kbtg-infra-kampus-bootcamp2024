# 09_setup_kibana-elk
Kibana is an open-source data visualization and exploration tool designed to work with the Elasticsearch data store. Together with Elasticsearch, Logstash, and Beats, Kibana forms what is known as the ELK Stack (Elasticsearch, Logstash, Kibana).
<img width="958" alt="kibana-login" src="https://github.com/chayapon-s/kbtg-infra-kampus-bootcamp2024/assets/49383429/b371a581-839a-4287-a1c0-7316c18a5878">

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
http://kibana-alb-8803233.ap-southeast-1.elb.amazonaws.com
```

With these credential for each group.
| Group Number | Username  | Password |
| ------------- | ------------- | ------------- |
| group01  | group01  | group01  |
| group02  | group02  | group02  |
| group03  | group03  | group03  |
| group04  | group04  | group04  |
| group05  | group05  | group05  |


## Verify the following instructions
- [ ] Ensure the Kibana Space for your group already exists.
    - Check the space name (for example, Group1's space is 'Group01')
      <img width="837" alt="kibana02" src="https://github.com/chayapon-s/kbtg-infra-kampus-bootcamp2024/assets/49383429/df94c1c5-cba3-4d0f-9d65-45b65be6be2a">
    
- [ ] Ensure that the index of your group has already been sent to the centralized logging system.
    - Click Stack Management >> Index Management
      <img width="703" alt="kibana03" src="https://github.com/chayapon-s/kbtg-infra-kampus-bootcamp2024/assets/49383429/1b80e8d3-d421-4f79-b43a-5f5bc825a966">
    - Index should be name kbtg-kampus-group-<groupname> (for example, Group1's index name is 'kbtg-kampus-group-1')
      
- [ ] After checking the index, go to Data Views to identify the Elasticsearch data you want to explore. Create and name the index according to the index of each group.
    - In Kibana, go to the left sidebar and click on "Discover.
      <img width="956" alt="kibana04" src="https://github.com/chayapon-s/kbtg-infra-kampus-bootcamp2024/assets/49383429/749fa7fa-a8bc-4059-a6ce-12dd774a98fa">

