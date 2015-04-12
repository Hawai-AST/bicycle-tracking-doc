# API General

API-Endpunkt ist `/api/<version>` wobei <version> die zu benutzende Version ist (z.B. v1). Alle Ressourcen beziehungsweise Methode sind hierunter angesiedelt.

Um eine Request zu machen, braucht die Applikation eine Client-ID die vom Server einmalig vergeben wird und bei jeder Request dann im Header vom Client übergeben wird. Dies ist zum einen zur Absicherung als auch für ggf. Rate limiting oder Erstellung von Statistiken benötigt.


## API-Resourcen/Methoden
- [Login](api_login.md)
