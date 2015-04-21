<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#sec-1">1. Test Konventionen</a>
<ul>
<li><a href="#sec-1-1">1.1. Konvention</a></li>
<li><a href="#sec-1-2">1.2. Beispiele</a></li>
<li><a href="#sec-1-3">1.3. Benennung von Helper-Methoden</a></li>
<li><a href="#sec-1-4">1.4. Referenzen und weiterführende Texte</a></li>
</ul>
</li>
</ul>
</div>
</div>


# Test Konventionen<a id="sec-1" name="sec-1"></a>

## Konvention<a id="sec-1-1" name="sec-1-1"></a>

Test-Methoden werden nach folgendem Schema benannt:

    Arbeitseinheit_Eingabe_ErwartetesErgebnis

(Englisch: "UnitOfWork\_StateUnderTest\_ExpectedBehavior")

-   Eine Arbeitseinheit ist die Klasse, Methode bzw. Funktionalität die getestet wird.   
        Ist am getesteten Ablauf nicht nur eine Methode beteiligt wird als   
        Arbeitseinheit die erste public Methode gewählt, die aufgerufen wird. ("Einstiegsmethode")
-   Die Eingabe sind die Eingabeparameter für den Test.
-   Das Erwartete Ergebnis ist das, was durch die Assertion(s) getestet wird.

## Beispiele<a id="sec-1-2" name="sec-1-2"></a>

    public void sum_NegativeNumberAs1stParam_ExceptionThrown()
    
    public void sum_NegativeNumberAs2ndParam_ExceptionThrown ()
    
    public void sum_simpleValues_Calculated ()
    
    public void parse_OnEmptyString_ExceptionThrown()
    
    public void parse_SingleToken_ReturnsEqualToeknValue ()

    isLoginOK_UserDoesNotExist_ReturnsFalse
    
    addUser_ValidUserDetails_UserCanBeLoggedIn
    
    isLoginOK_LoginFails_CallsLogger

## Benennung von Helper-Methoden<a id="sec-1-3" name="sec-1-3"></a>

Methoden, die keine Test-Methoden sind, werden nach folgendem Schema benannt:

    setup()
    setup_*()
    setup()
    teardown_*()
    initTest()
    initTest_*()

## Referenzen und weiterführende Texte<a id="sec-1-4" name="sec-1-4"></a>

-   <http://osherove.com/blog/2005/4/3/naming-standards-for-unit-tests.html>
-   <http://osherove.com/blog/2012/5/15/test-naming-conventions-with-unit-of-work.html>
-   <http://osherove.com/blog/2012/5/15/what-does-the-unit-in-unit-test-mean.html>
-   <http://artofunittesting.com/definition-of-a-unit-test/>