---
title: Adaptive Karten für Windows-Entwickler
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: c9ea788cfbc8e365cdece1cd8f42c3718b7bc3e7
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733117"
---
# <a name="adaptive-cards-for-windows-developers"></a><span data-ttu-id="9293d-102">Adaptive Karten für Windows-Entwickler</span><span class="sxs-lookup"><span data-stu-id="9293d-102">Adaptive Cards for Windows Developers</span></span>



## <a name="timeline"></a><span data-ttu-id="9293d-103">Zeitachse</span><span class="sxs-lookup"><span data-stu-id="9293d-103">Timeline</span></span>

<span data-ttu-id="9293d-104">Die erste Windows-Funktion zur Unterstützung von adaptiven Karten ist Timeline, eine völlig neue, in Windows 10 1803 eingeführte neue Darstellung.</span><span class="sxs-lookup"><span data-stu-id="9293d-104">The first Windows experience to supports Adaptive Cards is Timeline, a brand new experience first introduced in Windows 10 1803.</span></span> 

![Zeitachse](media/windows/timeline.png)

### <a name="useractivity-api"></a><span data-ttu-id="9293d-106">Useractivity-API</span><span class="sxs-lookup"><span data-stu-id="9293d-106">UserActivity API</span></span>

<span data-ttu-id="9293d-107">Die [`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) API füllt eine Aktivität in die Zeitachse auf.</span><span class="sxs-lookup"><span data-stu-id="9293d-107">The [`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) API is what populates an Activity into Timeline.</span></span>

<span data-ttu-id="9293d-108">Die Adaptive Karte wird über die `Content` -Eigenschaft von `VisualElement`bereitgestellt, wie unten gezeigt:</span><span class="sxs-lookup"><span data-stu-id="9293d-108">The Adaptive Card will be supplied via the `Content` property of `VisualElement`, as seen below:</span></span>

```csharp
UserActivity userActivity = await channel.GetOrCreateUserActivityAsync(activityId, new HostName("contoso.com"));
userActivity.ActivationUri = new Uri("rss-reader:article?" + article.Link);
userActivity.DisplayText = article.Title; //used for details tile text
userActivity.VisualElements.Content = AdaptiveCardBuilder.CreateAdaptiveCardFromJson(jsonString);
await userActivity.SaveAsync();
```

### <a name="learn-more"></a><span data-ttu-id="9293d-109">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9293d-109">Learn more</span></span>

<span data-ttu-id="9293d-110">In dieser Sitzung bei Build 2017 werden Benutzeraktivitäten in "detial" behandelt.</span><span class="sxs-lookup"><span data-stu-id="9293d-110">This session at Build 2017 covers User Activities in detial.</span></span>

<iframe src="https://channel9.msdn.com/Events/Build/2017/B8108/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

## <a name="other-windows-surfaces"></a><span data-ttu-id="9293d-111">Weitere Windows-Oberflächen</span><span class="sxs-lookup"><span data-stu-id="9293d-111">Other Windows Surfaces</span></span>
<span data-ttu-id="9293d-112">Wir haben noch nichts zu teilen, aber wir arbeiten daran, Adaptive Karten in mehr Windows-Umgebungen zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="9293d-112">We don't have anything to share just yet, but we're working on incorporating Adaptive Cards into more Windows experiences.</span></span>

## <a name="dive-in"></a><span data-ttu-id="9293d-113">Tauchen Sie ein!</span><span class="sxs-lookup"><span data-stu-id="9293d-113">Dive in!</span></span>

<span data-ttu-id="9293d-114">Wir haben die Oberfläche in diesem Tutorial kaum verkratzt. sehen Sie sich also die Links unten an, um weitere Informationen zu adaptiven Karten zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="9293d-114">We've barely scratched the surface in this tutorial, so check back soon and browse the links below to explore more about Adaptive Cards.</span></span>

* <span data-ttu-id="9293d-115">[Beispiel Karten zur Inspiration durchsuchen](http://adaptivecards.io/samples/)</span><span class="sxs-lookup"><span data-stu-id="9293d-115">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="9293d-116">Verwenden des [Schema-Explorers](http://adaptivecards.io/explorer) , um die verfügbaren Elemente zu erlernen</span><span class="sxs-lookup"><span data-stu-id="9293d-116">Use the [Schema Explorer](http://adaptivecards.io/explorer) to learn the available elements</span></span>
* <span data-ttu-id="9293d-117">Erstellen einer Karte mithilfe der [interaktiven](http://adaptivecards.io/visualizer/index.html?hostApp=Skype) Schnellansicht</span><span class="sxs-lookup"><span data-stu-id="9293d-117">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span></span>
* <span data-ttu-id="9293d-118">Feedback zu Feedback [erhalten](http://adaptivecards.io/connect)</span><span class="sxs-lookup"><span data-stu-id="9293d-118">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>
