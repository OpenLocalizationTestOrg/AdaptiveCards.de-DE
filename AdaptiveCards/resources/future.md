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
# <a name="future-work"></a><span data-ttu-id="e2e42-102">Zukünftige Arbeit</span><span class="sxs-lookup"><span data-stu-id="e2e42-102">Future work</span></span>

<span data-ttu-id="e2e42-103">Wir haben zwar einen hervorragenden Fortschritt beim Definieren adaptiver Karten vorgenommen, aber es gibt noch viel Arbeit.</span><span class="sxs-lookup"><span data-stu-id="e2e42-103">While we have made excellent progress defining adaptive cards, there is still lots of work to do.</span></span> <span data-ttu-id="e2e42-104">Wir hoffen, dass wir durch aktive Entwickler Communitys wie botness und große Partner wie Slack und KiK ein hervorragend Ökosystem plattformübergreifender Karten erstellen können.</span><span class="sxs-lookup"><span data-stu-id="e2e42-104">Our hope is that through active developer communities like botness, and great partners like Slack and Kik, we can create a great ecosystem of cross-platform cards.</span></span>

## <a name="roadmap"></a><span data-ttu-id="e2e42-105">Wegweiser</span><span class="sxs-lookup"><span data-stu-id="e2e42-105">Roadmap</span></span>

<span data-ttu-id="e2e42-106">Die [aktuelle (nicht abschließende) Roadmap](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog)finden Sie hier.</span><span class="sxs-lookup"><span data-stu-id="e2e42-106">You can see our [current (non-final) roadmap here](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog).</span></span> <span data-ttu-id="e2e42-107">Beachten Sie, dass alle hier aufgeführten Änderungen unterliegen und keine Garantie für den Versand ist.</span><span class="sxs-lookup"><span data-stu-id="e2e42-107">Note that anything on here is subject to change, and is not a guarantee of shipping.</span></span>

## <a name="future-ideas"></a><span data-ttu-id="e2e42-108">Zukünftige Ideen</span><span class="sxs-lookup"><span data-stu-id="e2e42-108">Future ideas</span></span>

<span data-ttu-id="e2e42-109">Im folgenden finden Sie einige zukünftige Ideen, die sich einfach in der Brainstorming-Phase befinden.</span><span class="sxs-lookup"><span data-stu-id="e2e42-109">The following are some future ideas we have, which are simply in the brainstorm stage.</span></span> <span data-ttu-id="e2e42-110">Wenn Sie an einer dieser Themen interessiert sind, informieren Sie uns in einem Kommentar.</span><span class="sxs-lookup"><span data-stu-id="e2e42-110">If you're interested in any of these, let us know in a comment.</span></span>

### <a name="great-looking-cards-from-data"></a><span data-ttu-id="e2e42-111">Hervorragend aussehende Karten aus Daten</span><span class="sxs-lookup"><span data-stu-id="e2e42-111">Great looking Cards from Data</span></span>

<span data-ttu-id="e2e42-112">Wir wissen, dass viele Karten Autoren bereits über klar definierte Daten hinter ihren Karten verfügen.</span><span class="sxs-lookup"><span data-stu-id="e2e42-112">We know many card authors already have well-defined data behind their cards.</span></span> <span data-ttu-id="e2e42-113">Unser Plan besteht darin, ein Vorlagen Modell zu untersuchen, das das Generieren von Karten ermöglicht (serverseitige oder Client seitige), basierend auf den Daten und einem Repository von klar definierten und anpassbaren Vorlagen.</span><span class="sxs-lookup"><span data-stu-id="e2e42-113">Our plan is to explore a templating model that would allow cards to be generated (server side or client side) based on the data and a repository of well-defined and customizable templates.</span></span>

### <a name="make-cards-responsive"></a><span data-ttu-id="e2e42-114">Reaktionsfähig machen von Karten</span><span class="sxs-lookup"><span data-stu-id="e2e42-114">Make cards responsive</span></span>

<span data-ttu-id="e2e42-115">Kartenlayouts sollten im verfügbaren Speicherplatz reaktiv sein.</span><span class="sxs-lookup"><span data-stu-id="e2e42-115">Card layouts should be reactive to available space.</span></span> <span data-ttu-id="e2e42-116">Adaptive Karten sind an verschiedene Geräte, UX-Stile und Benutzeroberflächen-Frameworks angepasst, sind aber noch nicht aktiv.</span><span class="sxs-lookup"><span data-stu-id="e2e42-116">Adaptive cards are adaptable to different devices, ux styles and and ui frameworks, but they are not reactive yet.</span></span> <span data-ttu-id="e2e42-117">Für-Elemente müssen zusätzliche Eigenschaften definiert werden, mit denen Karten Producer die erforderlichen Hinweise für die renderingbibliotheken bereitstellen können, damit Sie das Layout auf eine Weise ändern können, die die Absicht der Karte beibehält.</span><span class="sxs-lookup"><span data-stu-id="e2e42-117">Additional properties must be defined on elements which allow card producers to provide the necessary hints to the rendering libraries so that they can intelligently change the layout in a way which maintains the intent of the card.</span></span>

### <a name="responsive-exploration"></a><span data-ttu-id="e2e42-118">Reaktionsschnelle Untersuchung</span><span class="sxs-lookup"><span data-stu-id="e2e42-118">Responsive exploration</span></span>

* <span data-ttu-id="e2e42-119">Fügen Sie eine Wichtigkeits Eigenschaft hinzu, mit der die Wichtigkeit von Inhalten kommentiert wird.</span><span class="sxs-lookup"><span data-stu-id="e2e42-119">Add an **importance** property which annotates importance of content.</span></span> <span data-ttu-id="e2e42-120">Weniger wichtige Inhalte können gelöscht werden, um den verfügbaren Speicherplatz anzupassen.</span><span class="sxs-lookup"><span data-stu-id="e2e42-120">Less important content can be dropped to fit available space</span></span>
* <span data-ttu-id="e2e42-121">Fügen Sie **Einschränkungen** und **Richtlinien** Eigenschaften hinzu, die beschreiben, wie Sie reagieren, wenn Einschränkungen nicht erfüllt werden können.</span><span class="sxs-lookup"><span data-stu-id="e2e42-121">Add **constraints** and **policy** properties describing how to react when constraints can't be met.</span></span> 
  * <span data-ttu-id="e2e42-122">Inhalt ausblenden oder Inhalt auf kleinere Größe reduzieren.</span><span class="sxs-lookup"><span data-stu-id="e2e42-122">Hide content or collapse content to smaller size.</span></span>
  * <span data-ttu-id="e2e42-123">Fügen Sie einen Schwellenwert hinzu, bei dessen `columnSet` Überschreitung das Karussell der Spalten geändert wird.</span><span class="sxs-lookup"><span data-stu-id="e2e42-123">Add a threshold that, when exceeded, changes `columnSet` to carousel of columns.</span></span>

### <a name="new-element-types"></a><span data-ttu-id="e2e42-124">Neue Elementtypen</span><span class="sxs-lookup"><span data-stu-id="e2e42-124">New element types</span></span>

* <span data-ttu-id="e2e42-125">Maps?</span><span class="sxs-lookup"><span data-stu-id="e2e42-125">Maps?</span></span> <span data-ttu-id="e2e42-126">-Einbetten einer Karte in eine Karte mit Interaktivität oder Fall Back auf Bitmap</span><span class="sxs-lookup"><span data-stu-id="e2e42-126">- embed a map into a card with interactivity or fallback to bitmap</span></span>
* <span data-ttu-id="e2e42-127">*Welche Elemente möchten oder benötigen Sie*?</span><span class="sxs-lookup"><span data-stu-id="e2e42-127">*What elements do you want or need*?</span></span>

### <a name="new-rendering-libraries"></a><span data-ttu-id="e2e42-128">Neue renderingbibliotheken</span><span class="sxs-lookup"><span data-stu-id="e2e42-128">New rendering libraries</span></span>

* <span data-ttu-id="e2e42-129">REAG?</span><span class="sxs-lookup"><span data-stu-id="e2e42-129">React?</span></span>
* <span data-ttu-id="e2e42-130">Xamarin?</span><span class="sxs-lookup"><span data-stu-id="e2e42-130">Xamarin?</span></span>
* <span data-ttu-id="e2e42-131">*Welche Frameworks möchten Sie verwenden?*</span><span class="sxs-lookup"><span data-stu-id="e2e42-131">*What frameworks do you want?*</span></span>
