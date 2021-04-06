# API Changelogs

Changelogs :

## Version 2.25.1
* Hotfix on PUT user_measures : when you modify an existing user's weight on kg (datatype 22), the weight on grams (datatype 181) is also updated .
* Hotfix on PUT activity : In some cases, old activities (older than 2018/11) could't be updated.


## Version 2.22.2
* Add device model's settings.
Thanks to that, you can declare for some devices, we must trust the elevation collected by the device.
Our automatic elevation relcalcul will not be applied.


## Version 2.21.0
### User Program new fields :
* "language": "be", country strandard iso, user language when he subscribe to a program 
* "provider": "DCM", (whitelisting, content provider)
* "status": "processing", (pending / processing / completed / cancelled)
* "preferences": { (whitelisting, to store parameters)
* "week_days" : ["monday","wednesday"]
    }

### user_sessions New fields:
* "provider": "DCM", (whitelisting, fournisseur du contenu)
* "status": "pending", (pending / processing / completed / cancelled)
* "completeDate": null, (session's first completed date)
* "scheduledDate": "2021-02-16" (session's previsional schedule date)

### Rules on user_session :
* When an activity is imported, with a user_session_id, this user_session is automatically updated with following elements :
    "status": "completed",
    "completeDate": "activity_startdate"
* If the activity is deleted, the previous fields are reset to pending and null.


## Version 2.20.0
* Fix error on PUT activity for very old activities (< 2018)
* Fix error on activities records when user change sport
* New filters on firmwares API point (?model=xxx , isLastFirmware=true / false)
* Improve GPX and TCX  compatibility (cadence)
* Improve user's export personal data (TCX is now default format)

## Version 2.19.5 (2021-01-13)
Restriction on activity's tags . We applied a regex constraint on tags.
Special caracters are not allowed anymore.
Accepted : az AZ 09 - _ # .
If this rule is not respected, request answers will be HTTP 400 :  ConstraintViolationList
Before this version, an HTTP 500 was returned

## Version 2.18.11 (2021-01-05)
Increase control on /v2/upload API : withelist on file allowed (gpx,tcx,json,xml,jpeg)
Our backend url is no    more divulgated on HTTP 301 response body.

## Version 2.18.10 (2020-12-08)
You can now set float value on an activity's datasummaries (ex : "5": 10000.8)
NB : Float are not managed on user_record, user_sumup and global_challenge (we apply rounded value).
User_challenge and user_equipment does.

## Version 2.18.5 (2020-11-09)
enable JWT validation on /v2/coaching_rankings

