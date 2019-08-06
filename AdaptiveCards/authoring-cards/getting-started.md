---
title: Erste Schritte
author: matthidinger
ms.author: mahiding
ms.date: 11/9/2017
ms.topic: article
ms.openlocfilehash: c9a0ad07ba5fefbcdc35239591c02fe0720b5b66
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732652"
---
# <a name="getting-started"></a><span data-ttu-id="2f5ca-102">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="2f5ca-102">Getting Started</span></span> 

<span data-ttu-id="2f5ca-103">Eine Adaptive Karte ist ein JSON-serialisiertes Karten Objektmodell.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-103">An Adaptive Card is a JSON-serialized card object model.</span></span>

## <a name="adaptive-card-structure"></a><span data-ttu-id="2f5ca-104">Adaptive Karten Struktur</span><span class="sxs-lookup"><span data-stu-id="2f5ca-104">Adaptive Card structure</span></span>

<span data-ttu-id="2f5ca-105">Die grundlegende Struktur einer Karte lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="2f5ca-105">The basic structure of a card is as follows:</span></span>

* <span data-ttu-id="2f5ca-106">`AdaptiveCard`-Das Stamm Objekt beschreibt die adaptivecard selbst, einschließlich der Element Umgebung, ihrer Aktionen, der Art und Weise, wie Sie gesprochen werden soll, und der Schema Version, die zum Rendering erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-106">`AdaptiveCard` - The root object describes the AdaptiveCard itself, including its element makeup, its actions, how it should be spoken, and the schema version required to render it.</span></span>
* <span data-ttu-id="2f5ca-107">`body`-Der Hauptteil der Karte besteht aus Bausteinen, die als `elements`bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-107">`body` - The body of the card is made up of building-blocks known as `elements`.</span></span> <span data-ttu-id="2f5ca-108">Elemente können in nahezu unendlichen Anordnungen zusammengesetzt werden, um viele Kartentypen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-108">Elements can be composed in nearly infinite arrangements to create many types of cards.</span></span> 
* <span data-ttu-id="2f5ca-109">`actions`-Viele Karten verfügen über eine Reihe von Aktionen, die ein Benutzer ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-109">`actions` - Many cards have a set of actions a user may take on it.</span></span> <span data-ttu-id="2f5ca-110">Diese Eigenschaft beschreibt die Aktionen, die in der Regel in einer "Aktionsleiste" am unteren Rand gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-110">This property describes those actions which typically get rendered in an "action bar" at the bottom.</span></span>

### <a name="example-card"></a><span data-ttu-id="2f5ca-111">Beispiel Karte</span><span class="sxs-lookup"><span data-stu-id="2f5ca-111">Example Card</span></span>

<span data-ttu-id="2f5ca-112">Diese Beispiel Karte enthält eine einzelne Textzeile, gefolgt von einem Bild.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-112">This sample card which includes a single line of text followed by an image.</span></span>

```json
{
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "Here is a ninja cat"
        },
        {
            "type": "Image",
            "url": "http://adaptivecards.io/content/cats/1.png"
        }
    ]
}
```

## <a name="type-property"></a><span data-ttu-id="2f5ca-113">`Type` -Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="2f5ca-113">`Type` property</span></span>

<span data-ttu-id="2f5ca-114">Jedes-Element verfügt `type` über eine-Eigenschaft, die angibt, welche Art von Objekt es ist.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-114">Every element has a `type` property which identifies what kind of object it is.</span></span> <span data-ttu-id="2f5ca-115">Wenn Sie sich die obige Karte ansehen, sehen Sie, dass zwei Elemente vorhanden `TextBlock` sind: `Image`a und.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-115">Looking at the above card, you can see we have two elements, a `TextBlock` and an `Image`.</span></span>

<span data-ttu-id="2f5ca-116">Alle adaptiven Kartenelemente werden **vertikal gestapelt** und **auf die Breite der übergeordneten** Elemente `display: block` (in HTML) erweitert.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-116">All Adaptive Card elements **stack vertically** and **expand to the width of their parent** (think `display: block` in HTML).</span></span> <span data-ttu-id="2f5ca-117">Sie können jedoch einen `ColumnSet` verwenden, um parallele Container Spalten zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-117">However, you can use a `ColumnSet` to create side-by-side columns of containers.</span></span>

## <a name="adaptive-elements"></a><span data-ttu-id="2f5ca-118">Adaptive Elemente</span><span class="sxs-lookup"><span data-stu-id="2f5ca-118">Adaptive Elements</span></span>

<span data-ttu-id="2f5ca-119">Die grundlegendsten Elemente sind:</span><span class="sxs-lookup"><span data-stu-id="2f5ca-119">The most fundamental elements are:</span></span>

* <span data-ttu-id="2f5ca-120">**TextBlock** -fügt einen TextBlock mit Eigenschaften hinzu, um zu steuern, wie der Text aussieht.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-120">**TextBlock** - adds a block of text with properties to control what the text looks like</span></span>
* <span data-ttu-id="2f5ca-121">**Image** : Fügt ein Bild mit Eigenschaften hinzu, um zu steuern, wie das Bild aussieht.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-121">**Image** - adds an image with properties to control what the image looks like</span></span>

## <a name="container-elements"></a><span data-ttu-id="2f5ca-122">Container Elemente</span><span class="sxs-lookup"><span data-stu-id="2f5ca-122">Container elements</span></span>

<span data-ttu-id="2f5ca-123">Karten können auch Container enthalten, die eine Auflistung von untergeordneten Elementen anordnen.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-123">Cards can also have containers, which arrange a collection of child elements.</span></span>

* <span data-ttu-id="2f5ca-124">**Container** : definiert eine Auflistung von Elementen.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-124">**Container** - Defines a a collection of elements</span></span>
* <span data-ttu-id="2f5ca-125">**ColumnSet/Column** : definiert eine Auflistung von Spalten, wobei jede Spalte ein Container ist.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-125">**ColumnSet/Column** - Defines a collection of columns, each column is a container</span></span>
* <span data-ttu-id="2f5ca-126">**FactSet** -Container von Fakten</span><span class="sxs-lookup"><span data-stu-id="2f5ca-126">**FactSet** - Container of Facts</span></span>
* <span data-ttu-id="2f5ca-127">**ImageSet** -Container von Bildern, damit die Benutzeroberfläche für eine Auflistung von Bildern die passende Fotogalerie Darstellung anzeigen kann.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-127">**ImageSet** - Container of Images so that UI can show appropriate photo gallery experience for a collection of images.</span></span>

## <a name="input-elements"></a><span data-ttu-id="2f5ca-128">Eingabeelemente</span><span class="sxs-lookup"><span data-stu-id="2f5ca-128">Input elements</span></span>

<span data-ttu-id="2f5ca-129">Eingabeelemente ermöglichen es Ihnen, eine native Benutzeroberfläche zum Erstellen von einfachen Formularen anzufordern:</span><span class="sxs-lookup"><span data-stu-id="2f5ca-129">Input elements allow you to ask for native UI to build simple forms:</span></span>

* <span data-ttu-id="2f5ca-130">**Input. Text** : Text Inhalt vom Benutzer erhalten</span><span class="sxs-lookup"><span data-stu-id="2f5ca-130">**Input.Text** - get text content from the user</span></span>
* <span data-ttu-id="2f5ca-131">**Input. Date** : ein Datum vom Benutzer erhalten.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-131">**Input.Date** - get a Date from the user</span></span>
* <span data-ttu-id="2f5ca-132">**Eingabe. Zeit** zum Zeitpunkt der Benutzereingabe</span><span class="sxs-lookup"><span data-stu-id="2f5ca-132">**Input.Time** - get a Time from the user</span></span>
* <span data-ttu-id="2f5ca-133">**Input. Number** : eine Zahl vom Benutzer erhalten.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-133">**Input.Number** - get a Number from the user</span></span>
* <span data-ttu-id="2f5ca-134">**Input. choiceset** : Geben Sie dem Benutzer einen Satz von Optionen, und lassen Sie ihn auswählen.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-134">**Input.ChoiceSet** - Give the user a set of choices and have them pick</span></span>
* <span data-ttu-id="2f5ca-135">**Eingabe.** umschalten: Hiermit wird dem Benutzer eine einzige Auswahl zwischen zwei Elementen gewährt.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-135">**Input.Toggle** - Give the user a single choice between two items and have them pick</span></span>

## <a name="actions"></a><span data-ttu-id="2f5ca-136">Aktionen</span><span class="sxs-lookup"><span data-stu-id="2f5ca-136">Actions</span></span>

<span data-ttu-id="2f5ca-137">Aktionen fügen der Karte Schaltflächen hinzu.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-137">Actions add buttons to the card.</span></span> <span data-ttu-id="2f5ca-138">Diese können eine Reihe von Aktionen durchführen, z. b. das Öffnen einer URL oder das Senden von Daten.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-138">These can perform a variety of actions, like opening a URL or submitting some data.</span></span>

* <span data-ttu-id="2f5ca-139">**Action. OpenURL** : die Schaltfläche öffnet eine externe URL für die Anzeige.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-139">**Action.OpenUrl** - the button opens an external URL for viewing</span></span>
* <span data-ttu-id="2f5ca-140">**Action. showcard** : fordert an, dass dem Benutzer eine unter Karte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-140">**Action.ShowCard** - Requests a sub-card to be shown to the user.</span></span>
* <span data-ttu-id="2f5ca-141">**Action. Submit** : bitten Sie, alle Eingabeelemente in einem Objekt zu erfassen, das dann über eine Methode, die von der Host Anwendung definiert wird, an Sie gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-141">**Action.Submit** - Ask for all of the input elements to be gathered up into an object which is then sent to you through some method defined by the host application.</span></span>

> <span data-ttu-id="2f5ca-142">**Beispiel für Action. Submit**: Mit Skype sendet eine Aktion. Submit eine bot Framework-bot-Aktivität zurück an den bot mit der **value** -Eigenschaft, die ein Objekt mit allen Eingabedaten enthält.</span><span class="sxs-lookup"><span data-stu-id="2f5ca-142">**Example Action.Submit**: With Skype, an Action.Submit will send a Bot Framework bot activity back to the bot with the **Value** property containing an object with all of the input data on it.</span></span>

## <a name="learn-more"></a><span data-ttu-id="2f5ca-143">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2f5ca-143">Learn More</span></span>

* <span data-ttu-id="2f5ca-144">[Beispiel Karten zur Inspiration durchsuchen](http://adaptivecards.io/samples/)</span><span class="sxs-lookup"><span data-stu-id="2f5ca-144">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="2f5ca-145">Verwenden des [Schema-Explorers](http://adaptivecards.io/explorer) zum Durchsuchen der verfügbaren Elemente</span><span class="sxs-lookup"><span data-stu-id="2f5ca-145">Use the [Schema Explorer](http://adaptivecards.io/explorer) to browse the available elements</span></span>
* <span data-ttu-id="2f5ca-146">Erstellen einer Karte mithilfe der [interaktiven](http://adaptivecards.io/visualizer/) Schnellansicht</span><span class="sxs-lookup"><span data-stu-id="2f5ca-146">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/)</span></span>
* <span data-ttu-id="2f5ca-147">Feedback zu Feedback [erhalten](http://adaptivecards.io/connect)</span><span class="sxs-lookup"><span data-stu-id="2f5ca-147">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>
