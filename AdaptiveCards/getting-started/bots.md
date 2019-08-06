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
# <a name="adaptive-cards-for-bot-developers"></a><span data-ttu-id="6d0d4-102">Adaptive Karten für bot-Entwickler</span><span class="sxs-lookup"><span data-stu-id="6d0d4-102">Adaptive Cards for Bot Developers</span></span>

<span data-ttu-id="6d0d4-103">Adaptive Karten eignen sich hervorragend für Bots.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-103">Adaptive Cards are a great fit for Bots.</span></span> <span data-ttu-id="6d0d4-104">Mit Ihnen können Sie eine Karte einmal erstellen und Sie in mehreren apps wie Microsoft Teams, ihrer eigenen Website usw. schön darstellen.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-104">They let you author a card once and have it render beautifully inside multiple apps, like  Microsoft Teams, your own website, and more.</span></span>

> [!NOTE]
> <span data-ttu-id="6d0d4-105">Skype wird in der aktuellen Vorschauversion nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-105">Skype is not supported in the current preview.</span></span> <span data-ttu-id="6d0d4-106">Aktuelle Informationen finden Sie auf der Seite [Partner Status](../resources/partners.md) .</span><span class="sxs-lookup"><span data-stu-id="6d0d4-106">See the [Partner Status](../resources/partners.md) page for the latest.</span></span>

## <a name="try-it-out"></a><span data-ttu-id="6d0d4-107">Probieren Sie es aus</span><span class="sxs-lookup"><span data-stu-id="6d0d4-107">Try it out</span></span>

<span data-ttu-id="6d0d4-108">Klicken Sie auf den folgenden Link [, und sprechen Sie mit unserem Scuba bot](http://contososcubademo.azurewebsites.net/).</span><span class="sxs-lookup"><span data-stu-id="6d0d4-108">Click the following link and [talk to our Scuba Bot](http://contososcubademo.azurewebsites.net/).</span></span> <span data-ttu-id="6d0d4-109">Nehmen `I'm looking for scuba` wir an, und Sie können Ihnen dabei helfen, den Besuch Ihrer Träume zu verbuchern.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-109">Say `I'm looking for scuba` and it'll help you book the scuba trip of your dreams.</span></span>  

<span data-ttu-id="6d0d4-110">Alle Antworten des Bots werden mit adaptiven Karten erstellt.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-110">All of the bot's responses are created with Adaptive Cards.</span></span>

<span data-ttu-id="6d0d4-111">[![Bildschirm Abbildung von Scuba Chat](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)</span><span class="sxs-lookup"><span data-stu-id="6d0d4-111">[![Scuba chat screenshot](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)</span></span>

<span data-ttu-id="6d0d4-112">**Holen Sie sich den Code**: [den vollständigen Quellcode](https://github.com/matthidinger/ContosoScubaBot
) für den Quellcode für den Quellcode finden Sie auf GitHub.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-112">**Get the code**: the full [Contoso Scuba Bot source code](https://github.com/matthidinger/ContosoScubaBot
) can be found on GitHub.</span></span>


## <a name="bot-framework-integration"></a><span data-ttu-id="6d0d4-113">Bot Framework-Integration</span><span class="sxs-lookup"><span data-stu-id="6d0d4-113">Bot Framework Integration</span></span>

<span data-ttu-id="6d0d4-114">Mit dem [bot Framework](https://dev.botframework.com/) können Sie einen einzelnen bot schreiben, der in der Lage ist, mit Benutzern über mehrere Kanäle wie Skype, Microsoft Teams, Facebook Messenger usw. zu chatten.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-114">With the [Bot Framework](https://dev.botframework.com/) you can write a single bot that is able to chat with users across multiple "channels", like Skype, Microsoft Teams, Facebook Messenger, etc.</span></span>

## <a name="walkthrough"></a><span data-ttu-id="6d0d4-115">Exemplarische Vorgehensweise</span><span class="sxs-lookup"><span data-stu-id="6d0d4-115">Walkthrough</span></span>

<span data-ttu-id="6d0d4-116">Es ist recht einfach, dem bot eine Adaptive Karte hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-116">It's pretty straight forward to add an Adaptive Card to your bot.</span></span>

### <a name="step-0-start-with-a-basic-message"></a><span data-ttu-id="6d0d4-117">Schritt 0: Starten mit einer grundlegenden Nachricht</span><span class="sxs-lookup"><span data-stu-id="6d0d4-117">Step 0: Start with a basic message</span></span>

<span data-ttu-id="6d0d4-118">Im folgenden finden Sie eine Standard `message` Nutzlast des bot-Frameworks, die an beliebige Kanäle übermittelt und dem Benutzer Text angezeigt werden kann.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-118">Here's a standard Bot Framework `message` payload that can be delivered to any channel and display text to the user.</span></span>

```json
{
   "type": "message",
   "text": "Plain text is ok, but sometimes I long for more..."
}
```

### <a name="step-1-add-an-adaptive-card-attachment"></a><span data-ttu-id="6d0d4-119">Schritt 1: Hinzufügen einer adaptiven Karte`attachment`</span><span class="sxs-lookup"><span data-stu-id="6d0d4-119">Step 1: Add an Adaptive Card `attachment`</span></span>

<span data-ttu-id="6d0d4-120">Zum Hinzufügen eines gewissen Werts über nur Text verfügt das bot Framework über ein `attachments`Konzept von.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-120">To add some richness beyond just text, the Bot Framework has a concept of `attachments`.</span></span> 

<span data-ttu-id="6d0d4-121">Fügen wir eine Adaptive Karte an, die benutzerdefinierten Text anzeigt.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-121">Let's attach an Adaptive Card that displays custom text.</span></span>

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

### <a name="step-2-build-even-richer-cards"></a><span data-ttu-id="6d0d4-123">Schritt 2: Erstellen Sie noch umfangreichere Karten</span><span class="sxs-lookup"><span data-stu-id="6d0d4-123">Step 2: Build even richer cards</span></span> 

<span data-ttu-id="6d0d4-124">Adaptive Karten bieten viel mehr als nur anpassbaren Text.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-124">Adaptive Cards offer much more than just customizable text.</span></span> 

<span data-ttu-id="6d0d4-125">Sie haben folgende Möglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="6d0d4-125">You can:</span></span> 

* <span data-ttu-id="6d0d4-126">Zu `Images` Ihrer Karte hinzufügen</span><span class="sxs-lookup"><span data-stu-id="6d0d4-126">Add `Images` to your card</span></span>
* <span data-ttu-id="6d0d4-127">Organisieren Sie Ihre Inhalte `Containers` mit und`Columns`</span><span class="sxs-lookup"><span data-stu-id="6d0d4-127">Organize your content with `Containers` and `Columns`</span></span>
* <span data-ttu-id="6d0d4-128">Fügen Sie mehrere Typen von hinzu.`Actions`</span><span class="sxs-lookup"><span data-stu-id="6d0d4-128">Add multiple types of `Actions`</span></span>
* <span data-ttu-id="6d0d4-129">Von `Input` Benutzern erfassen</span><span class="sxs-lookup"><span data-stu-id="6d0d4-129">Collect `Input` from your users</span></span>
* <span data-ttu-id="6d0d4-130">Eine Karte haben`show another card`</span><span class="sxs-lookup"><span data-stu-id="6d0d4-130">Have one card `show another card`</span></span>
* <span data-ttu-id="6d0d4-131">[Sehen Sie sich den vollständigen Schema-Explorer](http://adaptivecards.io/explorer/)an!</span><span class="sxs-lookup"><span data-stu-id="6d0d4-131">[Check out the full schema explorer](http://adaptivecards.io/explorer/)!</span></span> 

## <a name="platform-sdks"></a><span data-ttu-id="6d0d4-132">Plattform-sdgs</span><span class="sxs-lookup"><span data-stu-id="6d0d4-132">Platform SDKs</span></span>

<span data-ttu-id="6d0d4-133">Wenn Ihr Bot mithilfe von .net oder nodejs entwickelt wurde, verfügen wir über Bibliotheken, die das Erstellen von adaptiven Karten noch vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-133">If your bot is developed using .NET or NodeJS we have libraries to make building Adaptive Cards even easier.</span></span>

<span data-ttu-id="6d0d4-134">Platform</span><span class="sxs-lookup"><span data-stu-id="6d0d4-134">Platform</span></span>|<span data-ttu-id="6d0d4-135">Installieren</span><span class="sxs-lookup"><span data-stu-id="6d0d4-135">Install</span></span>|<span data-ttu-id="6d0d4-136">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6d0d4-136">Learn more</span></span>
--------|-------|----------
<span data-ttu-id="6d0d4-137">.NET</span><span class="sxs-lookup"><span data-stu-id="6d0d4-137">.NET</span></span> | `Install-Package AdaptiveCards -IncludePrerelease` | [<span data-ttu-id="6d0d4-138">Bot Framework .NET-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="6d0d4-138">Bot Framework .NET Docs</span></span>](https://docs.microsoft.com/en-us/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
<span data-ttu-id="6d0d4-139">NodeJS</span><span class="sxs-lookup"><span data-stu-id="6d0d4-139">NodeJS</span></span> | `npm install adaptivecards` | [<span data-ttu-id="6d0d4-140">Bot Framework-nodejs-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="6d0d4-140">Bot Framework NodeJS Docs</span></span>](https://docs.microsoft.com/en-us/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)


## <a name="channel-status"></a><span data-ttu-id="6d0d4-141">Kanalstatus</span><span class="sxs-lookup"><span data-stu-id="6d0d4-141">Channel status</span></span>

<span data-ttu-id="6d0d4-142">Mit dem bot Framework können Sie den bot in mehreren Kanälen veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-142">The Bot Framework lets you publish your bot to multiple channels.</span></span> <span data-ttu-id="6d0d4-143">Wir arbeiten mit verschiedenen Kanälen, um eine vollständige Unterstützung für Adaptive Karten bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-143">We're working with various channels to provide full support for Adaptive Cards.</span></span> <span data-ttu-id="6d0d4-144">Aktuelle Informationen finden Sie auf der Seite [Partner Status](../resources/partners.md) .</span><span class="sxs-lookup"><span data-stu-id="6d0d4-144">See the [Partner Status](../resources/partners.md) page for the latest.</span></span>


## <a name="dive-in"></a><span data-ttu-id="6d0d4-145">Tauchen Sie ein!</span><span class="sxs-lookup"><span data-stu-id="6d0d4-145">Dive in!</span></span>

<span data-ttu-id="6d0d4-146">Wir haben in diesem Tutorial nur die Oberfläche durchgegangen. sehen Sie sich daher die unten aufgeführten Links an, um weitere Möglichkeiten zu finden, wie Adaptive Karten ihren bot verbessern können.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-146">We've just scratched the surface in this tutorial, so please take a look at the links below to explore more ways that Adaptive Cards can enhance your bot.</span></span>

* <span data-ttu-id="6d0d4-147">[Beispiel Karten zur Inspiration durchsuchen](http://adaptivecards.io/samples/)</span><span class="sxs-lookup"><span data-stu-id="6d0d4-147">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="6d0d4-148">Verwenden des [Schema-Explorers](http://adaptivecards.io/explorer) , um die verfügbaren Elemente zu erlernen</span><span class="sxs-lookup"><span data-stu-id="6d0d4-148">Use the [Schema Explorer](http://adaptivecards.io/explorer) to learn the available elements</span></span>
* <span data-ttu-id="6d0d4-149">Erstellen einer Karte mithilfe der [interaktiven](http://adaptivecards.io/visualizer/index.html?hostApp=Skype) Schnellansicht</span><span class="sxs-lookup"><span data-stu-id="6d0d4-149">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span></span>
* <span data-ttu-id="6d0d4-150">Feedback zu Feedback [erhalten](http://adaptivecards.io/connect)</span><span class="sxs-lookup"><span data-stu-id="6d0d4-150">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>
