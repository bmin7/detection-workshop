## Welcome to the Detections Workshop
This guide will provide you with a step-by-step of all the commands we will use throughout this workshop. Please reference it as we move forward. If you have questions, feel free to ask your group moderator.





## Exercise 1 Overview
We will use a pre-packaged detection from Panther and modify it to our liking within the Panther Console.

**Terms we'll reference**
- [Rules](https://docs.panther.com/writing-detections/rules)
- [Packs](https://docs.panther.com/writing-detections/detection-packs)
- [Helpers](https://docs.panther.com/writing-detections/globals?q=helpers)
- [Deep_Get](https://docs.panther.com/writing-detections/globals#deep_get)

**Exercise 1 Steps**
1. Open up a Pack of detections
2. Select the Okta.APIKey.Created rule in the Okta Rules Pack
3. Create a new rule and copy/paste Python code from original packed rule with unique name
4. Run a Test - See the sample data below. 
5. Add the severity function to triage low level alerts. 
6. Save Changes


**Sample Data for Okta**
```
{
	"debugContext": {},
	"published": "2021-01-08 21:28:34.875",
	"eventType": "system.api_token.create",
	"version": "0",
	"legacyEventType": "api.token.create",
	"outcome": {
		"result": "SUCCESS"
	},
	"request": {},
	"uuid": "2a992f80-d1ad-4f62-900e-8c68bb72a21b",
	"severity": "INFO",
	"displayMessage": "Create API token",
	"actor": {
		"alternateId": "user@example.com",
		"displayName": "Test User",
		"id": "00u3q14ei6KUOm4Xi2p4",
		"type": "User"
	},
	"target": [
		{
			"id": "00Tpki36zlWjhjQ1u2p4",
			"type": "Token",
			"alternateId": "unknown",
			"displayName": "test_key",
			"details": null
		}
	]
}
```








## Exercise 2 Overview
Utilizing the Panther Analysis Tool to create, test, and upload a new detection. 


**Terms we'll reference**
- [Panther Analysis Tool](https://docs.panther.com/panther-developer-workflows/panther-analysis-tool#overview)
- [API Key](https://docs.panther.com/panther-developer-workflows/api#how-to-use-panthers-api)


**Exercise 2 Steps**
1. Install Panther Analysis Tool 
```pip install panther_analysis_tool```
2. Verify proper version 
```panther_analysis_tool --version```
3. Fork off Panther Analysis Tool to local 
```git clone https://github.com/panther-labs/panther-analysis.git```
4. Create API Token in Panther Console 
5. Use Check-Connection to verify API setup is successful
```panther_analysis_tool check-connection --api-host DOMAIN --api-token TOKEN```
6. Create new file and copy a .py and .yml file
7. Modify .py file and .yml file
8. Test the rule
```panther_analysis_tool test --path <path to rule>```
9. Once verified, upload the rule
```panther_analysis_tool upload --path <path to rule> --api-host DOMAIN --api-token TOKEN```
10. Check Panther Console for changes









## Exercise 3 Overview and Instructions
Write a detection for each of the following scenarios and run a passing unit test. Once you've completed all three - submit your results to the Panther Console. First to finish all three in the fastest time, wins!

**Resources that will help**
- [Rules Template](https://github.com/panther-labs/panther-analysis/blob/master/templates/example_rule.py)
- [Documentation](https://docs.panther.com/)
- [Common Helper Functions](https://docs.panther.com/writing-detections/globals#common-helpers)


**Rule 1 - Github New Repository Created**
```
{
	"repo": "my-org/my-repo",
	"actor": "cat",
	"action": "repo.create",
	"created_at": 1621305118553,
	"org": "my-org",
	"p_log_type": "GitHub.Audit"
}
```

- Prompt 1 - Write a detection that fires an alert when a new Github Repository is created by a user 
- Prompt 2 - Create a description and runbook and add it into the alert





**Rule 2 - Box Untrusted Device Access**
```
{
	"created_by": {
		"id": "12345678",
		"type": "user",
		"login": "cat@example",
		"name": "Bob Cat"
	},
	"event_type": "DEVICE_TRUST_CHECK_FAILED",
	"source": {
		"login": "lukeskywalker@starwars.com",
		"id": "12345678",
		"type": "user"
	},
	"type": "event",
	"additional_details": "{\"key\": \"value\"}"
}
```



- Prompt 1 - Write a detection that fires an alert when a user device trust check does not pass
- Prompt 2 - Fire an alert with Info severity when the login user is Luke Skywalker (lukeskywalker@starwars.com)
- Prompt 3 - Fire an alert with High severity when the login user is Darth Vadar (darthvadar@starward.com)







**Rule 3 - AWS Root Password Change**
```
{
	"recipientAccountId": "123456789012",
	"requestParameters": null,
	"responseElements": {
		"PasswordUpdated": "Success"
	},
	"sourceIPAddress": "111.111.111.111",
	"eventName": "PasswordUpdated",
	"eventSource": "signin.amazonaws.com",
	"eventVersion": "1.05",
	"userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/77.0.3865.120 Safari/537.36",
	"eventID": "1111",
	"eventType": "AwsConsoleSignIn",
	"requestID": "1111",
	"userIdentity": {
		"principalId": "123456789012",
		"type": "Root",
		"accesKeyId": "1111",
		"accessKeyId": "",
		"accountId": "123456789012",
		"arn": "arn:aws:iam::123456789012:root"
	},
	"awsRegion": "us-east-1",
	"eventTime": "2019-01-01T00:00:00Z"
}
```


- Prompt 1 - Write a detection that fires off an alert when there is an updated password on a root account 
- Prompt 2 - Add the AWS account ID into the title when the alert fires


