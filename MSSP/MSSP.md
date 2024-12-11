```table-of-contents
```
#### Links 

1. [Deepesh doc for APIs](https://cisco-my.sharepoint.com/:w:/r/personal/dekausha_cisco_com/Documents/MSSP%20Analysis.docx?d=wb62ff7e546bc437b9a839cb34cb3a536&csf=1&web=1&e=apglxR)
2. https://confluence-eng-rtp2.cisco.com/conf/display/%7Eaghiya/MSSP+Design
3. [FeatureBrief-Reporting-MultiTenancy](https://cisco.sharepoint.com/:w:/r/sites/CiscoSecureAccess/_layouts/15/Doc.aspx?sourcedoc=%7B15DA4131-D748-411A-BC19-973962B47473%7D&file=FeatureBrief-Reporting-MultiTenancy.docx&action=default&mobileredirect=true)
4. https://confluence-eng-rtp2.cisco.com/conf/pages/viewpage.action?pageId=669736585 : dependency
5. https://jira.it.umbrella.com/browse/CSECF-960 EPIC
6. https://cisco.sharepoint.com/:p:/r/sites/CiscoSecureAccess/_layouts/15/Doc.aspx?sourcedoc=%7B1F4E6DF7-492D-4DFD-A356-07928C32F858%7D&file=CloudSec%20-%20Q2FY25%20-%20Nov%206%20EC%20-%20FINAL.pptx&action=edit&mobileredirect=true
7. https://cisco.sharepoint.com/:x:/r/sites/CiscoSecureAccess/_layouts/15/Doc.aspx?sourcedoc=%7BBBAE2D34-1A92-46B9-8107-21F8CD5C83B7%7D&file=Secure%20Access%20Backlogs%20with%20Owners.xlsx&action=default&mobileredirect=true
8. Endpoints called from overview page
```
By searching in sse-overview repo and UI
    activity/amp-retrospective
    app-connectors/groups/overloaded
    app-connectors/groups/overloaded-count
    categories
    categories-by-timerange
    connectoragents/counts
    connectorgroups/counts
    requests-by-timerange
    requests-by-timerange/firewall
    requests-by-timerange/intrusion
    requests-by-timerange/remote
    requests-by-timerange/remote-access
    requests-by-timerange/ztna
    section/route
    section/route-two
    top-identities
    top-resources
    total-requests
    unique-identities
    unique-resources

From UI
Cant find in UI calls
    app-connectors/groups/overloaded
    connectoragents/counts
    connectorgroups/counts
    

Found
    activity/amp-retrospective
    requests-by-timerange
    requests-by-timerange/firewall
    requests-by-timerange/intrusion
    requests-by-timerange/remote
    requests-by-timerange/remote-access
    requests-by-timerange/ztna
    top-identities
    top-resources

    /app-connectors/groups/overloaded-count             ?&cputhreshold=70
    /categories
    /categories-by-timerange                            ?&verdict=blocked
    /total-requests                                     ?&identityids=639921485
    /unique-identities                                  ?&sse=true
    /unique-resources

Screens
    Connectivity
    Data Transfer
    Security
    Private resources
    security


```

#### Umbrella MSP APIs

1. Total Requests uses
`/v2/providers/2376942/requests-by-timerange/dns?`

2. Security Activity uses
```
/v2/providers/2376942/requests-by-timerange/dns?categories=150
/v2/providers/2376942/requests-by-timerange/dns?categories=61,108,109
/v2/providers/2376942/requests-by-timerange/dns?categories=65
/v2/providers/2376942/requests-by-timerange/dns?categories=67
/v2/providers/2376942/requests-by-timerange/dns?categories=68
```

where categories are 
```
        "bitfieldPosition": 61,        "name": "Dynamic DNS",
        "bitfieldPosition": 65,        "name": "Enterprise Botnet",
        "bitfieldPosition": 67,        "name": "Enterprise Malware",
        "bitfieldPosition": 68,        "name": "Phishing",
        "bitfieldPosition": 108,        "name": "Newly Seen Domains",
        "bitfieldPosition": 109,        "name": "Potentially Harmful",
        "bitfieldPosition": 150,        "name": "Cryptomining",
```     

Response is daywise count for all
```
{
    "meta": {},
    "data": [
        {
            "count": 0,
            "timestamp": 1732665600000,
            "date": "2024-11-27",
            "time": "00:00:00"
        },
        {
            "count": 313,
            "timestamp": 1732752000000,
            "date": "2024-11-28",
            "time": "00:00:00"
        },
        {
            "count": 0,
            "timestamp": 1732838400000,
            "date": "2024-11-29",
            "time": "00:00:00"
        },
```


3. Total Deployment Health
uses
``/v2/providers/2376942/deployments`

Response
Each array element is for each org, total 301 orgs
In
Total Deployment Health, we show only
    "label": "Virtual Appliances"
    "label": "Roaming Computers"
    "label": "Networks"

```
{
    "meta": {},
    "data": [
        {
            "counts": [
                {
                    "identitytype": {
                        "id": 21,
                        "type": "site",
                        "label": "Sites"
                    },
                    "activecount": 0,
                    "count": 1
                },
                {
                    "identitytype": {
                        "id": 22,
                        "type": "organization",
                        "label": "Organization"
                    },
                    "activecount": 0,
                    "count": 1
                }
            ],
            "organization": {
                "id": 8230080,
                "label": "Test Customer - Big Bang"
            }
        },
        {
            "counts": [
                {
                    "identitytype": {
                        "id": 21,
                        "type": "site",
                        "label": "Sites"
                    },
                    "activecount": 0,
                    "count": 1
                },
                {
                    "identitytype": {
                        "id": 22,
                        "type": "organization",
                        "label": "Organization"
                    },
                    "activecount": 0,
                    "count": 1
                },
                {
                    "identitytype": {
                        "id": 1,
                        "type": "network",
                        "label": "Networks"
                    },
                    "activecount": 0,
                    "count": 2
                }
            ],
            "organization": {
                "id": 2622578,
                "label": "andreitest&#39;s"
            }
        }
```

4. Categories api call
   `/v2/providers/2376942/categories`
Response returns list of all categories
```
{
    "meta": {},
    "data": [
        {
            "label": "Adware",
            "type": "content",
            "legacyid": 1,
            "integration": false,
            "deprecated": false,
            "id": 0
        },
        {
            "label": "Illegal Activities",
            "type": "content",
            "legacyid": 347,
            "integration": false,
            "deprecated": false,
            "id": 121
        },
        {
            "label": "Command and Control",
            "type": "security",
            "legacyid": 92,
            "integration": false,
            "deprecated": false,
            "id": 65
        },
```



whereas for single org it is 
https://api.us.reports.umbrella.com/organizations/4/categories-by-timerange?verdict=blocked&categories=65%2C110%2C108%2C109%2C150%2C61%2C64%2C66%2C68%2C67&from=1731873294000&to=1732046094000&offset=0&timezone=UTC
Response : 
```
{
    "meta": {},
    "data": [
        {
            "counts": [],
            "timestamp": 1731870000000,
            "date": "2024-11-17",
            "time": "19:00:00"
        },
        {
            "counts": [],
            "timestamp": 1731873600000,
            "date": "2024-11-17",
            "time": "20:00:00"
        },
        {
```

#### SSE APIs 

1. 
Connectivity calls 
/v2/organizations/8172949/app-connectors/groups/overloaded-count

```
https://reports.api.umbrella.com/v2/organizations/8172949/app-connectors/groups/overloaded-count?limit=2000&offset=0&timezone=UTC&from=1730678400000&to=1733209167000&cputhreshold=70

{"meta":{},"data":{"count":0}}

```

2. Security calls 
For Security Activity tab : 
/v2/organizations/8172949/requests-by-timerange/intrusion
for 
intrusionaction=detected , blocked , would_block (3 API calls)
this returns hourly count in data array
```
https://reports.api.umbrella.com/v2/organizations/8172949/requests-by-timerange/intrusion?intrusionaction=detected

{
    "meta": {},
    "data": [
        {
            "count": 0,
            "counts": {
                "requests": 0,
                "allowedrequests": 0,
                "blockedrequests": 0,
                "connectedevents": 0,
                "disconnectedevents": 0
            },
            "timestamp": 1728086400000,
            "date": "2024-10-05",
            "time": "00:00:00"
        },
        {
            "count": 0,
            "counts": {
                "requests": 0,
                "allowedrequests": 0,
                "blockedrequests": 0,
                "connectedevents": 0,
                "disconnectedevents": 0
            },
            "timestamp": 1728172800000,
            "date": "2024-10-06",
            "time": "00:00:00"
        },


https://reports.api.umbrella.com/v2/organizations/8172949/requests-by-timerange/intrusion?intrusionaction=blocked

{
    "meta": {},
    "data": [
        {
            "count": 0,
            "counts": {
                "requests": 0,
                "allowedrequests": 0,
                "blockedrequests": 0,
                "connectedevents": 0,
                "disconnectedevents": 0
            },
            "timestamp": 1728086400000,
            "date": "2024-10-05",
            "time": "00:00:00"
        },
        {
            "count": 0,
            "counts": {
                "requests": 0,
                "allowedrequests": 0,
                "blockedrequests": 0,
                "connectedevents": 0,
                "disconnectedevents": 0
            },
            "timestamp": 1728172800000,
            "date": "2024-10-06",
            "time": "00:00:00"
        },
        {
            "count": 0,
            "counts": {
                "requests": 0,
                "allowedrequests": 0,
                "blockedrequests": 0,
                "connectedevents": 0,
                "disconnectedevents": 0
            },
            "timestamp": 1728259200000,
            "date": "2024-10-07",
            "time": "00:00:00"
        }

```

/v2/organizations/8172949/activity/amp-retrospective
this returns 
```
https://reports.api.umbrella.com/v2/organizations/8172949/activity/amp-retrospective?limit=100&offset=0&timezone=UTC&from=1733122760000&to=1733209160000

{"meta":{},"data":[]}
```

/v2/organizations/8172949/requests-by-timerange/
this returns
array for day wise/hour  count based on whether queried for 7 days or 1 day
```
https://reports.api.umbrella.com/v2/organizations/8172949/requests-by-timerange?limit=2000&offset=0&timezone=UTC&from=1733036360000&to=1733209160000


{
    "meta": {},
    "data": [
        {
            "count": 2469,
            "timestamp": 1733032800000,
            "date": "2024-12-01",
            "time": "06:00:00",
            "counts": {
                "requests": 2469,
                "allowedrequests": 2383,
                "blockedrequests": 86,
                "connectedevents": 0,
                "disconnectedevents": 0
            }
        },
        {
            "count": 2279,
            "timestamp": 1733036400000,
            "date": "2024-12-01",
            "time": "07:00:00",
            "counts": {
                "requests": 2279,
                "allowedrequests": 2195,
                "blockedrequests": 84,
                "connectedevents": 0,
                "disconnectedevents": 0
            }
        },
        {
            "count": 2604,
            "timestamp": 1733040000000,
            "date": "2024-12-01",
            "time": "08:00:00",
            "counts": {
                "requests": 2604,
                "allowedrequests": 2524,
                "blockedrequests": 80,
                "connectedevents": 0,
                "disconnectedevents": 0
            }
        },
        {
            "count": 2507,
            "timestamp": 1733043600000,
            "date": "2024-12-01",
            "time": "09:00:00",
            "counts": {
                "requests": 2507,
                "allowedrequests": 2423,
                "blockedrequests": 84,
                "connectedevents": 0,
                "disconnectedevents": 0
            }
        },
        {
            "count": 2573,
            "timestamp": 1733047200000,
            "date": "2024-12-01",
            "time": "10:00:00",
            "counts": {
                "requests": 2573,
                "allowedrequests": 2489,
                "blockedrequests": 84,
                "connectedevents": 0,
                "disconnectedevents": 0
            }
        },
        {
            "count": 2314,
            "timestamp": 1733050800000,
            "date": "2024-12-01",
            "time": "11:00:00",
            "counts": {
                "requests": 2314,
                "allowedrequests": 2230,
                "blockedrequests": 84,
                "connectedevents": 0,
                "disconnectedevents": 0
            }
        },
        {
            "count": 2330,
            "timestamp": 1733054400000,
            "date": "2024-12-01",
            "time": "12:00:00",
            "counts": {
                "requests": 2330,
                "allowedrequests": 2248,
                "blockedrequests": 82,
                "connectedevents": 0,
                "disconnectedevents": 0
            }
        },

```

For top Security Categories
/v2/organizations/8172949/categories
this returns categories list

```
https://reports.api.umbrella.com/v2/organizations/8172949/categories
{
    "meta": {},
    "data": [
        {
            "label": "Adware",
            "type": "content",
            "legacyid": 1,
            "integration": false,
            "deprecated": true,
            "id": 0
        },
        {
            "label": "Illegal Activities",
            "type": "content",
            "legacyid": 347,
            "integration": false,
            "deprecated": false,
            "id": 121
        },
        {
            "label": "Command and Control",
            "type": "security",
            "legacyid": 92,
            "integration": false,
            "deprecated": false,
            "id": 65
        },

```

/v2/organizations/8172949/categories-by-timerange?verdict=blocked
this returns daywise/hourwise count of blocked count category wise

```
https://reports.api.umbrella.com/v2/organizations/8172949/categories-by-timerange?limit=2000&offset=0&timezone=UTC&from=1733036627000&to=1733209427000&verdict=blocked
{
    "meta": {},
    "data": [
        {
            "timestamp": 1733036400000,
            "date": "2024-12-01",
            "time": "07:00:00",
            "counts": [
                {
                    "category": {
                        "id": 201,
                        "type": "content",
                        "label": "Encrypted DNS",
                        "integration": false,
                        "deprecated": false
                    },
                    "requests": 8
                },
                {
                    "category": {
                        "id": 43,
                        "type": "content",
                        "label": "Proxy/Anonymizer",
                        "integration": false,
                        "deprecated": true
                    },
                    "requests": 8
                }
            ]
        },
        {
            "timestamp": 1733040000000,
            "date": "2024-12-01",
            "time": "08:00:00",
            "counts": [
                {
                    "category": {
                        "id": 43,
                        "type": "content",
                        "label": "Proxy/Anonymizer",
                        "integration": false,
                        "deprecated": true
                    },
                    "requests": 8
                },
                {
                    "category": {
                        "id": 201,
                        "type": "content",
                        "label": "Encrypted DNS",
                        "integration": false,
                        "deprecated": false
                    },
                    "requests": 8
                }
            ]
        },

```


3. Users and Groups calls 

/v2/organizations/8172949/requests-by-timerange/ztna
/v2/organizations/8172949/requests-by-timerange/remote-access

this returns day-wise , hour-wise data for remote-access and ZTNA 
```
https://reports.api.umbrella.com/v2/organizations/8172949/requests-by-timerange/remote-access?limit=2000&offset=0&timezone=UTC&from=1733047425000&to=1733220225000

{
    "meta": {},
    "data": [
        {
            "count": 0,
            "counts": {
                "requests": 0,
                "allowedrequests": 0,
                "blockedrequests": 0,
                "connectedevents": 0,
                "disconnectedevents": 0
            },
            "timestamp": 1733047200000,
            "date": "2024-12-01",
            "time": "10:00:00"
        },
        {
            "count": 0,
            "counts": {
                "requests": 0,
                "allowedrequests": 0,
                "blockedrequests": 0,
                "connectedevents": 0,
                "disconnectedevents": 0
            },
            "timestamp": 1733050800000,
            "date": "2024-12-01",
            "time": "11:00:00"
        },


https://reports.api.umbrella.com/v2/organizations/8172949/requests-by-timerange/ztna?limit=2000&offset=0&timezone=UTC&from=1733047425000&to=1733220225000

{
    "meta": {},
    "data": [
        {
            "count": 76,
            "timestamp": 1733047200000,
            "date": "2024-12-01",
            "time": "10:00:00",
            "counts": {
                "requests": 76,
                "allowedrequests": 0,
                "blockedrequests": 76,
                "connectedevents": 0,
                "disconnectedevents": 0
            }
        },
        {
            "count": 76,
            "timestamp": 1733050800000,
            "date": "2024-12-01",
            "time": "11:00:00",
            "counts": {
                "requests": 76,
                "allowedrequests": 0,
                "blockedrequests": 76,
                "connectedevents": 0,
                "disconnectedevents": 0
            }
        },
```

Top 5 Users created requests 
Calls 
/v2/organizations/8172949/top-identities
to find top 5 identiteis 


```
https://reports.api.umbrella.com/v2/organizations/8172949/top-identities?limit=2000&offset=0&timezone=UTC&from=1733133825000&to=1733220225000

{
    "meta": {},
    "data": [
        {
            "requests": 31231,
            "bandwidth": 66085908,
            "identity": {
                "id": 619766289,
                "type": {
                    "id": 34,
                    "type": "anyconnect",
                    "label": "Anyconnect Roaming Client"
                },
                "label": "CSCO-W-PF443GG0",
                "deleted": false
            },
            "counts": {
                "requests": 31231,
                "allowedrequests": 30638,
                "blockedrequests": 593,
                "connectedevents": 0,
                "disconnectedevents": 0
            },
            "rank": 1
        },
        {
            "requests": 8731,
            "bandwidth": null,
            "identity": {
                "id": 639921485,
                "type": {
                    "id": 1,
                    "type": "network",
                    "label": "Networks"
                },
                "label": "dns-rtp3-1-l",
                "deleted": false
            },
            "counts": {
                "requests": 8731,
                "allowedrequests": 8731,
                "blockedrequests": 0,
                "connectedevents": 0,
                "disconnectedevents": 0
            },
            "rank": 2
        },
        {
            "requests": 8690,
            "bandwidth": null,
            "identity": {
                "id": 639922515,
                "type": {
                    "id": 1,
                    "type": "network",
                    "label": "Networks"
                },
                "label": "dns-rtp3-2-l",
                "deleted": false
            },
            "counts": {
                "requests": 8690,
                "allowedrequests": 8690,
                "blockedrequests": 0,
                "connectedevents": 0,
                "disconnectedevents": 0
            },
            "rank": 3
        },
        {
            "requests": 7352,
            "bandwidth": null,
            "identity": {
                "id": 640974639,
                "type": {
                    "id": 34,
                    "type": "anyconnect",
                    "label": "Anyconnect Roaming Client"
                },
                "label": "CSCO-C-IGSNABHL",
                "deleted": false
            },
            "counts": {
                "requests": 7352,
                "allowedrequests": 7352,
                "blockedrequests": 0,
                "connectedevents": 0,
                "disconnectedevents": 0
            },
            "rank": 4
        },
        {
            "requests": 4994,
            "bandwidth": 897380,
            "identity": {
                "id": 1251709893,
                "type": {
                    "id": 3,
                    "type": "directory_group",
                    "label": "AD Groups"
                },
                "label": "CED-SecureAccess-MVP",
                "deleted": false
            },
            "counts": {
                "requests": 4994,
                "allowedrequests": 4290,
                "blockedrequests": 704,
                "connectedevents": 0,
                "disconnectedevents": 0
            },
            "rank": 5
        },
        {
            "requests": 2647,
            "bandwidth": null,
            "identity": {
                "id": 639922547,
                "type": {
                    "id": 1,
                    "type": "network",
                    "label": "Networks"
                },
                "label": "dns-rtp4-1-l",
                "deleted": false
            },
            "counts": {
                "requests": 2647,
                "allowedrequests": 2647,
                "blockedrequests": 0,
                "connectedevents": 0,
                "disconnectedevents": 0
            },
            "rank": 6
        },

```

and for top 5 identities calls 

v2/organizations/8172949/total-requests?identityids=619766289,... : top 5 ids
to get total requests

```
5 such calls 
https://reports.api.umbrella.com/v2/organizations/8172949/total-requests?timezone=UTC&from=1733047425000&to=1733133825000&identityids=619766289
{"meta":{},"data":{"count":2827889}}

https://reports.api.umbrella.com/v2/organizations/8172949/total-requests?timezone=UTC&from=1733047425000&to=1733133825000&identityids=639921485
{"meta":{},"data":{"count":9535}}


```


4. Private resources
calls 

Applications accessed
calls 

```
https://reports.api.umbrella.com/v2/organizations/8172949/unique-resources?limit=2000&offset=0&timezone=UTC&from=1732665600000&to=1733220854000
{"meta":{},"data":{"count":16}}

```

Unique user identities accessed
calls 

```
https://reports.api.umbrella.com/v2/organizations/8172949/unique-identities?limit=2000&offset=0&timezone=UTC&exists=privateapplicationid&identitytypes=directory_user&sse=true&from=1732060800000&to=1732616054000

{"meta":{},"data":{"count":73}}
```

Activity Search Allowed / Blocked
calls 

and shows daywise/hourwise count of allowed and blocked.
```
https://reports.api.umbrella.com/v2/organizations/8172949/requests-by-timerange?limit=2000&offset=0&timezone=UTC&from=1733048332000&to=1733221132000&exists=privateapplicationid&sse=true

{
    "meta": {},
    "data": [
        {
            "count": 76,
            "counts": {
                "requests": 76,
                "allowedrequests": 0,
                "blockedrequests": 76,
                "connectedevents": 0,
                "disconnectedevents": 0
            },
            "timestamp": 1733047200000,
            "date": "2024-12-01",
            "time": "10:00:00"
        },
        {
            "count": 76,
            "counts": {
                "requests": 76,
                "allowedrequests": 0,
                "blockedrequests": 76,
                "connectedevents": 0,
                "disconnectedevents": 0
            },
            "timestamp": 1733050800000,
            "date": "2024-12-01",
            "time": "11:00:00"
        },
        {
            "count": 74,
            "counts": {
                "requests": 74,
                "allowedrequests": 0,
                "blockedrequests": 74,
                "connectedevents": 0,
                "disconnectedevents": 0
            },
            "timestamp": 1733054400000,
            "date": "2024-12-01",
            "time": "12:00:00"
        },

```

VPN resources accessed , Client-based ZTA , Browser-based ZTA
calls 

```
https://reports.api.umbrella.com/v2/organizations/8172949/requests-by-timerange/ztna?limit=2000&offset=0&timezone=UTC&from=1733048332000&to=1733221132000&exists=privateresourceid&ztnatype=clientless&sse=true

{
    "meta": {},
    "data": [
        {
            "count": 0,
            "counts": {
                "requests": 0,
                "allowedrequests": 0,
                "blockedrequests": 0,
                "connectedevents": 0,
                "disconnectedevents": 0
            },
            "timestamp": 1733047200000,
            "date": "2024-12-01",
            "time": "10:00:00"
        },
        {
            "count": 0,
            "counts": {
                "requests": 0,
                "allowedrequests": 0,
                "blockedrequests": 0,
                "connectedevents": 0,
                "disconnectedevents": 0
            },
            "timestamp": 1733050800000,
            "date": "2024-12-01",
            "time": "11:00:00"
        },

https://reports.api.umbrella.com/v2/organizations/8172949/requests-by-timerange/ztna?limit=2000&offset=0&timezone=UTC&from=1733048332000&to=1733221132000&exists=privateresourceid&ztnatype=clientbased&sse=true
{
    "meta": {},
    "data": [
        {
            "count": 76,
            "timestamp": 1733047200000,
            "date": "2024-12-01",
            "time": "10:00:00",
            "counts": {
                "requests": 76,
                "allowedrequests": 0,
                "blockedrequests": 76,
                "connectedevents": 0,
                "disconnectedevents": 0
            }
        },
        {
            "count": 76,
            "timestamp": 1733050800000,
            "date": "2024-12-01",
            "time": "11:00:00",
            "counts": {
                "requests": 76,
                "allowedrequests": 0,
                "blockedrequests": 76,
                "connectedevents": 0,
                "disconnectedevents": 0
            }
        },
        {


https://reports.api.umbrella.com/v2/organizations/8172949/requests-by-timerange/firewall?limit=2000&offset=0&timezone=UTC&from=1733048332000&to=1733221132000&exists=privateapplicationid&sse=true
{
    "meta": {},
    "data": [
        {
            "count": 0,
            "counts": {
                "requests": 0,
                "allowedrequests": 0,
                "blockedrequests": 0,
                "connectedevents": 0,
                "disconnectedevents": 0
            },
            "timestamp": 1733047200000,
            "date": "2024-12-01",
            "time": "10:00:00"
        },
        {
            "count": 0,
            "counts": {
                "requests": 0,
                "allowedrequests": 0,
                "blockedrequests": 0,
                "connectedevents": 0,
                "disconnectedevents": 0
            },
            "timestamp": 1733050800000,
            "date": "2024-12-01",
            "time": "11:00:00"
        },
        {

```
 

Top 3 resources accessed
calls 

```
https://reports.api.umbrella.com/v2/organizations/8172949/top-resources?limit=2000&offset=0&timezone=UTC&from=1732665600000&to=1733220854000&exists=privateapplicationid&sse=true

{
    "meta": {},
    "data": [
        {
            "application": {
                "id": 80185,
                "label": "OpenDNS Github",
                "category": "Private Application"
            },
            "count": 13531,
            "rank": 1
        },
        {
            "application": {
                "id": 54470,
                "label": "Jira IT Umbrella",
                "category": "Private Application"
            },
            "count": 8899,
            "rank": 2
        },
        {
            "application": {
                "id": 39974,
                "label": "IT Splunk",
                "category": "Private Application"
            },
            "count": 5131,
            "rank": 3
        },
        {
            "application": {
                "id": 31048,
                "label": "Cisco Bridge - wwwin",
                "category": "Private Application"
            },
            "count": 1928,
            "rank": 4
        },
```

and for these top 3 resources, finds total  requests 


```
https://reports.api.umbrella.com/v2/organizations/8172949/total-requests?timezone=UTC&from=1732060800000&to=1732616054000&sse=true
{"meta":{},"data":{"count":2865566}}

https://reports.api.umbrella.com/v2/organizations/8172949/total-requests?timezone=UTC&from=1732060800000&to=1732616054000&sse=true
{"meta":{},"data":{"count":2865566}}

https://reports.api.umbrella.com/v2/organizations/8172949/total-requests?timezone=UTC&from=1732060800000&to=1732616054000&sse=true
{"meta":{},"data":{"count":2865566}}

```


#### Queries 
1. /v2/organizations/8172949/requests-by-timerange/ : for proxy
   In case of all , call this for all tables and add the results. Try CTE if supported in clickhouse to do aggregation there only.
```sql
SELECT 
    transaction_organizationId AS organization_id,
    toStartOfMinute(toDateTime(timestamp)) AS hourhumanreadable,
    toInt64(hourhumanreadable) AS hourtimestamp,
    count(*) AS total,
    SUM(CASE WHEN verdict_status = 'ALLOWED' THEN 1 ELSE 0 END) AS allowed,
    SUM(CASE WHEN verdict_status = 'BLOCKED' THEN 1 ELSE 0 END) AS blocked
FROM sig_proxy_dist
WHERE 
    transaction_mspOrganizationId = 0 AND
    transaction_organizationId IN (8137163, 8137170, 8137190) AND
    timestamp >= toInt64(toStartOfMinute(toDateTime(1716575400))) AND
    timestamp <= toInt64(toStartOfMinute(addHours(toDateTime(1719426600), 1))) AND
    eventDate >= '2024-05-25' AND
    eventDate <= '2024-06-27'
GROUP BY 
    transaction_organizationId, hourhumanreadable
ORDER BY 
    hourhumanreadable ASC, transaction_organizationId
```
2. 