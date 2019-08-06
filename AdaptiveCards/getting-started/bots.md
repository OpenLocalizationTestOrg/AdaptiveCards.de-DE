---
title: Adaptive Karten für bot-Entwickler
author: matthidinger
ms.author: mahiding
ms.date: 05/30/2018
ms.topic: article
ms.openlocfilehash: a50f2e6f145ae2c4571d6b20b61b9ad182ca7ba5
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733167"
---
# <a name="adaptive-cards-for-bot-developers"></a>Adaptive Karten für bot-Entwickler

Adaptive Karten eignen sich hervorragend für Bots. Mit Ihnen können Sie eine Karte einmal erstellen und Sie in mehreren apps wie Microsoft Teams, ihrer eigenen Website usw. schön darstellen.

> [!NOTE]
> Skype wird in der aktuellen Vorschauversion nicht unterstützt. Aktuelle Informationen finden Sie auf der Seite [Partner Status](../resources/partners.md) .

## <a name="try-it-out"></a>Probieren Sie es aus

Klicken Sie auf den folgenden Link [, und sprechen Sie mit unserem Scuba bot](http://contososcubademo.azurewebsites.net/). Nehmen `I'm looking for scuba` wir an, und Sie können Ihnen dabei helfen, den Besuch Ihrer Träume zu verbuchern.  

Alle Antworten des Bots werden mit adaptiven Karten erstellt.

[![Bildschirm Abbildung von Scuba Chat](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)

**Holen Sie sich den Code**: [den vollständigen Quellcode](https://github.com/matthidinger/ContosoScubaBot
) für den Quellcode für den Quellcode finden Sie auf GitHub.


## <a name="bot-framework-integration"></a>Bot Framework-Integration

Mit dem [bot Framework](https://dev.botframework.com/) können Sie einen einzelnen bot schreiben, der in der Lage ist, mit Benutzern über mehrere Kanäle wie Skype, Microsoft Teams, Facebook Messenger usw. zu chatten.

## <a name="walkthrough"></a>Exemplarische Vorgehensweise

Es ist recht einfach, dem bot eine Adaptive Karte hinzuzufügen.

### <a name="step-0-start-with-a-basic-message"></a>Schritt 0: Starten mit einer grundlegenden Nachricht

Im folgenden finden Sie eine Standard `message` Nutzlast des bot-Frameworks, die an beliebige Kanäle übermittelt und dem Benutzer Text angezeigt werden kann.

```json
{
   "type": "message",
   "text": "Plain text is ok, but sometimes I long for more..."
}
```

### <a name="step-1-add-an-adaptive-card-attachment"></a>Schritt 1: Hinzufügen einer adaptiven Karte`attachment`

Zum Hinzufügen eines gewissen Werts über nur Text verfügt das bot Framework über ein `attachments`Konzept von. 

Fügen wir eine Adaptive Karte an, die benutzerdefinierten Text anzeigt.

![Einfache Adaptive Karte](media/bots/hello-adaptivecards.png)

```json
{
  "type": "message",
  "text": "Plain text is ok, but sometimes I long for more...",
  "attachments": [
    {
      "contentType": "application/vnd.microsoft.card.adaptive",
      "content": {
        "type": "AdaptiveCard",
        "version": "1.0",
        "body": [
          {
            "type": "TextBlock",
            "text": "Hello World!",
            "size": "large"
          },
          {
            "type": "TextBlock",
            "text": "*Sincerely yours,*"
          },
          {
            "type": "TextBlock",
            "text": "Adaptive Cards",
            "separation": "none"
          }
        ],
        "actions": [
          {
            "type": "Action.OpenUrl",
            "url": "http://adaptivecards.io",
            "title": "Learn More"
          }
        ]
      }
    }
  ]
}
```

### <a name="step-2-build-even-richer-cards"></a>Schritt 2: Erstellen Sie noch umfangreichere Karten 

Adaptive Karten bieten viel mehr als nur anpassbaren Text. 

Sie haben folgende Möglichkeiten: 

* Zu `Images` Ihrer Karte hinzufügen
* Organisieren Sie Ihre Inhalte `Containers` mit und`Columns`
* Fügen Sie mehrere Typen von hinzu.`Actions`
* Von `Input` Benutzern erfassen
* Eine Karte haben`show another card`
* [Sehen Sie sich den vollständigen Schema-Explorer](http://adaptivecards.io/explorer/)an! 

## <a name="platform-sdks"></a>Plattform-sdgs

Wenn Ihr Bot mithilfe von .net oder nodejs entwickelt wurde, verfügen wir über Bibliotheken, die das Erstellen von adaptiven Karten noch vereinfachen.

Platform|Installieren|Weitere Informationen
--------|-------|----------
.NET | `Install-Package AdaptiveCards -IncludePrerelease` | [Bot Framework .NET-Dokumentation](https://docs.microsoft.com/en-us/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
NodeJS | `npm install adaptivecards` | [Bot Framework-nodejs-Dokumentation](https://docs.microsoft.com/en-us/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)


## <a name="channel-status"></a>Kanalstatus

Mit dem bot Framework können Sie den bot in mehreren Kanälen veröffentlichen. Wir arbeiten mit verschiedenen Kanälen, um eine vollständige Unterstützung für Adaptive Karten bereitzustellen. Aktuelle Informationen finden Sie auf der Seite [Partner Status](../resources/partners.md) .


## <a name="dive-in"></a>Tauchen Sie ein!

Wir haben in diesem Tutorial nur die Oberfläche durchgegangen. sehen Sie sich daher die unten aufgeführten Links an, um weitere Möglichkeiten zu finden, wie Adaptive Karten ihren bot verbessern können.

* [Beispiel Karten zur Inspiration durchsuchen](http://adaptivecards.io/samples/)
* Verwenden des [Schema-Explorers](http://adaptivecards.io/explorer) , um die verfügbaren Elemente zu erlernen
* Erstellen einer Karte mithilfe der [interaktiven](http://adaptivecards.io/visualizer/index.html?hostApp=Skype) Schnellansicht
* Feedback zu Feedback [erhalten](http://adaptivecards.io/connect)
