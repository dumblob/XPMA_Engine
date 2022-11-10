Dobrý den,

chtěl bych přejít s několika spolupracovníky a známými k volání přes odorik pomocí callbacků. Sám to tak již leta spokojeně používám ve formě "přednastavených volání".

Nyní bych měl zůstat zodpovědný za funkčnost včetně vyúčtování, ale pro každého zřídit nové linky, aby každý dostal alespoň 99 volných callback čísel a mohl si je nastavovat. A tady je kámen úrazu. Nyní je musím nastavovat já, protože pouze vlastník účtu má k tomu práva a dále, protože rozhraní je krajně nepříjemné na ovládání.

Spolupracovníci a známí totiž volají dost z destinací, kde není k dispozici datové připojení (např. poušť ve Spojených arabských emirátech či Švýcarsko, kde jsou data příliš drahá). Nelze tedy využít API pro objednání callbacku.

Dále díky tomu, že odorik účet a spolu s ním všechny linky (kde každou používá jiná osoba) jsou vázané na jedno telefonní číslo, nelze použít "rychlé kontakty" (aka "zkrácené volby"), které může použít pouze jedno číslo - a sice číslo vlastníka odorik účtu.

Chtěl bych tedy požádat o vytvoření jednoduchého způsobu jak libovolný uživatel telefonu s iOS s libovolnou zahraniční SIM kartou co nejjednodušším a nejintuitivnějším způsobem přidá/změní/zobrazí_si callback.

Moje představa je následující (pro vysokou efektivitu a přívětivost jsou důležité detaily).

a) Uživatel otevře v iOS webovém prohlížeči `callback.odorik.cz`. Zobrazí se mu formulář s pouhými 2 políčky:

a.1) autentizační "hash" (např. `436881BEO3ZTRM`), který dostal od majitela odorik účtu - interně by mohlo jít o konkatenaci vygenerovaného "jména" a "hesla" pro danou linku - šlo by zřejmě použít SIP přihlašovací údaje, pokud je "jméno" nebo "heslo" fixní délky
a.2) svoje telefonní číslo předvyplněné webovým prohlížečem (https://developers.google.com/web/updates/2015/06/checkout-faster-with-autofill )

Okamžitě jakmile se objeví nějaká hodnota v obou políčkách se javascriptem vygeneruje URL odkaz (např. `https://callback.odorik.cz/?hash=436881BEO3ZTRM&num=00420123456789`) a na pozadí se ověří, že autentizace funguje. Pokud bude fungovat, objeví se zvýrazněný boxík pod formulářem obsahující tu vygenerovanou URL jako odkaz a pod tím identifikace linky o kterou se jedná a pod tím obrázkový návod (ideálně animovaný gif) jak uložit tento URL odkaz na "home screen" mezi ostatní aplikace - tzn.:

a.3.I) tapnout na vygenerovaný odkaz
a.3.II) tapnout na ikonu "Share" v liště dole
a.3.III) zvolit "Add to home screen"
a.3.IV) zavřít tuto webovou stránku

b) Jakmile uživatel klikne v iOS "home screen" na ikonu vedoucí na tu vygenerovanou URL, otevře se mu prohlížeč a zobrazí:

b.1) Identifikace linky a pod ní formulář s 1 vstupním políčkem předvyplněným číslem z "copy&paste clipboard" (pokud ve schránce byl string obsahující podřetězec vypadající jako telefonní číslo, jinak pouze nevýrazný placeholder) a fokusem na toto políčko včetně textového kurzoru umístěného za konec tohoto automaticky vloženého čísla. Submit tlačítko formuláře by se mohlo jmenovat "Add or find callback association". Uživatel zkontroluje či vyplní číslo (buď nové číslo volaného, či existující číslo volaného či číslo callbacku - ať již použitého/asociovaného či pouze rezervovaného pro danou linku).

Po odeslání formuláře se zobrazí jedna z následujících možností:

b.2) Pokud číslo v políčku bylo neznámé číslo volaného, je automaticky přidána asociace prvního volného callback čísla s tímto zadaným číslem (jako číslo, na které bude volat ústředna se použije to z URL z kroku (a) ) a uživateli je zobrazena výsledná asociace (callback + číslo_volaného) a dále instruktáž (např. animovaný gif) k uložení obou čísel z nové asociace do telefonního seznamu s vysvětlivkou, že běžné číslo je pro zobrazení správného jména u příchozích hovorů a callback pro volání (odchozí hovory). Z výsledné asociace je callback automaticky "předoznačen" a zkopírován do "copy&paste clipboard" (https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/Interact_with_the_clipboard ).

Pokud již není k dispozici žádné volné callback číslo, pak musí dojít k nahrazení. Tzn. zobrazí se vertikální seznam tlačítek, jejichž počet a názvy odpovídají jednotlivým stávajícím asociovaným číslům volaných a to včetně popisků (pokud bude popisek prázdný, pak bude popisek automaticky vygenerovaný "mnemonic code" algoritmem z několika posledních číslic - např. https://github.com/bitmark-inc/bc-bip39 nebo https://github.com/mbrubeck/mnemonic.js - z důvodu výrazně lepší přehlednosti v té stovce čísel).

Stisknutím jakéhokoliv z těchto tlačítek dojde k deasociaci stávajícího callbacku (tzn. jeho "uvolnění") a okamžité asociaci s nově vyplněným číslem volajícího. Uživateli bude nakonec výrazným způsobem (např. jako info box s vykřičníkem ve žlutém trojúhelníku) zobrazen další postup v bodech:

b.2.I) Nezapomeňte odstranit kontakt s číslem <CALLBACK_ČÍSLO> či ho přejmenovat (na jméno odpovídající <NOVÉ_ČÍSLO>).
b.2.II) Pokud jste v bodu (2) kontakt odstranili, přidejte si číslo <CALLBACK_ČÍSLO> jako callback ke kontaktu <NOVÉ_ČÍSLO>.
b.2.III) Zavřete tuto webovou stránku.

Ať již došlo k přidání nové asociace či přepsání/změně stávající asociace, úplně dole na stránce se zobrazí nevýrazné malé tlačítko nebo pouze odkaz nazvaný "Vrátit vše do původního stavu" po jehož zvolení se vše navrátí do stavu "po otevření webového prohlížeče z home screen URL ikony". Zřejmě bude stačit, aby to byl link zhruba ve stylu `https://callback.odorik.cz/?hash=436881BEO3ZTRM&num=00420123456789&callee=987654321&cb=` (tzn. jednoduché nastavení hodnot na původní - např. "prázdný" callback může znamenat jeho deasociaci).

b.3) Pokud číslo v políčku bylo známé číslo volaného, je zobrazena stávající asociace (tzn. čtveřice: identifikace linky, callback, číslo volaného, poznámka).

b.4) Pokud číslo v políčku bylo známé číslo callbacku, je zobrazena stávající asociace (tzn. čtveřice: identifikace linky, callback, číslo volaného, poznámka).

b.5) Pokud číslo v políčku bylo číslo callbacku, který ještě není asociovaný, je zobrazena pouze tato informace o volném callbacku a identifikace linky.

Pozn.: Záměrně všude uvádím iOS jakožto "nejproblémovější" systém, na kterém naneštěstí mnozí v mém okolí pracují a cokoliv co funguje na iOS funguje všude jinde pro ostatní uživatele.

Pozn. 2: Záměrně nemluvím o JSON API, protože primární je uživatelské rozhraní. Pokud by bylo navíc JSON API, tak proč ne. Ale pokud by bylo pouze JSON API, tak by to neřešilo ten problém popsaný výše a akorát by to nutilo každého provozovat vlastní server či pořizovat web hosting jenom pro takto jednoduchý PHP/... skript (byl by nutný i v případě "single page" offline aplikací jako https://github.com/martykan/odorik kvůli prvotnímu stažení či obnově po vymazání cache prohlížeče atd.).

Dává i z vašeho pohledu smysl něco takového implementovat?

S pozdravem

Jan Pacner
