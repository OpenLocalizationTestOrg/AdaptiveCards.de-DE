---
title: 'Aktionen: .net WPF SDK'
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: dfee76c5dc0a8caafcd693b47337c28f84e71a53
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732737"
---
# <a name="actions---net-wpf"></a><span data-ttu-id="5305a-102">Aktionen: .net WPF</span><span class="sxs-lookup"><span data-stu-id="5305a-102">Actions - .NET WPF</span></span>

<span data-ttu-id="5305a-103">Alle `actions` innerhalb der Karte werden als WPF `Button`s angezeigt, aber es liegt an Ihrer APP, zu behandeln, was geschieht, wenn ein Benutzer Sie drückt.</span><span class="sxs-lookup"><span data-stu-id="5305a-103">Any `actions` within the card will render as WPF `Button`s, but it's up to your app to handle what happens when a user presses them.</span></span> 

<span data-ttu-id="5305a-104">Das `RenderedAdaptiveCard` -Objekt stellt `OnAction` für diesen Zweck ein Ereignis bereit.</span><span class="sxs-lookup"><span data-stu-id="5305a-104">The `RenderedAdaptiveCard` object provides an `OnAction` event for this purpose.</span></span>

```csharp
// Event handler fires when a user clicks an action within the card
renderedCard.OnAction += MyActionHandler;

private void MyActionHandler(RenderedAdaptiveCard sender, AdaptiveActionEventArgs e)
{
    if (e.Action is AdaptiveOpenUrlAction openUrlAction)
    {
        Process.Start(openUrlAction.Url.AbsoluteUri);
    }
    else if (e.Action is AdaptiveShowCardAction showCardAction)
    {
        // Action.ShowCard can be rendered inline automatically
        // ... but if you want to handle show card as a "popup", you handle this event
        if (_myHostConfig.Actions.ShowCard.ActionMode == ShowCardActionMode.Popup)
        {
            var dialog = new ShowCardWindow(showCardAction.Title, showCardAction, Resources);
            dialog.Owner = this;
            dialog.ShowDialog();
        }
    }
    else if (e.Action is AdaptiveSubmitAction submitAction)
    {
        var inputs = sender.UserInputs.AsJson();
        inputs.Merge(submitAction.Data);
        MessageBox.Show(this, JsonConvert.SerializeObject(inputs, Formatting.Indented), "SubmitAction");
    }
}
```
