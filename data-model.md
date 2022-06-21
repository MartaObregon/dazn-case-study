# Watch Party data model (events)
## DAZN - Case Study

## Description
The new feature allows up to 4 DAZN customers to watch a sport event from the same “watch room”, which offers synchronized streaming and allows users to interact with each other through a live chat functionality as well as through camera and microphone. This feature is implemented to revolutionize the way users watch our content and make the streaming experience more fun and interactive, which should contribute to increased engagement and retention on the platform.

## Event Definition & Schema



### 1. Initiation of the Watch Party streaming through CTA click - [PROD-1283](https://duckduckgo.com)

[Sample output](https://github.com/MartaObregon/dazn/edit/main/README.md#1-sample-for-initiation-of-the-watch-party-streaming-through-cta-click) 

|              |                   |  
| -------------| ------------------|
| event        | watchPartyStart   |
| category     | watch party       | 
| action       | start             |
| label        | {{itemId}}        | 



### 2. Successful joining of the Watch Party “room - [PROD-5683](https://duckduckgo.com)

[Sample output](https://github.com/MartaObregon/dazn/edit/main/README.md#1-sample-for-successfull-joining-of-the-watch-party-room) 

|              |                   |
| -------------| ------------------|
| event    | watchPartyJoined     |
| category     | watch party      | 
| action       | join|
| label        | {{watchRoomId}}        | 



### 3. Being presented with the Watch Party initialization error modal - [PROD-3321](https://duckduckgo.com)
[Sample output](https://github.com/MartaObregon/dazn/edit/main/README.md#3-sample-for-being-presented-with-the-watch-party-initialization-error-modal) 


|              |                   |
| -------------| ------------------|
| event    | error            |
| category     | watch party error | 
| action       | modal error shown|
| label        | true              | 

### 4. Dismissing the error modal through “CLOSE” cta click - - [PROD-1112](https://duckduckgo.com)
[Sample output](https://github.com/MartaObregon/dazn/edit/main/README.md#4-sample-for-dismissing-the-error-modal-through-close-cta-click) 

|              |                   |
| -------------| ------------------|
| event    | error            |
| category     | watch party error | 
| action       | modal error closed|
| label        | true              | 

## EVENT SCHEMA

|   Event Parameters    |       Type        | Sample         |
| -------------    | ------------------|----------------|
| error          | Object            |   {}             |
| playback       | Object            |   {}             |
| player         | Object            |   {}             |
| application    | Object            |   {}             | 
| watchParty     | Object            |   {}             | 
| clientId       | String            | "07c53c0f6"    | 
| customerId       | String          | "1afc44bd767b" |
| User Agent      | String          | "Mozilla/5.0 (Windows NT 10.0; Win64; x64) " |

|Nested objects{}| Parameters         |  Type | Sample|
|--------------|-------------------|-------| -----|
|error        | category       | String| "Video Player Error" |
|       | code       | String| "API_SERVICE_PLAYBACK_RESUMEPOINTS_UNAVAILABLE" |
|playback      | articleName       | String| "AWS GP de Canadá | Carrera" |
|              | articleId         | String| "4ipwu1ze6b7a1az4ztflqyluw"|
|              | competitionId     | String| "6rqw7bnjivfrz93gae0lboea4"|
|              | competitionName     | String| "DAZN Linear"|
|              | sportId     | String| "11qbnjiv23frz93gae1234a4"|
|              | sportname     | String| "Motor"|
|              | type     | String| "vod"|
|player              | playbackSessionId | String| "1655716256365-1afc44bd767b-y44drrjcqtxa18g3arxjz58ge-e91811"|
|          | liveEdge | Boolean| true|
|          | playerState | String| "start"|
|          | videoType | String| "watch party"|
|application              | type | String| "web.hybrid.2"|
|                   | version | String| "9.13.0"|
|                   | device | object| {}|
|device                  | platform | String| "web"|
|                   | platform | String| "web"|
|watchParty         | itemId | String| "17vb4ds80aga7916d0dc6gvbn"|
|         | itemType | String| "article"|
|         | itemName | String| "Abierto de Eastbourne | Día 2"|
|         | watchRoomId | String| "1655716256365-1afc44bd767b-y44drrjc"|
|         | watchRoomName | String| "ForzaFerrari!!"|
|         | hostId | String| "07c53c0f6"|
|         | guestIds | Array| ["2233c0f6", "123450f6", "12346876p"]|
|         | watchPartyStatus | String| "started"|
|         | liveChatStarted | Boolean| true |


### Sample Datalayer outputs

##### 1. Sample for initiation of the Watch Party streaming through CTA click 
```json
{
    "event": "watchPartyStart",
    "watchParty": {
        "itemType": "article",
        "itemId": "17vb4ds80aga7916d0dc6gvbn",
        "itemName": "Abierto de Eastbourne | Día 2",
    },
    "playback": {
        "articleName": "AWS GP de Canadá | Carrera",
        "articleId": "n6rmhypv1xke1d9e4icohclab",
        "competitionId": "2slaywwom6tyirsmaukgu5mty",
        "competitionName": "Torneo de Eastbourne",
        "sportId": "4rheplujt9zryv3fqvtu1jpah",
        "sportname": "Tenis",
        "type": "live", 
        
    },
    "player": {
        "playbackSessionId": "1655736158523-1afc44bd767b-n6rmhypv1xke1d9e4icohclab-532bc9", 
         "liveEdge":true,
         "playerState":"start",
         "videoType": "watch party",
         
    },
    "application": {
        "type": "web.hybrid.2",
        "version": "9.13.0-hotfix.1.130",
        "device": {
            "platform": "web"
        }
    },
    "clientId": "007c53c0f6",
    "customerId": "1afc44bd767b",
    "User Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/102.0.0.0 Safari/537.36",
    "gtm.uniqueEventId": 99
}
```

#### 2. Sample for successful joining of the Watch Party “room

```json
{
    "event": "watchPartyStart",
    "watchParty": {
        "itemType": "article",
        "itemId": "17vb4ds80aga7916d0dc6gvbn",
        "itemName": "Abierto de Eastbourne | Día 2",
        "watchRoomId": "23094yjhwkjh29343298n",
        "watchRoomName": "MuguruzaFANCLUB!!",
        "hostId": "1afc44bd767b",
        "guestIds": ["892731jbm", "9d92jd73"],
        "watchPartyStatus" : "started",
        "liveChatStarted" : false,
        
    },
    "playback": {
        "articleName": "Abierto de Eastbourne | Día 2",
        "articleId": "n6rmhypv1xke1d9e4icohclab",
        "competitionId": "2slaywwom6tyirsmaukgu5mty",
        "competitionName": "Torneo de Eastbourne",
        "sportId": "4rheplujt9zryv3fqvtu1jpah",
        "sportname": "Tenis",
        "type": "live", 
        
    },
    "player": {
        "playbackSessionId": "1655736158523-1afc44bd767b-n6rmhypv1xke1d9e4icohclab-532bc9", 
         "liveEdge":true,
         "playerState":"start",
         "videoType": "watch party",
         
    },
    "application": {
        "type": "web.hybrid.2",
        "version": "9.13.0-hotfix.1.130",
        "device": {
            "platform": "web"
        }
    },
    "clientId": "007c53c0f6",
    "customerId": "1afc44bd767b",
    "User Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/102.0.0.0 Safari/537.36",
    "gtm.uniqueEventId": 102,
}
```
### 3. Sample for being presented with the Watch Party initialization error modal

```json

{
    "event": "error",
    "error": {
        "category": "Watch Party Initialization Error",
        "code": "API_SERVICE_PLAYBACK_RESUMEPOINTS_UNAVAILABLE"
    },
        "playback": {
        "articleName": "Abierto de Eastbourne | Día 2",
        "articleId": "n6rmhypv1xke1d9e4icohclab",
        "competitionId": "2slaywwom6tyirsmaukgu5mty",
        "competitionName": "Torneo de Eastbourne",
        "sportId": "4rheplujt9zryv3fqvtu1jpah",
        "sportname": "Tenis",
        "type": "live", 
        
    },
    "player": {
        "playbackSessionId": "1655738645337-1afc44bd767b-n6rmhypv1xke1d9e4icohclab-ff723b"
    },
    "application": {
        "type": "web.hybrid.2",
        "version": "9.13.0-hotfix.1.130",
        "device": {
            "platform": "web"
        }
    },
    "clientId": "007c53c0f6",
    "customerId": "1afc44bd767b",
    "User Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/102.0.0.0 Safari/537.36",
    "gtm.uniqueEventId": 34,
}
```
### 4. Sample for dismissing the error modal through “CLOSE” cta click

```json

{
    "event": "error",
    "error": {
        "category": "Watch Party Initialization Error",
        "code": "API_SERVICE_PLAYBACK_RESUMEPOINTS_UNAVAILABLE"
    },
    "clientId": "007c53c0f6",
    "customerId": "1afc44bd767b",
    "User Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/102.0.0.0 Safari/537.36",
    "gtm.uniqueEventId": 35,
}
```

