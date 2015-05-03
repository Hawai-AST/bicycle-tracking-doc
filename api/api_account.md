# Account V1

## POST /changePassword
### Request
_Benötigt Client-ID Header._
```json
{
    "token": "bf3b8eca-f5cd-46ba-b424-f6f91d142d70",
    "code": "thisIsTjeNewPassword"
}
```
| Parameter  | Beschreibung |
|------------|--------------|
| token      | Token, der während des Logins erstellt wurde |
| code       | Neues Password des Users |

### Response
Bei Erfolg:
```json
{
    "status": "OK"
}
```

__Fehler__:
- 401 - Invalid Token
- 404 - Password kann nicht gesetzt werden
- 500 - Server Error


## POST /setUserCredentials
### Request
_Benötigt Client-ID Header._
```json
{
	"token": "bf3b8eca-f5cd-46ba-b424-f6f91d142d70",
    "email": "testing@example.com",
    "customerid": "00157751",
    "firstname": "Hans",
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
| token      | Token, der während des Logins erstellt wurde |
| email      | Email des Kunden, die Später verwendet werden soll |
| customerid | Kundennummer, dem Kunden vom CRM zugeteilt wurde (Optional, kann leer sein) |
| firstname  | Vorname des Kunden |
| name       | Nachname des Kunden |
| birthday   | Geburtstag des Kunden, Format: yyyy-MM-dd (Optional, kann leer sein) |
| gender     | Geschlecht des Kunden (Optional, kann leer sein) |
| address    | Adresse des Kunden |

### Response
Bei Erfolg:
```json
{
    "status": "ok"
}
```

__Fehler__:
- 400 - Eines der Inputs war nicht im richtigen Format
- 401 - Invalid Token
- 402 - Email existiert bereits für einen anderen Nutzer
- 500 - Server Error

## POST /setUserCredentials
### Request
_Benötigt Client-ID Header._
```json
{
    "token": "bf3b8eca-f5cd-46ba-b424-f6f91d142d70",
}
```
| Parameter  | Beschreibung |
|------------|--------------|
| token      | Token, der während des Logins erstellt wurde |

### Response
Bei Erfolg:
```json
{
    "email": "testing@example.com",
    "customerid": "00157751",
    "firstname": "Hans",
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
- 401 - Invalid Token
- 500 - Server Error
