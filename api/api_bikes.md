# Bike V1

## GET /biketypes
Gibt alle im System verfügbaren Fahrradtypen zurück.

### Request

_Requires login and Client-ID header_

*NO CONTENT*

### Response
[
  {
    "name": "City Bike",
    "id": "bed4ec0c-ccdb-4f18-bfad-b74a045876b9",
    "description": "for the city",
    "inspectionIntervalInWeeks": 4
  },
  {
    "name": "City Cross",
    "id": "00f5ef7e-1c51-4a56-9b5d-244b8730b3e3",
    "description": "for the cross",
    "inspectionIntervalInWeeks": 2
  }
  ,
  ...
]

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
    "purchaseDate": "2015-12-01",
    "nextMaintenance": "2016-12-01"
}
```

| Parameter       | Beschreibung |
|-----------------|--------------|
| frameNumber     | Rahmennr des Fahrrads |
| type            | Fahrradmodell |
| salesLocation   | Name des Verkaufsortes (Optional, kann null sein.) |
| purchaseDate    | Kaufdatum |
| nextMaintenance | Datum der nächsten Inspektion |

### Response
Bei Erfolg:

```json
{
    "id": "6ba7b810-9dad-11d1-80b4-00c04fd430c8",
    "frameNumber": 1010101,
    "type": "mk-401 street style",
    "salesLocation": null,
    "purchaseDate": "2015-12-01",
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
            "id": "6ba7b810-9dad-11d1-80b4-00c04fd430c8",
            "frameNumber": 1010101,
            "type": "mk-401 street style",
            "salesLocation": null,
            "purchaseDate": "2015-12-01",
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
    "purchaseDate": "2015-12-01",
    "nextMaintenance": "2016-12-01"
}
```

| Parameter       | Beschreibung |
|-----------------|--------------|
| type            | Fahrradmodell |
| frameNumber     | Rahmennr des Fahrrads |
| salesLocation   | Name des Verkaufsortes |
| purchaseDate    | Kaufdatum |
| nextMaintenance | Datum der nächsten Inspektion |

### Response
Bei Erfolg:

```json
{
    "id": "6ba7b810-9dad-11d1-80b4-00c04fd430c8",
    "frameNumber": 1010101,
    "type": "mk-401 street style",
    "salesLocation": null,
    "purchaseDate": "2015-12-01",
    "nextMaintenance": "2016-12-01"
}
```

__Fehler__:
- 401 - Nicht eingeloggt / Fehlender login-token
- 403 - Angefragtes Fahrrad gehört dem User nicht
- 404 - Fahrrad mit der ID existiert nicht
- 500 - Server Error
