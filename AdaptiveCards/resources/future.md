---
title: Roadmap für Adaptive Karten
author: matthidinger
ms.author: mahiding
ms.date: 05/16/2018
ms.topic: article
ms.openlocfilehash: b11edbedca83bb26d2990d029a220165f68bc1ca
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733092"
---
# <a name="future-work"></a>Zukünftige Arbeit

Wir haben zwar einen hervorragenden Fortschritt beim Definieren adaptiver Karten vorgenommen, aber es gibt noch viel Arbeit. Wir hoffen, dass wir durch aktive Entwickler Communitys wie botness und große Partner wie Slack und KiK ein hervorragend Ökosystem plattformübergreifender Karten erstellen können.

## <a name="roadmap"></a>Wegweiser

Die [aktuelle (nicht abschließende) Roadmap](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog)finden Sie hier. Beachten Sie, dass alle hier aufgeführten Änderungen unterliegen und keine Garantie für den Versand ist.

## <a name="future-ideas"></a>Zukünftige Ideen

Im folgenden finden Sie einige zukünftige Ideen, die sich einfach in der Brainstorming-Phase befinden. Wenn Sie an einer dieser Themen interessiert sind, informieren Sie uns in einem Kommentar.

### <a name="great-looking-cards-from-data"></a>Hervorragend aussehende Karten aus Daten

Wir wissen, dass viele Karten Autoren bereits über klar definierte Daten hinter ihren Karten verfügen. Unser Plan besteht darin, ein Vorlagen Modell zu untersuchen, das das Generieren von Karten ermöglicht (serverseitige oder Client seitige), basierend auf den Daten und einem Repository von klar definierten und anpassbaren Vorlagen.

### <a name="make-cards-responsive"></a>Reaktionsfähig machen von Karten

Kartenlayouts sollten im verfügbaren Speicherplatz reaktiv sein. Adaptive Karten sind an verschiedene Geräte, UX-Stile und Benutzeroberflächen-Frameworks angepasst, sind aber noch nicht aktiv. Für-Elemente müssen zusätzliche Eigenschaften definiert werden, mit denen Karten Producer die erforderlichen Hinweise für die renderingbibliotheken bereitstellen können, damit Sie das Layout auf eine Weise ändern können, die die Absicht der Karte beibehält.

### <a name="responsive-exploration"></a>Reaktionsschnelle Untersuchung

* Fügen Sie eine Wichtigkeits Eigenschaft hinzu, mit der die Wichtigkeit von Inhalten kommentiert wird. Weniger wichtige Inhalte können gelöscht werden, um den verfügbaren Speicherplatz anzupassen.
* Fügen Sie **Einschränkungen** und **Richtlinien** Eigenschaften hinzu, die beschreiben, wie Sie reagieren, wenn Einschränkungen nicht erfüllt werden können. 
  * Inhalt ausblenden oder Inhalt auf kleinere Größe reduzieren.
  * Fügen Sie einen Schwellenwert hinzu, bei dessen `columnSet` Überschreitung das Karussell der Spalten geändert wird.

### <a name="new-element-types"></a>Neue Elementtypen

* Maps? -Einbetten einer Karte in eine Karte mit Interaktivität oder Fall Back auf Bitmap
* *Welche Elemente möchten oder benötigen Sie*?

### <a name="new-rendering-libraries"></a>Neue renderingbibliotheken

* REAG?
* Xamarin?
* *Welche Frameworks möchten Sie verwenden?*
