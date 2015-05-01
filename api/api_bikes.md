# Bike V1 (DRAFT)

## GET /saleslocations
Gibt alle im System verfügbaren Verkaufsorte zurück.

### Request

_Requires login and Client-ID header_

*NO CONTENT*

### Response
```json
{
    "total": 1,
    "locations": [
        {
            "name": "Beep Bikes",
            "address": {
                "street": "Leetstreet",
                "houseNumber": "13",
                "city": "Hamburg",
                "state": "Hamburg",
                "postcode": 42042,
                "country": "Germany"
            }
        }
    ]
}
```

## POST /bike

Fügt ein Fahrrad zu dem Kunden
### Request
_Requires login and Client-ID header_

```json
{
    "frameNumber": 1010101,
    "type": "mk-401 street style",
    "salesLocation": null,
    "buyDate": "2015-12-01",
    "nextMaintenance": "2016-12-01"
}
```

| Parameter       | Beschreibung |
|-----------------|--------------|
| frameNumber     | Rahmennr des Fahrrads |
| type            | Fahrradmodell |
| buyDate         | Kaufdatum |
| salesLocation   | Name des Verkaufsortes (Optional, kann null sein.) |
| nextMaintenance | Datum der nächsten Inspektion |

### Response
Bei Erfolg:

```json
{
    "id": 1337,
    "frameNumber": 1010101,
    "type": "mk-401 street style",
    "salesLocation": null,
    "buyDate": "2015-12-01",
    "nextMaintenance": "2016-12-01"
}
```

__Fehler__:
- 401 - Nicht eingeloggt / Fehlender login-token
- 409 - Fahrrad mit der Rahmennr existiert bereits
- 500 - Server Error

## GET /bikes
### Request
_Requires login and Client-ID header_

_NO CONTENT_

### Response
```json
{
    "total": 1,
    "bikes": [
        {
            "id": 1337,
            "frameNumber": 1010101,
            "type": "mk-401 street style",
            "salesLocation": null,
            "buyDate": "2015-12-01",
            "nextMaintenance": "2016-12-01"
        }
    ]
}
```

## POST /bike/:id

Ändert die Daten eines Fahrrads
### Request
_Requires login and Client-ID header_

#### Url Parameters
| Parameter  | Beschreibung |
|------------|--------------|
| id         | ID des zu ändernden Fahrrads |

#### Content
```json
{
    "type": "mk-401 street style",
    "frameNumber": 1010101,
    "salesLocation": null,
    "buyDate": "2015-12-01",
    "nextMaintenance": "2016-12-01"
}
```

| Parameter       | Beschreibung |
|-----------------|--------------|
| type            | Fahrradmodell |
| frameNumber     | Rahmennr des Fahrrads |
| salesLocation    | Name des Verkaufsortes |
| buyDate         | Kaufdatum |
| nextMaintenance | Datum der nächsten Inspektion |

### Response
Bei Erfolg:

```json
{
    "id": 1337,
    "frameNumber": 1010101,
    "type": "mk-401 street style",
    "salesLocation": null,
    "buyDate": "2015-12-01",
    "nextMaintenance": "2016-12-01"
}
```

__Fehler__:
- 401 - Nicht eingeloggt / Fehlender login-token
- 403 - Angefragtes Fahrrad gehört dem User nicht
- 404 - Fahrrad mit der ID existiert nicht
- 500 - Server Error
