## Welcome to the Detections Workshop
This guide will provide you with a step-by-step of all the commands we will use throughout this workshop. Please reference it as we move forward. If you have questions, feel free to ask your group moderator.

## Exercise 1 Overview
We will use a pre-packaged detection from Panther and modify it to our liking within the Panther Console.

**Terms we'll reference**
- [Rules](https://docs.panther.com/writing-detections/rules)
- [Packs](https://docs.panther.com/writing-detections/detection-packs)
- [Helpers](https://docs.panther.com/writing-detections/globals?q=helpers)
- [Deep_Get](https://docs.panther.com/writing-detections#accessing-nested-fields-safely)

**Exercise 1 Steps**
1. Open up a Pack of detections
2. Select the Okta.APIKey.Created rule in the Okta Rules Pack
3. Create a new rule and copy/paste Python code from original packed rule with unique name
4. Run a Test - See code snippet 1-1
5. Add more to tune the detection 
6. Save Changes


**Code 1-1**
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
Utilzing the Panther Analysis Tool to create, test, and upload a new detection. 


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


## Exercise 3 Overview
Apply what we've learned to the following scenarios.

## Instructions for Exercise 3
Write a detection for each of the following scenarios and run a passing test. Once you've completed all three - submit your results to the Panther Console. First to finish all three in the fastest time, wins! 














