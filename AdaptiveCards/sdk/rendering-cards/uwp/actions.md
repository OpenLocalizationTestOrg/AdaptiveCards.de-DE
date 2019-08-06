---
title: 'Aktionen: UWP SDK'
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 98b4374ce6a31d6d7ec2416d3b4e451ef1c59d1b
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732497"
---
# <a name="actions---uwp"></a><span data-ttu-id="7d040-102">Aktionen-UWP</span><span class="sxs-lookup"><span data-stu-id="7d040-102">Actions - UWP</span></span>

<span data-ttu-id="7d040-103">Alle **Aktionen** innerhalb der Karte werden als UWP- **Schalt**Flächen gerendet, aber es liegt an Ihrer APP, zu behandeln, was geschieht, wenn ein Benutzer Sie drückt (mit Ausnahme von showcard-Aktionen... Weitere Informationen finden Sie unter Code Ausschnitt.)</span><span class="sxs-lookup"><span data-stu-id="7d040-103">Any **actions** within the card will render as UWP **Button**'s, but it's up to your app to handle what happens when a user presses them (except for ShowCard actions... see code snippet for more info).</span></span>

<span data-ttu-id="7d040-104">Das `RenderedAdaptiveCard` -Objekt stellt `Action` für diesen Zweck ein Ereignis bereit.</span><span class="sxs-lookup"><span data-stu-id="7d040-104">The `RenderedAdaptiveCard` object provides an `Action` event for this purpose.</span></span>

```csharp
// Render a card (as previously shown)
RenderedAdaptiveCard renderedAdaptiveCard =  renderer.RenderAdaptiveCard(card);

// ...

// Attach the event handler for action click events
renderedAdaptiveCard.Action += RenderedAdaptiveCard_Action;

private async void RenderedAdaptiveCard_Action(RenderedAdaptiveCard sender, AdaptiveActionEventArgs args)
{
    if (args.Action is AdaptiveOpenUrlAction openUrlAction)
    {
        await Launcher.LaunchUriAsync(openUrlAction.Url);
    }

    else if (args.Action is AdaptiveShowCardAction showCardAction)
    {
        // This is only fired if, in HostConfig, you set the ShowCard ActionMode to Popup.
        // Otherwise, the renderer will automatically display the card inline without firing this event.
    }

    else if (args.Action is AdaptiveSubmitAction submitAction)
    {
        // Get the data and inputs
        string data = submitAction.DataJson.Stringify();
        string inputs = args.Inputs.AsJson().Stringify();

        // Process them as desired
    }
}
```
