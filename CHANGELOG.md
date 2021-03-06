# Changelog

## [1.14] - 2019-10-04
Fix for "Error in as.POSIXlt.character(x, tz, ...) : character string is not in a standard unambiguous format" when running GetAssignments().

## [1.13] - 2019-10-02
Added an error handler when hit.type and qual.req are both used in call to CreateHIT(). Both cannot be used at the same time. (thanks to Jeremy for identifying this problem!)

## [1.12] - 2019-09-28
Fix a bug in AssignQualification() when assigning a single value to multiple workers (thanks Jennie!)

## [1.11] - 2019-09-13
Added a vignette for Qualification Tests
Fix for GetAssignments() returning duplicate results

## [1.1] - 2019-09-04
Major change to improve API requests by creating a stable client rather than creating a client each time a request is made
Fix for bug in GrantBonus due to legacy code (thanks Chris Hydock!)

## [1.0] - 2019-09-02
Now that the unit testing is done and all tests are passing and hopefully all bugs sussed out, I'm bumping the version to 1.0!

## [0.7.1] - 2019-09-02
- CreateHIT now accepts hitlayoutparameters parameter
- Some small fixes

## [0.7.0] - 2019-09-01
- Deduplicating workers in GrantBonus doesn't make sense. Should be de-duplicating assignments -- but with a prompt to the user in case it's desired behavior. To achieve this, I've added a skip.prompt parameter.
- Bug fix in SearchHITs -- Don't forget to refresh the results found!
- Allow no hit.type specified in GetReviewableHITs
- Small fix in HITStatus where it would print the results in addition to returning them
- More namespace exports for ToDataFrame* functions
- Error messages for if no HITs are found in GetAssignment searches
- Lots of unit test enhancements / optimizations

## [0.6.9] - 2019-08-31
- Fix for ActionsGuarded in GenerateQualificationRequirement
- Now exports GenerateAssignmentReviewPolicy
- Small change to parameter checking IntegerValues and LocaleValues
- Add new parameter: persist.on.error in GetAssignment
- Fix for page parameter in GetAssignment
- Error on NA annotation in GetAssignment
- Fix for report of HITs Retrieved in GetReviewableHITs
- Fewer dependencies now, dropping progress and aws.signature
- Default behavior for functions calling other functions is for cross-function calls to be verbose FALSE
- Removing return.pages on several Get functions

## [0.6.8] - 2019-08-30
- Fix in CreateQualificationType when specifying a Qualification Test
- Remove erroneous global variable assignment in CreateHIT
- Added templates from MTurkR
- More unit tests

## [0.6.7] - 2019-08-27
### Fixed
- Now exports emptydf() helper function

## [0.6.6] - 2019-08-25
### Fixed
- Fixed a bug in ContactWorker when warning about invalid requests
- Fixed a bug in ContactWorker with the deduplication of worker lists
- Fixed a bug in ApproveAssignment reporting of total # approved
### Unit tests
- Added unit tests for AssignQualification, BlockWorker, ChangeHITType, ContactWorker

## [0.6.5] - 2019-08-25
### Fixed
- auto.approval.delay parameter in CreateHIT (thanks Clara!)

## [0.6.4] - 2019-08-24
### Unit tests
- Added unit tests for AccountBalance, ApproveAllAssignments, ApproveAssignment, GetClient, SearchQualificationTypes

## [0.6.3] - 2019-08-24
### Cleanup
- Code cleanup to pass build check without any warnings :)

## [0.6.2] - 2019-08-23
### Fixed
- Fix for IntegerValues in GenerateQualificationRequirement, requires casting as.integer() (thanks Clara!)

## [0.6.1] - 2019-08-23
### Fixed
- Really fixed bug in GenerateQualificationRequirement

## [0.6.0] - 2019-08-22
### Fixed
- Fixed bug in GenerateQualificationRequirement introduced by overhaul of CreateHIT() in version 0.4.2 (thanks for catching that Clara!)

## [0.5.9] - 2019-08-20
### Fixed
- Fix for bug in answer return with GetAssignment

## [0.5.8] - 2019-08-19
### Fixed
- Fix misspecification of dataframe length in ApproveAssignment (thanks Brent Kaplan!)

## [0.5.7] - 2019-08-18
### Added
- UpdateQualificationType()

## [0.5.6] - 2019-08-17
### Added
- UpdateQualificationScore()

## [0.5.5] - 2019-08-13
### Added
- UnblockWorker()

## [0.5.4] - 2019-08-13
### Added
- GetReviewResultsForHIT()

## [0.5.3] - 2019-08-11
### Added
- SetHITTypeNotification()

## [0.5.2] - 2019-08-11
### Change
- Changing GetAssignment() parameter answers.as.separate.df to get.answers. Removing default behavior of returning Answers in Assignment data.frame.

## [0.5.1] - 2019-08-11
### Fixed
- Fix for GetAssignment() return of Answers in Assignment data.frame

## [0.5.0] - 2019-08-11
### Fixed
- Fixed a bug in GenerateHTMLQuestion() related to the escaping of strings introduced in 0.3.8. String escaping is now not necessary after update 0.4.2. (Yay!)

## [0.4.9] - 2019-08-11
### Added
- SetHITAsReviewing()

## [0.4.8] - 2019-08-11
### Added
- RevokeQualification()

## [0.4.7] - 2019-08-11
### Added
- GenerateNotification()
- SendTestEventNotification()

## [0.4.6] - 2019-08-10
### Updated
- GetAssignment() now has the ability to return Answers as a separate list using the answers.as.separate.list parameter

## [0.4.5] - 2019-08-09
### Added
- RejectAssignment()

## [0.4.4] - 2019-08-09
### Added
- RejectQualification()

## [0.4.3] - 2019-08-09
### Added
- GrantQualification()

## [0.4.2] - 2019-08-06
### Fixes
Overhaul of CreateHIT() using do.call() instead of eval(parse())
	now with better support for HIT and Assignment Review Policies.

## [0.4.1] - 2019-08-03
### Added
- GenerateExternalQuestion()

## [0.4.0] - 2019-08-03
### Added
- GetReviewableHITs()

## [0.3.9] - 2019-08-03
### Added
- GetQualificationType()

## [0.3.8] - 2019-08-03
### Bug fix
- GetAssignment() now returns the proper results when using hit.type parameter
- GenerateHTMLQuestion() now escapes the HTML quotes and doublequotes

## [0.3.7] - 2019-06-27
### Changed
- GetAssignment() now returns an "Answer" column with XML

## [0.3.6] - 2019-06-26
### Fixed
- Fixing a nasty bug in CreateHIT() when specifying Qualification Requirements and an HTML Question

## [0.3.5] - 2019-06-23
### Added
- GetQualificationScore()

## [0.3.4] - 2019-06-23
### Added
- GetQualifications()

## [0.3.3] - 2019-06-16
### Fix
- Fixes test.duration type issue in CreateQualificationType()

## [0.3.2] - 2019-06-16
### Added
- GetQualificationRequests()

## [0.3.1] - 2019-06-09
### Added
- GetBonuses()

## [0.3.0] - 2019-06-08
### Added
- GetBlockedWorkers()

## [0.2.9] - 2019-06-04
### Fix
- Fix for annotation parameter in CreateHIT()

## [0.2.8] - 2019-06-03
### Added
- HITStatus()

## [0.2.7] - 2019-06-03
### Fix
- Fix for search by annotation

## [0.2.6] - 2019-06-02
### Added
- GetHITsForQualificationType()

## [0.2.5] - 2019-06-02
### Added
- SearchQualificationTypes()

## [0.2.4] - 2019-06-02
### Added
- GenerateHITReviewPolicy()
- GenerateAssignmentReviewPolicy()

## [0.2.3] - 2019-06-02
### Added
- DisposeQualificationType()

## [0.2.2] - 2019-06-01
### Added
- GenerateQualificationRequirement()
- GenerateHITsFromTemplate()
- GenerateHTMLQuestion()

## [0.2.1] - 2019-06-01
### Added
- DisableHIT() and synonyms DisposeHIT(), DeleteHIT(), ExpireHIT()

## [0.2.0] - 2019-06-01
### Added
- ExtendHIT()
### Changed
Small bug fix for GetHIT()

## [0.1.9] - 2019-05-31
### Added
- GetHIT()

## [0.1.8] - 2019-05-31
### Changed
- User can now set access keys using more familiar environment variables
	Sys.setenv(AWS_ACCESS_KEY_ID = "my access key")
	Sys.setenv(AWS_SECRET_ACCESS_KEY = "my secret key")
- User can now set sandbox parameter as option
	R.utils::setOption("pyMTurkR.sandbox", TRUE)
- User can now set AWS profile parameter as option (most users won't need to do this)
	R.utils::setOption("pyMTurkR.profile", TRUE)

## [0.1.7] - 2019-05-27
### Added
- ApproveAllAssignments()

## [0.1.6] - 2019-05-26
### Added
- GetAssignment()

## [0.1.5] - 2019-05-25
### Added
- CreateHIT()
- ContactWorker()

## [0.1.4] - 2019-05-18
### Added
- RegisterHITType()
- ChangeHITType()

## [0.1.3] - 2019-05-16
### Added
- SearchHITs()

## [0.1.2] - 2019-05-14
### Added
- BlockWorker()

## [0.1.1] - 2019-05-12
### Added
- AssignQualification()
- CreateQualificationType()

## [0.1.0] - 2019-05-11
### Added
- Initialized repo with R package ingredients
- Wrote several functions
  - client(): The core client function, creates an MTurk Client using the AWS SDK for Python (Boto3)
  - AccountBalance(): Retrieve MTurk account balance
  - ApproveAssignment(): Approve Assignment(s)
