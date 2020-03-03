# Receptio?

Vi hade tänkt göra en recept-app. Tanken är att användaren kommer att kunna logga in för att lagra vad denne har i kyl, frys och skafferi, lägga till egna recept och spara recept. Via ett externt API, t.ex [Recipe Puppy][1], ska man sedan kunna kolla upp recept som man har varor till att laga. ~~Kan dock behöva göras något urval för att kunna göra en vettig sökning mot API:et.~~ Man ska även kunna göra tvärtom, alltså söka fram ett recept och kolla vad man har hemma och vad man behöver handla för att kunna laga det. 
Kanske det går att implementera en EAN-skanner för att enkelt kunna lägga in vad man har hemma? Exempel [EANdata][4] eller [UPC Database][5], dock verkar inte vara så aktuellt då de mest riktar sig mot USA. Möjligtvis att det är något som användare själv kan lägga in som sedan kan återanvändas vi vårt API?
Finns det kanske några matkedjor som tillhandahåller API:er för att se vad de har i lager? Tänker vidare här att vi skulle kunna ha aviseringar på när det är dags att börja laga maten för att hinna till ett visst klockslag. Kanske kunna räkna med restiden och schablon-tid för att handla varor som behövs till någon favoritbutik, kanske behöver något API som tillhandahåller resväg/restid? T.ex [Here][2] 
Om vi vill att det ska kunna vara svenska recept skulle man kunna använda något utav alla översättnings-API:er som finns. T.ex [Yandex][3].




##### Lite tekniskt:
1. Databaser
    - PostGreSql: <br> Lagra användarnamn, email, lösenord, API-Nyckel och id för skafferiet (i mongoDB).
    - MongoDB: <br> Lagra recept som användare gjort, och användares "skafferi".
    - Redis: <br> För att snabba upp för användaren, t.ex senaste recept på startsida? Aktiv användares varor?

2. API <br>
Görs i Spring och ska implementera Spring Security. Varje användare får en unik API-nyckel som används i dennes konto när klienter används för att koppla upp sig mot API:et. 

3. Klienter <br>
Första tanken är en mobil-app i Flutter/Dart för Android och iOS. Och en webvariant som görs i Sping Boot med Thymeleaf.

4. Hosting <br>
Heroku känns som ett hett alternativ, frågan är om man kan få till alla dessa databaser där. Kan även vara värt att kolla om vi ska köra Docker-containers på Heroku för att underlätta.

[1]: <http://www.recipepuppy.com/about/api/> "Recipe Puppy"
[2]: <https://developer.here.com/develop/rest-apis> "Here"
[3]: <http://tech.yandex.com> "Yandex"
[4]: <https://eandata.com/> "Eandata"
[5]: <https://upcdatabase.org/api> "UPC Database"
