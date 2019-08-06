---
title: 'Aktionen: .net html SDK'
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: f577c0bab73e2bd1f75bb22dd7a41a7dbfd63307
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732852"
---
# <a name="actions---net-html"></a><span data-ttu-id="04ccd-102">Aktionen: .net-html</span><span class="sxs-lookup"><span data-stu-id="04ccd-102">Actions - .NET HTML</span></span>

<span data-ttu-id="04ccd-103">Die Karte `actions` der obersten Ebene wird als HTML `<button>`-Code dargestellt.</span><span class="sxs-lookup"><span data-stu-id="04ccd-103">Top-level card `actions` will render as an HTML `<button>`.</span></span> <span data-ttu-id="04ccd-104">Da es sich hierbei um eine serverseitige Bibliothek handelt, können Sie Client seitige Ereignishandler beim Drücken von Schaltflächen verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="04ccd-104">Since this is a server-side library it's up to you to wire up client-side event handlers when buttons are pressed.</span></span> <span data-ttu-id="04ccd-105">Jeder `<button>` in der HTML-Code verfügt über Attribute, die Sie verwenden können, um das richtige Verhalten zu verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="04ccd-105">Each `<button>` in the HTML will have attributes that you can use to wire up the proper behavior.</span></span>

<span data-ttu-id="04ccd-106">Einige Elemente verfügen über `selectAction` eine Eigenschaft (Container, Spalten, Bild), durch die Sie aufgerufen werden können.</span><span class="sxs-lookup"><span data-stu-id="04ccd-106">Some elements have a `selectAction` property (Container, Columns, Image) which makes them invokable.</span></span> <span data-ttu-id="04ccd-107">Wenn ein Element über einen `selectAction` verfügt, fügt der Renderer eine CSS- `ac-selectable`Klasse von zusammen mit den folgenden Attributen hinzu.</span><span class="sxs-lookup"><span data-stu-id="04ccd-107">If an element has a `selectAction` the renderer will add a CSS class of `ac-selectable`, along with the below attributes.</span></span>

<span data-ttu-id="04ccd-108">Aktionstyp</span><span class="sxs-lookup"><span data-stu-id="04ccd-108">Action Type</span></span> | <span data-ttu-id="04ccd-109">CSS-Klasse</span><span class="sxs-lookup"><span data-stu-id="04ccd-109">CSS class</span></span> | <span data-ttu-id="04ccd-110">Zusätzliche Attribute</span><span class="sxs-lookup"><span data-stu-id="04ccd-110">Additional attributes</span></span>
---|---|---
`Action.OpenUrl` | `ac-action-openUrl` | <span data-ttu-id="04ccd-111">`data-ac-url`(die `url` -Eigenschaft der Karte)</span><span class="sxs-lookup"><span data-stu-id="04ccd-111">`data-ac-url` (the `url` property from the card)</span></span>
`Action.Submit` | `ac-action-submit` | <span data-ttu-id="04ccd-112">`data-ac-data`(die `data` -Eigenschaft der Karte)</span><span class="sxs-lookup"><span data-stu-id="04ccd-112">`data-ac-data` (the `data` property from the card)</span></span>
`Action.ShowCard` | `ac-action-showCard` | <span data-ttu-id="04ccd-113">`data-ac-showcardid`(der `id` `<div>` der, die die innere Karte enthält)</span><span class="sxs-lookup"><span data-stu-id="04ccd-113">`data-ac-showcardid` (the `id` of the `<div>` containing the inner card)</span></span>