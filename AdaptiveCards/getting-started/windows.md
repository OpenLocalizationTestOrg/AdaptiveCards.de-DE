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
# <a name="adaptive-cards-for-windows-developers"></a>Adaptive Karten für Windows-Entwickler



## <a name="timeline"></a>Zeitachse

Die erste Windows-Funktion zur Unterstützung von adaptiven Karten ist Timeline, eine völlig neue, in Windows 10 1803 eingeführte neue Darstellung. 

![Zeitachse](media/windows/timeline.png)

### <a name="useractivity-api"></a>Useractivity-API

Die [`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) API füllt eine Aktivität in die Zeitachse auf.

Die Adaptive Karte wird über die `Content` -Eigenschaft von `VisualElement`bereitgestellt, wie unten gezeigt:

```csharp
UserActivity userActivity = await channel.GetOrCreateUserActivityAsync(activityId, new HostName("contoso.com"));
userActivity.ActivationUri = new Uri("rss-reader:article?" + article.Link);
userActivity.DisplayText = article.Title; //used for details tile text
userActivity.VisualElements.Content = AdaptiveCardBuilder.CreateAdaptiveCardFromJson(jsonString);
await userActivity.SaveAsync();
```

### <a name="learn-more"></a>Weitere Informationen

In dieser Sitzung bei Build 2017 werden Benutzeraktivitäten in "detial" behandelt.

<iframe src="https://channel9.msdn.com/Events/Build/2017/B8108/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

## <a name="other-windows-surfaces"></a>Weitere Windows-Oberflächen
Wir haben noch nichts zu teilen, aber wir arbeiten daran, Adaptive Karten in mehr Windows-Umgebungen zu integrieren.

## <a name="dive-in"></a>Tauchen Sie ein!

Wir haben die Oberfläche in diesem Tutorial kaum verkratzt. sehen Sie sich also die Links unten an, um weitere Informationen zu adaptiven Karten zu erhalten.

* [Beispiel Karten zur Inspiration durchsuchen](http://adaptivecards.io/samples/)
* Verwenden des [Schema-Explorers](http://adaptivecards.io/explorer) , um die verfügbaren Elemente zu erlernen
* Erstellen einer Karte mithilfe der [interaktiven](http://adaptivecards.io/visualizer/index.html?hostApp=Skype) Schnellansicht
* Feedback zu Feedback [erhalten](http://adaptivecards.io/connect)
