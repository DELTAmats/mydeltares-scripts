# mydeltares-scripts
MyDeltares usermanagement scripts

Export users from the DSD mongodb and filter out any unwanted users by email address:
- Place all unwanted email addresses in file: liferay/input/unwanted_emails.csv
- run batch: mongodb/export and filter emails.kjb

Export users from Liferay and filter out any unwanted users by email address:
- Go to Liferay console and under users export to csv. Place export file in file: liferay/input/liferay_eported_users.csv
- Place all unwanted email addresses in file: liferay/input/unwanted_emails.csv
- run batch: liferay/filter emails.kjb

Merge output from Liferay and from MongoDB to get single list of users. (liferay values overrule mongodb values):
- Place liferay output in file: merge_valid_users/input/liferay_valid_users.csv
- Place mongodb output in file: merge_valid_users/input/dsd_valid_users.csv
- run batch: merge_valid_users/merge_users.kjb

Upload exported, filtered and merged users to Keycloak:
- Place merged output in file: keycloak/input/merged_users.csv
- run batch:keycloak/import_users.kjb
