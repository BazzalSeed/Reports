#### Incentive Windowing Possibility

###### Origin
Originally created to get Dick's Sporting Goods on board with an incentive, Igor built some functionality to automatically swap codes out for new ones according to some date windows. This has become an increasing need for more clients, as Tractor Supply Company and Northgate both have monthly codes that need updating and it lands on one person to keep up with those updates and do them at the correct times.


##### Approach

This functionality can be achieved purely through backend effort by
1. For incentive table, add in active_date field
2. Query incentive based on extra filter > active_date

1 can be easily done by editing SurveyMiniRewardsItem @ siphon/rewards/models.py

2 is the part that can be risky/tricky since we reserve reward for survey

Essentially all api calls rely on grabbing the incentive code needs to be modified accordingly.

I believe there are 3

1. def survey(request, api_vers, trigger_id):
2. def sm_available_giftcards(request, api_vers):
3. def lp_account_post(request, api_vers)
