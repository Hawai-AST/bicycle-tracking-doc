# Map Draft

## POST /route
### Request
_Benötigt Client-ID Header._

```json
{
	"name": "RouteXYZ",
	"bikeID": 1234,
	"lengthInKm": 123.5,
	"startAt": "2015-04-25T12:35:55Z",
	"finishedAt": "2015-04-25T12:35:55Z",
	"waypoints": [
		{
			"latitude": 53.55705300904082,
		    "longitude": 10.022841095924377,
		    "name": "Hochschule für Angewandte Wissenschaften Campus Berliner Tor, 5-21, Berliner Tor, St. Georg, Hamburg-Mitte, Hamburg, 20099, Deutschland"
		},
		{
			"latitude": 53.557301561749455,
		    "longitude": 10.020703375339508,
		    "name": "1, Lübeckertordamm, St. Georg, Hamburg-Mitte, Hamburg, 20099, Deutschland"
		}
	]
}
```

| Parameter  | Beschreibung |
|------------|--------------|
| name | User-vergebener Name der Route |
| bikeID | ID des Bikes mit dem die Route gefahren wurde |
| lengthInKm | Länge der gefahrenen Strecke |
| startAt | Startzeitpunkt der Tour |
| finishedAt | Endzeitpunkt der Tour |
| waypoints | Array aus Waypoint, Route wird mit aufsteigendem Index abgelaufen |
| latitude | Geographische Breite des Waypoints |
| longitude | Geographische Länge des Wapoints |
| name | Genaue Bezeichnung des Waypoints |

### Response
__Erfolg__:

Siehe Rückgabe einzelne Route (GET /route/:id).

__Fehler__:

- 403 - Nicht eingeloggt
- 500 - Server Error


## PUT /route/:id
### Request
_Benötigt Client-ID Header._

| Parameter  | Beschreibung |
|------------|--------------|
| id | Numerische ID der ausgewählten Route |

```json
{
	"name": "RouteXYZ",
	"bikeID": 1234,
	"lengthInKm": 123.5,
	"startAt": "2015-04-25T12:35:55Z",
	"finishedAt": "2015-04-25T12:35:55Z",
	"waypoints": [
		{
			"latitude": 53.55705300904082,
		    "longitude": 10.022841095924377,
		    "name": "Hochschule für Angewandte Wissenschaften Campus Berliner Tor, 5-21, Berliner Tor, St. Georg, Hamburg-Mitte, Hamburg, 20099, Deutschland"
		},
		{
			"latitude": 53.557301561749455,
		    "longitude": 10.020703375339508,
		    "name": "1, Lübeckertordamm, St. Georg, Hamburg-Mitte, Hamburg, 20099, Deutschland"
		}
	]
}
```

| Parameter  | Beschreibung |
|------------|--------------|
| name | User-vergebener Name der Route |
| bikeID | ID des Bikes mit dem die Route gefahren wurde |
| lengthInKm | Länge der gefahrenen Strecke |
| startAt | Startzeitpunkt der Tour |
| finishedAt | Endzeitpunkt der Tour |
| waypoints | Array aus Waypoint, Route wird mit aufsteigendem Index abgelaufen |
| latitude | Geographische Breite des Waypoints |
| longitude | Geographische Länge des Wapoints |
| name | Genaue Bezeichnung des Waypoints |

### Response
__Erfolg__:

Siehe Rückgabe einzelne Route (GET /route/:id).

__Fehler__:

- 403 - Nicht eingeloggt
- 404 - ID nicht gefunden
- 500 - Server Error


## GET /route
### Request
_Benötigt Client-ID Header._

__Empty__

### Response
__Erfolg__:

Gibt Collection mit Name, Bike-ID sowie Start- und Endzeitpunkt von allen gefahrenen Routen des Nutzers zurück.

```json
[
	{
		"id":	12345,
		"name": "Route66",
		"lengthInKm": 123.5,
		"bikeID": 1234,
		"startAt": "2015-04-25T12:35:55Z",
		"finishedAt": "2015-04-25T12:35:55Z"
	},
	{
		"id":	12500,
		"name": "Route33",
		"lengthInKm": 123.5,
		"bikeID": 1234,
		"startAt": "2015-04-24T12:35:55Z",
		"finishedAt": "2015-04-25T12:35:55Z"
	}
]
```

__Fehler__:

- 403 - Nicht eingeloggt
- 500 - Server Error


## GET /route/:id
### Request
_Benötigt Client-ID Header._

| Parameter  | Beschreibung |
|------------|--------------|
| id | Numerische ID der ausgewählten Route |

### Response
__Erfolg__:

Gibt Map mit spezifischer Route zurück.

```json
{	
	"id":	12345,
	"name": "RouteXYZ",
	"bikeID": 1234,
	"lengthInKm": 123.5,
	"startAt": "2015-04-25T12:35:55Z",
	"finishedAt": "2015-04-25T12:35:55Z",
	"createdAt": "2015-04-26T12:35:55Z",
	"updatedAt": "2015-04-26T12:35:55Z",
	"waypoints": [
		{
			"latitude": 53.55705300904082,
		    "longitude": 10.022841095924377,
		    "name": "Hochschule für Angewandte Wissenschaften Campus Berliner Tor, 5-21, Berliner Tor, St. Georg, Hamburg-Mitte, Hamburg, 20099, Deutschland"
		},
		{
			"latitude": 53.557301561749455,
		    "longitude": 10.020703375339508,
		    "name": "1, Lübeckertordamm, St. Georg, Hamburg-Mitte, Hamburg, 20099, Deutschland"
		}
	]
}
```

__Fehler__:

- 403 - Nicht eingeloggt
- 500 - Server Error


## DELETE /route/:id
### Request
_Benötigt Client-ID Header._

| Parameter  | Beschreibung |
|------------|--------------|
| id | Numerische ID der ausgewählten Route |

### Response
__Erfolg__:

- 200 - Löschen erfolgreich

__Fehler__:

- 403 - Nicht eingeloggt
- 404 - ID nicht gefunden
- 500 - Server Error