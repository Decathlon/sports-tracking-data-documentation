# API Changelogs

## Version 2.19.5 (2021-01-13)
Restriction on activity's tags . We applied a regex constraint on tags.
Special caracters are not allowed anymore.
Accepted : az AZ 09 - _ # .
If this rule is not respected, request answers will be HTTP 400 :  ConstraintViolationList
Before this version, an HTTP 500 was returned

## Version 2.18.11 (2021-01-05)
Increase control on /v2/upload API : withelist on file allowed (gpx,tcx,json,xml,jpeg)
Our backend url is no more divulgated on HTTP 301 response body.

## Version 2.18.10 (2020-12-08)
You can now set float value on an activity's datasummaries (ex : "5": 10000.8)
NB : Float are not managed on user_record, user_sumup and global_challenge (we apply rounded value).
User_challenge and user_equipment does.

## Version 2.18.5 (2020-11-09)
enable JWT validation on /v2/coaching_rankings

