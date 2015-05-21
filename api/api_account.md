# Account V1

## POST /user/password
### Request
_Benötigt Client-ID Header._

```json
{
    "code": "thisIsTjeNewPassword"
}
```

| Parameter  | Beschreibung |
|------------|--------------|
| code       | Neues Password des Users |

### Response
__EMPTY__

__Fehler__:

- 403 - Nicht eingeloggt
- 400 - Password kann nicht gesetzt werden
- 500 - Server Error


## POST /user
### Request
_Benötigt Client-ID Header._

```json
{
    "customerid": "6ba7b810-9dad-11d1-80b4-00c04fd430c8",
    "firstName": "Hans",
    "name": "Wurst",
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
| customerid | Kundennummer, dem Kunden vom CRM zugeteilt wurde (Optional, kann leer sein) |
| firstname  | Vorname des Kunden |
| name       | Nachname des Kunden |
| birthday   | Geburtstag des Kunden, Format: yyyy-MM-dd (Optional, kann leer sein) |
| gender     | Geschlecht des Kunden (Optional, kann leer sein) |
| address    | Adresse des Kunden |

### Response
__EMPTY__

__Fehler__:

- 400 - Eines der Inputs war nicht im richtigen Format
- 403 - Nicht eingeloggt
- 409 - Customer ID existiert bereits
- 500 - Server Error

## GET /user
### Request
_Benötigt Client-ID Header._

__Empty__

### Response
Bei Erfolg:

```json
{
    "email": "testing@example.com",
    "customerid": "6ba7b810-9dad-11d1-80b4-00c04fd430c8",
    "firstName": "Hans",
    "name": "Wurst",
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

__Fehler__:

- 403 - Nicht eingeloggt
- 500 - Server Error
