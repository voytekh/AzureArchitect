# Opis sytuacji:
Jesteś architektem w firmie o europejskim zasięgu i rozpoczynasz w swojej firmie budowanie rozwiązań opartych o Microsoft Azure.
Jako architekt ustaliłeś kilka pryncypiów projektowych, które powinny być respektowane przy każdym wdrożeniu:
1. Każdy projekt powinien używać konwencji nazw dla grup i zasobów zgodnych z konwencją firmy.
2. Infrastruktura, budowana w Azure pod środowiska czy aplikacje powinna być zawsze budowana z wykorzystaniem Azure Resource Managera i template’ów. Jeśli jest to duże wdrożenie, powinny być użyte tzw. Linked Templates.
3. Jeśli to konieczne, należy zbudować własny model ról za pomocą RBAC
Docelowo, wszystkie kluczowe ustawienia, tak jak np. nazwy lokalnych administratorów i hasła powinny być pobierane z Azure KeyVault.

# Zadanie:
Zadanie ma 4 etapy, zrób wszystkie 4 by zebrać jak największą liczbę punktów!

## [#TYDZIEN3.1]:
Zbuduj prostą konwencję nazewniczą dla min. takich zasobów jak Grupa Zasobów, VNET, Maszyn Wirtualna, Dysk, Konta składowania danych. Pamiętaj o ograniczeniach w nazywaniu zasobów, które występują w Azure.

# Odpowiedz3.1:

Nie wymyślając koła i bazując na dobrych praktykach które znalazłem pod adresem:

## [AZure Recommended naming and tagging conventions](https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/naming-and-tagging)

Wymyśliłem poniższą konwencję nazw dla obiektów:

`<business unit>-<asset type>-<region or subregion>-<number nnn>`

## Przykłady dla każdego modułu:

- business unit: `it, fin, mktg, product, corp`
- asset type:`(Management group) mg-, (Resource group) rg-, (Public IP address) pip-, (Virtual machine) vm-, (Azure SQL database) sqldb-`
- environment: `prod, dev, qa, stage, test`
- region or subregion: `westus, eastus2, westeurope, usgovia`
- number: `numer kolejny w formacie nnn`

## Przykładowa nazwa obiektu:

`it-sqldb-dev-westeurope-001`

Co oznacza: Deweloperska baza danych Azure SQL dla działu IT w regionie: europa zachodnia.

Dodatkowo uważam że dobrym rozwiązaniem jest korzystanie w maksymalnym stopniu z `Metadata tags` Pozwala to na przechowanie większej ilości informacji, dodatkowo umożliwiając wykonywanie akcji na podstawie zdefiniowanych tagów.

Uwaga: Podstawa to dokładna i na bieżąco aktualizowana dokumentacja.

## Kilka interesujących artykułów do rozważenia:

Rozważania dotyczące skrócenia nazw regionów, w przypadku bardzo długiej nazwy zasobu, każdy znak na wagę złota :) [Adventures with Azure: Regions](http://www.mattruma.com/adventures-with-azure-regions/)

[7 Rules for Flawless Azure Naming Convention](https://www.ais.com/7-rules-for-flawless-azure-naming-convention/)

[What does a good Azure naming convention look like?](https://sharegate.com/blog/what-does-a-good-azure-naming-convention-look-like)

Ograniczenia w nazewnictwie dla poszczególnych obiektów z Azure [Naming rules and restrictions for Azure resources](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/resource-name-rules)



## [#TYDZIEN3.2]:
Zbuduj prosty ARM Template (możesz wykorzystać już gotowe wzorce z GitHub), który wykorzystuje koncepcję Linked Templates. Template powinien zbudować środowisko złożone z jednej sieci VNET, podzielonej na dwa subnety. W każdy subnecie powinna powstać najprostsza maszyna wirtualna z systemem Ubuntu 18.04 a na każdym subnecie powinny zostać skonfigurowane NSG.

## [#TYDZIEN3.3]:
Zbuduj najprostrzą właśną rolę RBAC, która pozwala użytkownikowi uruchomić maszynę, zatrzymać ją i zgłosić zgłoszenie do supportu przez Portal Azure.

## [#TYDZIEN3.4]:
Spróbuj na koniec zmodyfikować template tak, by nazwa użytkownika i hasło do każdej maszyny z pkt. 2 było pobierane z KeyVault.
