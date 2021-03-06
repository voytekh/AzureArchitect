# Opis sytuacji:
Jesteś architektem w firmie, która tworzy systemy w branży e-commerce dla innych firm, które sprzedają w modelu business-to-consumer w całej Europie. Systemy budujesz w oparciu o Microsoft Azure i strategia budowania systemów Cloud Native została przyjęta i jest w pełni akceptowana przez Twoich klientów
Jako architekt możesz zdecydować zarówno o architekturze systemu jak i wzorcach, które wykorzystasz. Klienci oczekują dobrze zaprojektowanego systemu, nie wnikają w Twoje decyzje.  
System, który projektujesz, będzie odwiedzany przez klientów końcowych, a więc możesz się spodziewać, że:
1) W wybranych godzinach będzie zarówno dużo odwiedzin strony jak i dużo zamówień
2) System będzie miał bardzo nieprzewidywalną liczbę zamówień – zdarzą się okresy, że z systemu nikt nie będzie korzystał, ale też zdarzy się promocja typu „Black Friday”
3) Do systemu importują swoje towary również partnerzy firmy, którzy w różnych okresach roku promują wybrane produkty
4) System musi być jak najbardziej odporny na sytuacje awaryjne – jego podstawowa funkcjonalność, czyli sprzedaż i prezentacja ofert dla klientów powinna być dostępna „zawsze”

# Zadanie:
## [#TYDZIEN2.1]:
Na bazie poznanych wzorców projektowych wybierz 3, które chciałbyś zastosować wraz z uzasadnieniem przy każdym z nich, dlaczego właśnie ten wzorzec projektowy będzie przydatny i jakie problemy ew. może rozwiązać. Uzasadnienie nie może być długie – przy każdym wzorcu postaraj się nie przekroczyć 5 punktów maksymalnie. Wystarczą mi 3 dobre powody.

# Odpowiedzi:

## [Throttling pattern](https://docs.microsoft.com/pl-pl/azure/architecture/patterns/throttling)

- Możliwość przyznania określonych zasobów dla żądań klientów, pozwoli to na uniknięcie przeciążenia projektowanego systemu.
- Możliwość skalowania w przypadku wzrostu obciążenia.
- Unikamy rozbudowywania i późniejszego "zwijania" naszego środowiska w przypadku krótkotrwałych pików obciążenia

## [Messaging patterns](https://docs.microsoft.com/en-us/azure/architecture/patterns/category/messaging)

- [Competing Consumers pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/competing-consumers) - Kierowanie wygenerowanych przez aplikację messages do odpowiednich consumer services.
- [Queue-Based Load Leveling pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/queue-based-load-leveling) - Równoważenie obciążenia.

- [Priority Queue pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/priority-queue) - możliwość priorytetyzacji żądań, na przykład zapis transakcji zakupu przed zapytaniem o dostępność produktu.

## [Static Content Hosting pattern](https://docs.microsoft.com/pl-pl/azure/architecture/patterns/static-content-hosting)
- Obsługa zapytań o pliki statyczne (obrazki, materiały wideo)
- Obsługa klienta z najbliższego CDN-a
- Odciążenie serwerów aplikacyjnych


## [#TYDZIEN2.2]:
Jeśli to możliwe, przy wybranym wzorcu projektowym, zaproponuj, których usług byś użył, by wzorzec ten zaimplementować. Krótko uzasadnij, dlaczego będzie to najbardziej efektywne podejście.

Throttling pattern: API  Management1

Messaging pattern: Service Bus

Static content pattern: Content Delivery Network
