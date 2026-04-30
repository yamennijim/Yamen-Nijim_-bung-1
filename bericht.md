# Übungsblatt 1 – Rechnernetze

## Aufgabe 2: Teamwork

Das bereitgestellte Token-Ring-Programm wurde lokal auf einem Rechner getestet, indem mehrere Instanzen des Programms gestartet wurden.

Jede Instanz erhält beim Start eine eigene IP-Adresse und eine dynamisch zugewiesene Portnummer. Die Kommunikation zwischen den Instanzen erfolgt über das UDP-Protokoll.

Es wurde beobachtet, dass Token-Nachrichten zwischen den Instanzen gesendet werden. Die Nachrichten enthalten Informationen wie die IP-Adresse und den Port des jeweiligen Knotens im Ring.

Da die Ports dynamisch vergeben werden, kam es teilweise zu Situationen, in denen Nachrichten an Ports gesendet wurden, auf denen kein Empfänger aktiv war. In diesen Fällen wurden entsprechende Fehlermeldungen erzeugt. Dennoch konnte gezeigt werden, dass das Programm grundsätzlich in der Lage ist, Nachrichten zwischen mehreren Instanzen zu übertragen.

---

## Aufgabe 3: Wireshark

Zur Analyse der Netzwerkkommunikation wurde das Programm Wireshark verwendet.

Da die Kommunikation lokal auf einem Rechner stattfindet, wurde das Interface „Adapter for loopback traffic capture“ ausgewählt.

Zur Filterung der relevanten Pakete wurde der Display-Filter „udp“ verwendet, um ausschließlich UDP-Pakete anzuzeigen.

Nach dem Start des Token-Ring-Programms konnten UDP-Pakete zwischen der lokalen IP-Adresse beobachtet werden. Die Pakete wurden zwischen verschiedenen Ports übertragen, die vom Programm dynamisch zugewiesen wurden.

Zusätzlich wurden ICMP-Nachrichten mit der Meldung „Destination unreachable (Port unreachable)“ sichtbar. Diese entstehen, wenn ein Paket an einen Port gesendet wird, auf dem kein Empfänger aktiv ist.

Die Analyse zeigt, dass das Programm das UDP-Protokoll verwendet, welches verbindungslos arbeitet und keine Garantie für die Zustellung von Paketen bietet. Dennoch konnte beobachtet werden, dass Nachrichten erfolgreich zwischen den Instanzen übertragen werden.

---

## Probleme und Lösungen

Während der Durchführung der Übung traten mehrere kleinere Probleme auf.

Zunächst gab es Schwierigkeiten bei der Konfiguration der Ports, da diese dynamisch vergeben werden. Dies führte dazu, dass Nachrichten teilweise an falsche Ports gesendet wurden. Dieses Problem wurde durch manuelles Anpassen der Programmargumente und wiederholtes Testen gelöst.

Ein weiteres Problem bestand darin, dass zunächst keine Pakete in Wireshark sichtbar waren. Dies lag daran, dass das falsche Netzwerkinterface ausgewählt wurde. Nach Auswahl des Loopback-Adapters konnten die Pakete korrekt erfasst werden.

Zusätzlich musste darauf geachtet werden, den passenden Display-Filter („udp“) zu setzen, um die relevanten Pakete übersichtlich darzustellen.

---

## Hinweis

Für die Abgabe wurde ein eigener Branch erstellt und ein Pull Request in das bereitgestellte Repository eingereicht.