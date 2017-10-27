
User activity data model

	• Interaction points stored per user in short table
	• Long term interaction stored in similar table with data partition
	• Process long term later using batch 
	• Reverse time series to get last N items


CREATE TABLE user_activity (
username varchar,
Interaction_time timeuuid,
activity_code varchar,
Detail varchar,
PRIMARY KEY (username, interaction_time)
) WITH CLUSTERING ORDER BY (interaction_time DESC);


CREATE TABLE user_activity_history (
Username varchar,
Interaction_date varchar,
Interaction_time timeuuid,
activity_code varchar,
Detail varchar,
PRIMARY KEY ((username, interaction_date), interaction_time)
)