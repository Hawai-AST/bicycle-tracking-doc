# Map Draft  -  bitte auf Sinnhaftigkeit bzgl Fehler etc prüfen.

## POST /route
### Request
_Benötigt Client-ID Header._

```json
{
	name: "RouteXYZ",
	rodeAt: "2015-04-25T12:35:55Z",
	waypoints: [
		{
			lat: 53.55705300904082,
		    lng: 10.022841095924377,
		    name: "Hochschule für Angewandte Wissenschaften Campus Berliner Tor, 5-21, Berliner Tor, St. Georg, Hamburg-Mitte, Hamburg, 20099, Deutschland"
		},
		{
			lat: 53.557301561749455,
		    lng: 10.020703375339508,
		    name: "1, Lübeckertordamm, St. Georg, Hamburg-Mitte, Hamburg, 20099, Deutschland"
		}
	]
}
```

| Parameter  | Beschreibung |
|------------|--------------|
| name | User-vergebener Name der Route |
| rodeAt | Start der Tour |
| waypoints | Array aus Waypoint, Route wird mit aufsteigendem Index abgelaufen |
| lat | Geographische Breite des Waypoints |
| lng | Geographische Länge des Wapoints |
| name | Genaue Bezeichnung des Waypoints |

### Response
__Erfolg__:

Siehe Rückgabe einzelne Route (GET /route/:id).

__Fehler__:

- 403 - Nicht eingeloggt
- 500 - Server Error


## GET /route
### Request
_Benötigt Client-ID Header._

__Empty__

### Response
__Erfolg__:

```json
[
	{
		id:	12345,
		name: "Route66",
		rodeAt: "2015-04-25T12:35:55Z"
	},
	{
		id:	12500,
		name: "Route33",
		rodeAt: "2015-04-24T12:35:55Z"
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

```json
{
	name: "RouteXYZ",
	rodeAt: "2015-04-25T12:35:55Z",
	createdAt: "2015-04-26T12:35:55Z",
	updatedAt: "2015-04-26T12:35:55Z",
	waypoints: [
		{
			lat: 53.55705300904082,
		    lng: 10.022841095924377,
		    name: "Hochschule für Angewandte Wissenschaften Campus Berliner Tor, 5-21, Berliner Tor, St. Georg, Hamburg-Mitte, Hamburg, 20099, Deutschland"
		},
		{
			lat: 53.557301561749455,
		    lng: 10.020703375339508,
		    name: "1, Lübeckertordamm, St. Georg, Hamburg-Mitte, Hamburg, 20099, Deutschland"
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