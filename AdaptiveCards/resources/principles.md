---
title: Motivation und Prinzipien
author: matthidinger
ms.author: mahiding
ms.date: 5/14/2018
ms.topic: article
ms.openlocfilehash: 243ad63fc585c5afc3fa396b86ff6261e8a7ee93
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732562"
---
# <a name="motivations-and-principles"></a>Motivation und Prinzipien

Im folgenden finden Sie die Gründe und Prinzipien, die die Entwicklung des adaptiven Karten Formats in den Grund haben.

## <a name="motivations-behind-the-format"></a>Gründe für das Format

In den frühen 2016 hatten mehrere Teams bei Microsoft (einschließlich Outlook, Windows und bot Framework) die Erkenntnis, dass Sie alle etwas ähnliches wollten ("Karten") und dass jede von Ihnen eigene Lösungen unabhängig entworfen hat:

- Windows verfügte über eigene Live-Kacheln und Benachrichtigungs Format
-  Das bot Framework verwendet einen Satz vordefinierter Karten Vorlagen, aus denen Entwickler beim Senden von botnachrichten wählen können.
- Outlook verwendet ein eigenes messagecard-Format für die Funktion für ausführbare Nachrichten.

Gleichzeitig haben andere Plattformen, wie z. b. Line, Facebook Messenger, Slack und mehr, Ihr eigenes, proprietäres "Kartenformat" definiert. Einige Microsoft-Mitarbeiter haben sich damit beschäftigt, ein einzelnes Open Card-Format und einen Satz von sdert zu definieren, die Folgendes:

- Erleichtert den Austausch von Karten zwischen Hosts.
- Ermöglicht jedem Host die Kontrolle über die Formatierung von Karten, um die visuelle Konsistenz sicherzustellen.
- Erleichtert es einer Host Anwendung, Karten mit minimalem Aufwand über einsatzbereite sdche anzuzeigen.
- Und das würde auch für Drittanbieter von Bedeutung sein und schließlich von der Branche weitgehend übernommen werden.

## <a name="principles-governing-adaptive-cards"></a>Prinzipien für Adaptive Karten

1.  **Adaptive Karte ist ein _einfaches_ und _deklaratives_ Kartenformat.**

    1.  Es ist nicht als HTML-oder XAML-Ersatz/Alternative gedacht.
    2.  Es ist **kein "Code Behind"** mit adaptiven Karten vorhanden.
        1. Karten Autoren können keinen benutzerdefinierten/beliebigen Code mit ihren Nutzlasten einbetten. Daher muss ein adaptiver Karten Host niemals Code von Drittanbietern ausführen.
        2. Dynamik und Interaktivität werden ausschließlich über deklaratives Markup erzielt.
    3.  Dadurch wird sichergestellt, dass der erforderliche Aufwand zum Erstellen eines adaptiven Karten-SDKs für eine neue Plattform weiterhin angemessen ist

2.  **Das Format der adaptiven Karte kann nicht die Verwendung einer bestimmten zugrunde liegenden Technologie vorschreiben.**

    1.  Das Format der adaptiven Karte beruht nicht auf JavaScript C#,, Python oder einer anderen Sprache.
    2.  Auf ähnliche Weise ist Sie nicht von HTML oder XAML oder anderen Grafiken/UI-Frameworks abhängig.
    3.  Auf diese Weise können Adaptive Karten auf jeder beliebigen Plattform nativ gerendert werden, solange ein Renderer vorhanden ist.

3.  **Das Format der adaptiven Karte ist eine frei _gegebene Eigenschaft_ .**

    1.  Zusammen mit den sdkchen ist das Format Open Source und seine Entwicklungs Community
    2.  Das Format ist daher nicht im Besitz und wird von keinem Team gesteuert.

4.  **Das Format der adaptiven Karte ist nicht "nur für die Verwendung durch Microsoft" konzipiert.**

    1.  Stattdessen ist es so konzipiert, dass es den Anforderungen einer Vielzahl von Anwendungen und Anwendungsfällen entspricht.

5.  **Die _Arbeitsgruppe der adaptiven Karte_ steuert die Weiterentwicklung des Formats.**

    1.  Diese Arbeitsgruppe besteht aus einer Reihe von Microsoft-Mitarbeitern, die alle am Erfolg des Formats beteiligt sind.
    2.  Die Arbeitsgruppe führt wöchentliche Besprechungen (derzeit am Montag) aus, während die featureangebote überprüft werden, offene Probleme besprochen und Selektierung und der Gesamtfortschritt bei vNext-Arbeitsaufgaben nachverfolgt werden.
    3.  Die Arbeitsgruppe verwendet Feedback von der Community, einschließlich interner Microsoft-Teams, um zu entscheiden, wie das Format weiterentwickelt wird.
        1. Jeder kann an der Arbeitsgruppe teilnehmen, indem er Probleme in GitHub öffnet (siehe unten).
        2. Probleme/Featureanforderungen, die in der tatsächlichen Verwendung des Adaptive Cards-Frameworks (als Host oder als Karten Autor) verankert sind, haben die größten Auswirkungen auf die Zukunft des Formats.
    4.  Um von der Arbeitsgruppe genehmigt zu werden, haben Sie neue Features vorgeschlagen:
        1. Muss in realen Anwendungsfällen gerechtfertigt werden
        2. Muss eine funktionale Spezifikation aufweisen
    5.  Genehmigte neue Funktion wird dem Rückstand hinzugefügt und für "vNext" berücksichtigt.
        1. Die Kriterien für die Priorisierung neuer Features umfassen die Vielzahl der Szenarien, die das Feature ermöglicht, die Komplexität/Wartbarkeit und vieles mehr.
        2. Wenn Sie sich im Zweifelsfall befinden, behalten Sie es! Es ist viel einfacher, ein gut konzipiertes Feature später einzuführen, als es immer wieder mit einem Fehler zu leben.
    6.  Alle neuen Features werden in allen unterstützten sdert implementiert.
    7.  Alle neuen Features werden dokumentiert und einer im Ordner "Beispiele" veröffentlichten Test Karte zugeordnet.
    8.  Neue Versionen des Formats und der sdche durchlaufen eine Beta Phase
    9.  Der releasezeitplan für adaptives Karten Schema und SDK-Versionen wird durch Qualität gesteuert, nicht durch Datum

6.  **Interoperabilität**
    1.  Karten, die in Übereinstimmung mit dem dokumentierten Format (z. b. keine Host spezifischen Erweiterungen) erstellt wurden, werden in jedem adaptiver Karten fähigen Host ordnungsgemäß renderfähig.
    2.  Die einzigen Ausnahmen von diesen Prinzipien sind:
        1.  Einige Hosts erlauben möglicherweise keine Interaktivität, und es werden daher weder Eingaben noch Aktionen gerentet.
        2.  Die Ausführung von Aktionen. das Senden von Aktionen liegt nach dem Ermessen des Hosts, und nicht alle Hosts werden notwendigerweise ordnungsgemäß alle Aktionen verarbeiten. übermitteln Sie Nutzlasten. Darüber hinaus unterstützen einige Hosts möglicherweise Action. Submit überhaupt nicht.

7.  **Das Format muss erweiterbar sein.**

    1.  Hosts müssen die Möglichkeit haben, Unterstützung für benutzerdefinierte Elemente oder benutzerdefinierte Aktionen hinzuzufügen, die über die Fähigkeit des Formats hinausgehen.
    2.  Dies ist besonders wichtig für Aktionen, da verschiedene Hosts nicht notwendigerweise denselben Satz von Aktionen unterstützen.
    3.  Diese Ergänzungen sind nach dem Ermessen des Hosts.
        1. Sie stellen keine *de-facto* -Ergänzung zur adaptiven Karten Spezifikation dar.
        2. Daher wird eine Nutzlast, die Sie verwendet, mit dem normalen adaptiven Kartenformat nicht kompatibel.
        3. Sie können jedoch der Arbeitsgruppe präsentiert und als neue Features für eine zukünftige Version des Formats vorgeschlagen werden, wie unter Punkt #5

8.  **Karten Autoren besitzen den Inhalt, Host-apps sind das Aussehen und fühlen.**

    1.  Host-apps erzwingen ihren Stil, sodass Karten Aussehen und Verhalten sich wie Native Erweiterungen der APP-Erfahrung.
    2.  Karten Autoren können weiterhin formatieren, aber nur über semantische Ausdrücke von Farben, Größen usw.

9.  **Sdele werden für die beliebtesten Entwickler Plattformen bereitgestellt.**

    1.  SDI erleichtern das Rendering von adaptiven Karten Nutzlasten auf einem beliebigen Host.
    2.  Dadurch wird sichergestellt, dass die Zugangs Barriere für Entwickler von Drittanbietern und Microsoft Teams so gering wie möglich ist.
