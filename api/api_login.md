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
    "token": "vabkj4fvba4jkvrtaj4gr"
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
    "customerid": "00157751",
    "firstname": "Hans",
    "name": "Wurst",
    "password": "thisismypawword",
    "birthday": "01.01.1970",
    "gender": "male",
    "address": {
        "street": "Leetstreet",
        "houseNumber": "13",
        "city": "Hamburg",
        "state": "Hamburg",
        "postcode": 42042,
        "country": "Germany"
    }
}
```
| Parameter  | Beschreibung |
|------------|--------------|
| email      | Email des Kunden, die Später verwendet werden soll |
| customerid | Die vom CRM dem Kunden zugeteil wurde |
| firstname  | Vorname des Kunden |
| name       | Nachname des Kunden |
| password   | Das zu verwendende Password |
| birthday   | Geburtstag des Kunden, Format: dd.mm.yyyy |
| gender     | Geschlecht des Kunden |
| address    | Adress des Kunden |

### Response
Bei Erfolg:
```json
{
    "email": "testing@example.com",
    "token": "vabkj4fvba4jkvrtaj4gr"
}
```
Der Token wird für alle weiteren Anfragen benötigt. Zu beachten: Die Registrierung führt sogleich einen Login aus, deswegen die gleiche Rückgabe.

__Fehler__:
- 400 - Eines der Inputs war nicht im richtigen Format
- 404 - Kundennr existiert nicht
- 409 - Benutzer existiert bereits
- 500 - Server Error
