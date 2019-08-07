---
title: Übersicht über Adaptive Karten
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: d62bae9259a45dd828028e4f866d18fc75924b0c
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733112"
---
# <a name="adaptive-cards-overview"></a>Übersicht über Adaptive Karten 

Adaptive Karten sind ein Open Card-Austauschformat, das es Entwicklern ermöglicht, Inhalte der Benutzeroberfläche auf gängige und konsistente Weise auszutauschen.

<video controls width="100%" poster="./content/videoposter.png">
    <source src="https://adaptivecardsblob.blob.core.windows.net/assets/AdaptiveCardsOverviewVideo.mp4" type="video/mp4">
</video>

## <a name="how-they-work"></a>Funktionsweise

[**Karten Autoren**](authoring-cards/getting-started.md) beschreiben ihren Inhalt als einfaches JSON-Objekt. Dieser Inhalt kann dann nativ in einer [**Host Anwendung**](rendering-cards/getting-started.md)gerendert werden, sodass er automatisch an das Erscheinungsbild des Hosts angepasst wird.

So kann z. b. der Dienst von "Configuration Manager" eine Adaptive Karte über das bot-Framework erstellen, und wenn er an Skype übermittelt wird, sieht er wie eine Skype-Karte aus. Wenn dieselbe Nutzlast an Microsoft Teams gesendet wird, sieht Sie wie Microsoft Teams aus. Da mehr Host-Apps die Unterstützung von adaptiven Karten unterstützen, wird die gleiche Nutzlast in diesen Anwendungen automatisch bereinigt, aber dennoch ist Sie für die APP vollständig einheitlich.

Benutzer gewinnen, weil alles vertraut ist. Host-apps gewinnen einen Gewinn, da Sie die Benutzer Leistung steuern. Und Karten Autoren gewinnen, weil ihre Inhalte eine breitere Reichweite erreichen, ohne dass zusätzliche Aufgaben ausgeführt werden.

## <a name="goals"></a>Ziele 

Die Ziele für Adaptive Karten lauten:

* **Portabel** : für beliebige apps, Geräte und Benutzeroberflächen-Frameworks
* **Open** -Libraries und Schema sind Open Source und Shared
* Leicht zu definierenden und leicht zu definierenden **kostengünstiger**
* **Ausdrucksstark** als Ziel für den langen Inhalt, den Entwickler entwickeln möchten
* **Rein deklarativ** -es ist kein Code erforderlich oder zulässig.
* **Automatisch** formatiert: die Benutzeroberfläche der Host Anwendung und die Markenrichtlinien

## <a name="for-card-authors"></a>Für Karten Autoren
Adaptive Karten eignen sich hervorragend für Karten Autoren:

* **Ein Schema** : Sie erhalten ein einzelnes Format und minimieren die Kosten für das Erstellen einer Karte und das Maximieren der Anzahl der Orte, die Sie verwenden können.
* Umfang **reicherer Ausdruck** : Ihre Inhalte können enger an gewünschten Wünschen angepasst werden, da Sie über eine umfangreichere Palette verfügen, mit der Sie zeichnen möchten.
* **Umfassende Reichweite** : Ihre Inhalte funktionieren in einem breiteren Satz von Anwendungen, ohne dass Sie neue Schemas erlernen müssen.
* **Eingabe Steuerelemente** : Ihre Karte kann Eingabe Steuerelemente zum Sammeln von Informationen des Benutzers enthalten, der die Karte anzeigen soll.
* **Bessere** Tools: ein Open Card-Ökosystem bedeutet bessere Tools, die von allen Benutzern gemeinsam genutzt werden.

## <a name="for-experience-owners"></a>Für Erfahrungs Besitzer
Wenn Sie ein App-Entwickler sind, der auf ein Ökosystem von Inhalten von Drittanbietern tippen möchte, werden Adaptive Karten aus folgenden Gründen angezeigt:

* **Konsistente Benutzer** Darstellung: Sie garantieren eine konsistente Benutzerfunktion, da Sie den Stil der gerenderten Karte besitzen.
* Systemeigene **Leistung** : Sie erhalten eine native Leistung, da Sie direkt auf Ihr Benutzeroberflächen Framework ausgerichtet ist.
* **Sicherer** Inhalt wird in sicheren Nutzlasten bereitgestellt, sodass Sie das UI-Framework nicht für Rohdaten Markup und Skripterstellung öffnen müssen.
* **Einfache Implementierung** : Sie erhalten die Regal Bibliotheken, um problemlos eine beliebige Plattform zu integrieren, die Sie unterstützen. 
* **Kostenlose Dokumentation** : Sie sparen Zeit, da Sie kein proprietäres Schema erfinden, implementieren und dokumentieren müssen.
* Frei **gegebene** Tools: Sie sparen Zeit, da Sie keine benutzerdefinierten Tools erstellen müssen.

## <a name="core-design-principles"></a>Grundlegende Entwurfs Prinzipien 

Adaptive Karten werden durch eine Reihe von [Leitfäden](resources/principles.md) gesteuert, die für die Nachverfolgung des Entwurfs nützlich waren. 

### <a name="semantic-instead-of-pixel-perfect"></a>Semantik anstelle von Pixel-perfekt
Wir haben so viel wie möglich für semantische Werte und Konzepte im Gegensatz zum reinen Pixel perfekten Layout eingesetzt. Beispiele für den semantischen Ausdruck werden in Farben, Größen und in Elementen wie FactSet und ImageSet angezeigt. Dies ermöglicht es der Host Anwendung, bessere Entscheidungen über das tatsächliche Erscheinungsbild zu treffen.

### <a name="card-authors-own-the-content-host-app-owns-the-look-and-feel"></a>Karten Autoren besitzen den Inhalt, die Host-App besitzt das Aussehen und Gefühl
Die Karten Autoren besitzen das, was Sie sagen möchten, aber die Anwendung, die Sie anzeigt, besitzt das Aussehen und Gefühl der Karte im Kontext ihrer Anwendung.

### <a name="keep-it-simple-but-expressive"></a>Einfache, aber ausdrucksstarke
Wir möchten, dass Adaptive Karten ausdrucksstark und universell sind, aber wir möchten kein UI-Framework erstellen.  Ziel ist es, eine Zwischenebene zu erstellen, die auf die gleiche Weise wie markdown für Dokumente ausdrucksstark genug ist.

Wenn Sie sich auf eine einfache und ausdrucksstarke Speicherung konzentrieren, hat markdown eine einfache und konsistente Beschreibung des Dokument Inhalts erstellt.  Auf die gleiche Weise werden wir davon ausgehen, dass Adaptive Karten eine einfache, ausdrucksstarke Möglichkeit zum Beschreiben von Karten Inhalten bilden können.

### <a name="when-in-doubt-keep-it-out"></a>Wenn Sie sich im Zweifelsfall befinden, behalten Sie es
Es ist einfacher, zu einem späteren Zeitpunkt zu kommen, um mit einem Fehler zu leben. Wenn wir feststellen, ob wir etwas hinzufügen sollten, haben wir uns entschieden, das Problem zu überlassen.  Es ist immer einfacher, eine Eigenschaft hinzuzufügen, als Sie mit einer älteren Legacy-Version zu leben, die wir nicht unterstützen müssen.


## <a name="build-2018-session"></a>Build 2018-Sitzung

In der folgenden Sitzung bei Build 2018 werden Adaptive Karten in Bots, Cortana, Outlook und Windows veranschaulicht. 

<iframe src="https://medius.studios.ms/Embed/Video/BRK2401?SFYT=true" width="960" height="540" allowFullScreen frameBorder="0"></iframe>
