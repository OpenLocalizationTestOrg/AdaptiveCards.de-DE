---
title: Text Features
author: matthidinger
ms.author: mahiding
ms.date: 11/09/2017
ms.topic: article
ms.openlocfilehash: f7ea40b80df4d976c0a8a86b15254018fdf2fac6
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732672"
---
# <a name="text-features"></a><span data-ttu-id="02292-102">Text Features</span><span class="sxs-lookup"><span data-stu-id="02292-102">Text features</span></span>

<span data-ttu-id="02292-103">`TextBlock`bietet einige erweiterte Funktionen zum Formatieren und Lokalisieren des Texts.</span><span class="sxs-lookup"><span data-stu-id="02292-103">`TextBlock` offers some advanced features for formatting and localizing the text.</span></span>

## <a name="markdown"></a><span data-ttu-id="02292-104">Markdown</span><span class="sxs-lookup"><span data-stu-id="02292-104">Markdown</span></span>
<span data-ttu-id="02292-105">Um Inline Markup zu unterstützen, unterstützen Adaptive Karten eine **Teilmenge** der markdownsyntax.</span><span class="sxs-lookup"><span data-stu-id="02292-105">To support inline markup, Adaptive Cards support a **subset** of Markdown syntax.</span></span>

<span data-ttu-id="02292-106">_Unterstützt_</span><span class="sxs-lookup"><span data-stu-id="02292-106">_Supported_</span></span>

| <span data-ttu-id="02292-107">Textstil</span><span class="sxs-lookup"><span data-stu-id="02292-107">Text Style</span></span>      | <span data-ttu-id="02292-108">Markdown</span><span class="sxs-lookup"><span data-stu-id="02292-108">Markdown</span></span> |
|-----------------|-----|
| <span data-ttu-id="02292-109">**Fett**</span><span class="sxs-lookup"><span data-stu-id="02292-109">**Bold**</span></span>        | ```**Bold**``` |
| <span data-ttu-id="02292-110">_Kursiv_</span><span class="sxs-lookup"><span data-stu-id="02292-110">_Italic_</span></span>        | ```_Italic_``` |
| <span data-ttu-id="02292-111">Aufzählungs Liste</span><span class="sxs-lookup"><span data-stu-id="02292-111">Bullet list</span></span>     | ```- Item 1\r- Item 2\r- Item 3``` | 
| <span data-ttu-id="02292-112">Nummerierte Liste</span><span class="sxs-lookup"><span data-stu-id="02292-112">Numbered list</span></span>   | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="02292-113">Links</span><span class="sxs-lookup"><span data-stu-id="02292-113">Hyperlinks</span></span>      | ```[Title](url)``` |

<span data-ttu-id="02292-114">_Nicht unterstützt_</span><span class="sxs-lookup"><span data-stu-id="02292-114">_Not supported_</span></span>

* <span data-ttu-id="02292-115">Header</span><span class="sxs-lookup"><span data-stu-id="02292-115">Headers</span></span>
* <span data-ttu-id="02292-116">Tabellen</span><span class="sxs-lookup"><span data-stu-id="02292-116">Tables</span></span>
* <span data-ttu-id="02292-117">Bilder</span><span class="sxs-lookup"><span data-stu-id="02292-117">Images</span></span>
* <span data-ttu-id="02292-118">Alles, was nicht in der obigen Tabelle angegeben ist</span><span class="sxs-lookup"><span data-stu-id="02292-118">Anything not in the table above</span></span>

### <a name="markdown-example"></a><span data-ttu-id="02292-119">Markdown-Beispiel</span><span class="sxs-lookup"><span data-stu-id="02292-119">Markdown Example</span></span>

<span data-ttu-id="02292-120">Die folgende Nutzlast würde etwa wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="02292-120">The below payload would render something like this:</span></span>

![markdown-Bildschirmfoto](media/text-features/markdown.png)

```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "This is some **bold** text"
        },
        {
            "type": "TextBlock",
            "text": "This is some _italic_ text"
        },
        {
            "type": "TextBlock",
            "text": "- Bullet \r- List \r",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "1. Numbered\r2. List\r",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "Check out [Adaptive Cards](http://adaptivecards.io)"
        }
    ]
}
```

## <a name="datetime-formatting-and-localization"></a><span data-ttu-id="02292-122">Datums-/Uhrzeitformatierung und Lokalisierung</span><span class="sxs-lookup"><span data-stu-id="02292-122">Date/Time formatting and localization</span></span>

<span data-ttu-id="02292-123">Manchmal wissen Sie nicht, dass die Zeitzone des Benutzers, der die Karte empfängt, angezeigt wird `DATE()` , `TIME()` daher bieten Adaptive Kartenfunktionen und Formatierungsfunktionen zum automatischen lokalisieren der Zeit auf dem Zielgerät.</span><span class="sxs-lookup"><span data-stu-id="02292-123">Sometimes you won't know the timezone of the user receiving the card, so Adaptive Cards offers `DATE()` and `TIME()` formatting functions to automatically localize the time on the target device.</span></span>

### <a name="datetime-example"></a><span data-ttu-id="02292-124">Datums-/Uhrzeit-Beispiel</span><span class="sxs-lookup"><span data-stu-id="02292-124">Date/Time Example</span></span>

```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "Your package will arrive on {{DATE(2017-02-14T06:00:00Z, SHORT)}} at {{TIME(2017-02-14T06:00:00Z)}}",
            "wrap": true
        }
    ]
}
```

<span data-ttu-id="02292-125">Die obige Karte wird angezeigt:</span><span class="sxs-lookup"><span data-stu-id="02292-125">The above card will display:</span></span> 

> <span data-ttu-id="02292-126">**Ihr Paket wird am Dienstag, 14. Februar, 2017 um 6:00 Uhr eintreffen.**</span><span class="sxs-lookup"><span data-stu-id="02292-126">**Your package will arrive on Tue, Feb 14th, 2017 at 6:00 AM**</span></span>

### <a name="datetime-function-rules"></a><span data-ttu-id="02292-127">Datums-/uhrzeitfunktionsregeln</span><span class="sxs-lookup"><span data-stu-id="02292-127">Date/Time function rules</span></span>

<span data-ttu-id="02292-128">Es gibt einige Regeln, mit denen die Datums-/Uhrzeitfunktionen auf allen Plattformen ordnungsgemäß interpretiert werden können.</span><span class="sxs-lookup"><span data-stu-id="02292-128">There are some rules to properly interpret the the date/time functions on every platform.</span></span> <span data-ttu-id="02292-129">Wenn die Regeln nicht erfüllt sind, wird die unformatierte Zeichenfolge für den Benutzer angezeigt, und niemand möchte dies.</span><span class="sxs-lookup"><span data-stu-id="02292-129">If the rules aren't met then the raw string will be displayed to the user, and no one wants that.</span></span>

1. <span data-ttu-id="02292-130">beachten Sie (muss alle Caps sein)</span><span class="sxs-lookup"><span data-stu-id="02292-130">**CASE SENSITIVE** (must be all caps)</span></span>
1. <span data-ttu-id="02292-131">Es sind **keine Leerzeichen** zwischen den `{{`Klammern, `}}`oder enthalten.</span><span class="sxs-lookup"><span data-stu-id="02292-131">**NO SPACES** between the `{{`, `}}`, or parentheses</span></span>
1. <span data-ttu-id="02292-132">**Strikte [RFC 3389](https://tools.ietf.org/html/rfc3339) -Formatierung** (Siehe Beispiele unten)</span><span class="sxs-lookup"><span data-stu-id="02292-132">**STRICT [RFC 3389](https://tools.ietf.org/html/rfc3339) FORMATTING** (See examples below)</span></span>
1. <span data-ttu-id="02292-133">**Muss** ein gültiges Datum und eine gültige Uhrzeit sein</span><span class="sxs-lookup"><span data-stu-id="02292-133">**MUST BE** a valid date and time</span></span>

### <a name="valid-formats"></a><span data-ttu-id="02292-134">Gültige Formate</span><span class="sxs-lookup"><span data-stu-id="02292-134">Valid formats</span></span>

* `2017-02-14T06:08:00Z`
* `2017-02-14T06:08:00-07:00`
* `2017-02-14T06:08:00+07:00`

### <a name="date-formatting-param"></a><span data-ttu-id="02292-135">Datums Formatierungs Parameter</span><span class="sxs-lookup"><span data-stu-id="02292-135">Date formatting param</span></span>

<span data-ttu-id="02292-136">Für Datumsangaben kann ein optionaler Parameter angegeben werden, um die Ausgabe zu formatieren.</span><span class="sxs-lookup"><span data-stu-id="02292-136">For dates, an optional param may be specified to format the output.</span></span>


|       <span data-ttu-id="02292-137">Format</span><span class="sxs-lookup"><span data-stu-id="02292-137">Format</span></span>        |            <span data-ttu-id="02292-138">Beispiel</span><span class="sxs-lookup"><span data-stu-id="02292-138">Example</span></span>            |
|---------------------|-------------------------------|
| <span data-ttu-id="02292-139">`COMPACT`Vorgegebene</span><span class="sxs-lookup"><span data-stu-id="02292-139">`COMPACT` (Default)</span></span> |          <span data-ttu-id="02292-140">"2/13/2017"</span><span class="sxs-lookup"><span data-stu-id="02292-140">"2/13/2017"</span></span>          |
|       `SHORT`       |     <span data-ttu-id="02292-141">"Mon, 13. Feb, 2017"</span><span class="sxs-lookup"><span data-stu-id="02292-141">"Mon, Feb 13th, 2017"</span></span>     |
|       `LONG`        | <span data-ttu-id="02292-142">"Montag, 13. Februar, 2017"</span><span class="sxs-lookup"><span data-stu-id="02292-142">"Monday, February 13th, 2017"</span></span> |

