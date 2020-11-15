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

## [Recommended naming and tagging conventions](https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/naming-and-tagging)

Wymyśliłem poniższą konwencję nazw dla obiektów:

<business unit>-<asset type>-<region or subregion>-<number>

## Przykłady dla każdego modułu:

- business unit:
- asset type:
- environment:
- region or subregion:
- number

Kilka interesujących artykułów do rozważenia:

[Rozważania dotyczące skrócenia nazw regionów, w przypadku bardzo długiej nazwy zasobu, każdy znak na wagę złota :)](http://www.mattruma.com/adventures-with-azure-regions/)

## [#TYDZIEN3.2]:
Zbuduj prosty ARM Template (możesz wykorzystać już gotowe wzorce z GitHub), który wykorzystuje koncepcję Linked Templates. Template powinien zbudować środowisko złożone z jednej sieci VNET, podzielonej na dwa subnety. W każdy subnecie powinna powstać najprostsza maszyna wirtualna z systemem Ubuntu 18.04 a na każdym subnecie powinny zostać skonfigurowane NSG.

## [#TYDZIEN3.3]:
Zbuduj najprostrzą właśną rolę RBAC, która pozwala użytkownikowi uruchomić maszynę, zatrzymać ją i zgłosić zgłoszenie do supportu przez Portal Azure.

## [#TYDZIEN3.4]:
Spróbuj na koniec zmodyfikować template tak, by nazwa użytkownika i hasło do każdej maszyny z pkt. 2 było pobierane z KeyVault.
