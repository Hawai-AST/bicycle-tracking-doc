# Login V1

## POST /login
### Request
_Benötigt Client-ID Header._

```json
{
    "grant-type": "password",
    "email": "testing@example.com",
    "code": "thisismypassword"
}
```

| Parameter  | Beschreibung |
|------------|--------------|
| grant-type | Typ der Autorisierung. Verfügbar: password |
| email      | Email des Benutzers |
| code       | Autorisierungscode. Abhängig von `grant-type` |

Autorisierungscode:
- `grant-type` = `password`: Code ist das Passwort des Benutzers

### Response
Bei Erfolg:

```json
{
    "email": "testing@example.com",
    "token": "bf3b8eca-f5cd-46ba-b424-f6f91d142d70"
}
```

Der Token wird für alle weiteren Anfragen benötigt.

__Fehler__:

- 401 - Falscher Autorisierungscode
- 404 - Benutzer existiert nicht
- 500 - Server Error


## POST /register
### Request
_Benötigt Client-ID Header._

```json
{
    "email": "testing@example.com",
    "customerid": "6ba7b810-9dad-11d1-80b4-00c04fd430c8",
    "firstname": "Hans",
    "name": "Wurst",
    "password": "thisismypassword",
    "birthday": "1970-01-01",
    "gender": "male",
    "address": {
        "street": "Leetstreet",
        "houseNumber": "13",
        "city": "Hamburg",
        "state": "Hamburg",
        "postcode": "42042",
        "country": "Germany"
    }
}
```

| Parameter  | Beschreibung |
|------------|--------------|
| email      | Email des Kunden, die Später verwendet werden soll |
| customerid | Kundennummer, dem Kunden vom CRM zugeteilt wurde (Optional, kann leer sein) |
| firstname  | Vorname des Kunden |
| name       | Nachname des Kunden |
| password   | Das zu verwendende Passwort |
| birthday   | Geburtstag des Kunden, Format: yyyy-MM-dd (Optional, kann leer sein) |
| gender     | Geschlecht des Kunden (Optional, kann leer sein) |
| address    | Adresse des Kunden |

### Response
Bei Erfolg:

```json
{
    "email": "testing@example.com",
    "token": "bf3b8eca-f5cd-46ba-b424-f6f91d142d70"
}
```
Der Token wird für alle weiteren Anfragen benötigt. Zu beachten: Die Registrierung führt sogleich einen Login aus, deswegen die gleiche Rückgabe.

__Fehler__:

- 400 - Eines der Inputs war nicht im richtigen Format
- 404 - Kundennr existiert nicht
- 409 - Benutzer existiert bereits
- 500 - Server Error


# Login V2
## POST /oauth/token
__ACHTUNG__: Befindet sicht nicht unter /api/v2/... sondern direkt /oauth/token

_Requires Client ID header._

Content:

```
username=<email>&grant_type=password&password=<password>&scope=read+write
```

| Parameter  | Beschreibung |
|------------|--------------|
| username	| Email des Benutzers |
| password	| Passwort des Benutzers |

### Response

```json
{
	"access_token":"ca1c05f9-4ce4-4997-a82d-76168fe14191",
	"token_type":"bearer",
	"expires_in":604799,
	"scope":"read write"
}
```

__Errors__:

- 401 : Missing client info
- 400 : Invalid Username/Password

## POST /register
### Request
_Benötigt Client-ID Header._

```json
{
    "email": "testing@example.com",
    "customerid": "6ba7b810-9dad-11d1-80b4-00c04fd430c8",
    "firstname": "Hans",
    "name": "Wurst",
    "password": "thisismypassword",
    "birthday": "1970-01-01",
    "gender": "male",
    "address": {
        "street": "Leetstreet",
        "houseNumber": "13",
        "city": "Hamburg",
        "state": "Hamburg",
        "postcode": "42042",
        "country": "Germany"
    }
}
```

| Parameter  | Beschreibung |
|------------|--------------|
| email      | Email des Kunden, die Später verwendet werden soll |
| customerid | Kundennummer, dem Kunden vom CRM zugeteilt wurde (Optional, kann leer sein) |
| firstname  | Vorname des Kunden |
| name       | Nachname des Kunden |
| password   | Das zu verwendende Passwort |
| birthday   | Geburtstag des Kunden, Format: yyyy-MM-dd (Optional, kann leer sein) |
| gender     | Geschlecht des Kunden (Optional, kann leer sein) |
| address    | Adresse des Kunden |

### Response
Bei Erfolg:

```json
{
    "email": "testing@example.com",
    "token": "bf3b8eca-f5cd-46ba-b424-f6f91d142d70"
}
```

Der Token wird für alle weiteren Anfragen benötigt. Zu beachten: Die Registrierung führt sogleich einen Login aus, deswegen die gleiche Rückgabe.

__Fehler__:

- 400 - Eines der Inputs war nicht im richtigen Format
- 404 - Kundennr existiert nicht
- 409 - Benutzer existiert bereits
- 500 - Server Error
