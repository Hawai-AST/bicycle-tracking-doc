<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#sec-1">1. Test Konventionen</a>
<ul>
<li><a href="#sec-1-1">1.1. Konvention</a></li>
<li><a href="#sec-1-2">1.2. Beispiele</a></li>
<li><a href="#sec-1-3">1.3. Referenzen und weiterführende Texte</a></li>
</ul>
</li>
</ul>
</div>
</div>


# Test Konventionen<a id="sec-1" name="sec-1"></a>

## Konvention<a id="sec-1-1" name="sec-1-1"></a>

Tests werden nach folgendem Schema benannt:

    Arbeitseinheit_Eingabe_ErwartetesErgebnis

(Englisch: "UnitOfWork\_StateUnderTest\_ExpectedBehavior")

-   Eine Arbeitseinheit ist die Klasse, Methode bzw. Funktionalität die getestet wird.   
        Ist am getesteten Ablauf nicht nur eine Methode beteiligt wird als   
        Arbeitseinheit die erste public Methode gewählt, die aufgerufen wird. ("Einstiegsmethode")
-   Die Eingabe sind die Eingabeparameter für den Test.
-   Das Erwartete Ergebnis ist das, was durch die Assertion(s) getestet wird.

## Beispiele<a id="sec-1-2" name="sec-1-2"></a>

    public void Sum_NegativeNumberAs1stParam_ExceptionThrown()
    
    public void Sum_NegativeNumberAs2ndParam_ExceptionThrown ()
    
    public void Sum_simpleValues_Calculated ()
    
    public void Parse_OnEmptyString_ExceptionThrown()
    
    public void Parse_SingleToken_ReturnsEqualToeknValue ()

    IsLoginOK_UserDoesNotExist_ReturnsFalse
    
    AddUser_ValidUserDetails_UserCanBeLoggedIn
    
    IsLoginOK_LoginFails_CallsLogger

## Referenzen und weiterführende Texte<a id="sec-1-3" name="sec-1-3"></a>

-   <http://osherove.com/blog/2005/4/3/naming-standards-for-unit-tests.html>
-   <http://osherove.com/blog/2012/5/15/test-naming-conventions-with-unit-of-work.html>
-   <http://osherove.com/blog/2012/5/15/what-does-the-unit-in-unit-test-mean.html>
-   <http://artofunittesting.com/definition-of-a-unit-test/>