---
title: Sprache und erweiterte Anpassung
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 468d090dff0511f40cb7e5eedc4f4a18fa12aa3c
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732667"
---
# <a name="speech-and-advanced-customization"></a><span data-ttu-id="6ac9a-102">Sprache und erweiterte Anpassung</span><span class="sxs-lookup"><span data-stu-id="6ac9a-102">Speech and advanced customization</span></span>
<span data-ttu-id="6ac9a-103">Wir leben in einer Ära der Sprachinteraktion über Dienste wie Cortana.</span><span class="sxs-lookup"><span data-stu-id="6ac9a-103">We live in an era of speech interaction via services like Cortana.</span></span>  <span data-ttu-id="6ac9a-104">Adaptive Karten werden von Tag a zur Unterstützung von Sprache entwickelt, sodass Sie neue praktische Szenarios ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="6ac9a-104">Adaptive cards are designed from day one to support speech, enabling cool new hands-full scenarios.</span></span>

<span data-ttu-id="6ac9a-105">Mit `speak` dem-Tag kann die Adaptive Karte an eine Umgebung übermittelt werden, in der eine visuelle Darstellung keine primäre Darstellung ist, wie z. b. ein Auto-Dashboard.</span><span class="sxs-lookup"><span data-stu-id="6ac9a-105">The `speak` tag enables the adaptive card to be delivered to an environment where a visual display is not primary experience, such as to a car dashboard while driving.</span></span> 

## <a name="speak-property"></a><span data-ttu-id="6ac9a-106">Eigenschaft "sprechen"</span><span class="sxs-lookup"><span data-stu-id="6ac9a-106">Speak property</span></span>
<span data-ttu-id="6ac9a-107">Zur Unterstützung von Sprache verfügen `speak` wir über eine Eigenschaft, die dem Benutzer Text enthält.</span><span class="sxs-lookup"><span data-stu-id="6ac9a-107">To support speech we have a `speak` property which contains text to say to the user.</span></span> <span data-ttu-id="6ac9a-108">Der Text kann mit der Sprache Synthese Markup Language ([SSML](https://msdn.microsoft.com/en-us/library/office/hh361578)) kommentiert werden.</span><span class="sxs-lookup"><span data-stu-id="6ac9a-108">The text can be annotated using speech synthesis markup language ([SSML](https://msdn.microsoft.com/en-us/library/office/hh361578)).</span></span> <span data-ttu-id="6ac9a-109">SSML steuert die Geschwindigkeit, den Ton und die Einfügung der Sprache.</span><span class="sxs-lookup"><span data-stu-id="6ac9a-109">SSML controls the speed, tone, and inflection of the speech.</span></span>  <span data-ttu-id="6ac9a-110">Es ermöglicht Ihnen sogar das Streamen von Audiodaten oder das Rendering eines TTS-Audiostreams von Ihrem eigenen Dienst, sodass Sie viel Flexibilität bei der Anpassung haben.</span><span class="sxs-lookup"><span data-stu-id="6ac9a-110">It even allows you to stream audio or a render a TTS audio stream from your own service, giving you a great deal of flexibility for customization.</span></span>

<span data-ttu-id="6ac9a-111">Es gibt zwei Muster für die Verwendung von Spracheigenschaften durch eine Host Anwendung:</span><span class="sxs-lookup"><span data-stu-id="6ac9a-111">There are two patterns for speak property usage by a host application:</span></span>

* <span data-ttu-id="6ac9a-112">**Bei der Übermittlung** : Wenn eine Karte übermittelt wird, kann der Client die sprach Eigenschaft für die Karte lesen, um die Karte als Ganzes zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="6ac9a-112">**On delivery** - When a card is delivered, the client may opt to read the Speak property for the card to describe the card as a whole.</span></span>
* <span data-ttu-id="6ac9a-113">**Bei Bedarf** : das Schema unterstützt ein Anfangstag für jedes Element, um ein umfasseneres Barrierefreiheits Modell zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="6ac9a-113">**On demand** - In order to support a richer accessibility model, the schema supports a speak tag for each element.</span></span> <span data-ttu-id="6ac9a-114">Der Client kann eine Eigenschaft "sprechen" für jedes Element in der Karte lesen.</span><span class="sxs-lookup"><span data-stu-id="6ac9a-114">The client may read a Speak property  for each element in the card.</span></span>

### <a name="examples"></a><span data-ttu-id="6ac9a-115">Beispiele</span><span class="sxs-lookup"><span data-stu-id="6ac9a-115">Examples</span></span>

```json
    "speak":"hello world!"

    "speak":"<s>This is sentence 1.</s><s>This is sentence two</s>"

    "speak":"<speak><audio src='https://www.soundjay.com/misc/bell-ringing-04.mp3'/><s>Time to wake up!</s></speak>"
```

## <a name="speech-content-design"></a><span data-ttu-id="6ac9a-116">Design von Sprachinhalten</span><span class="sxs-lookup"><span data-stu-id="6ac9a-116">Speech content design</span></span>

<span data-ttu-id="6ac9a-117">Der für Sprache entworfene Inhalt unterscheidet sich von Inhalten, die für die visuelle Darstellung entworfen wurden.</span><span class="sxs-lookup"><span data-stu-id="6ac9a-117">Content designed for speech is different from content designed for visual display.</span></span> <span data-ttu-id="6ac9a-118">Wenn Sie eine Karte entwerfen, entwerfen Sie eine vollständige visuelle Darstellung, um Benutzern Informationen auf eine Weise zur Verfügung zu stellen, die Sie erfreut.</span><span class="sxs-lookup"><span data-stu-id="6ac9a-118">When you design a card, you are designing an entire visual experience to present information to a user in a way that delights them.</span></span> <span data-ttu-id="6ac9a-119">Beim Entwerfen der Sprache sollten Sie sich Gedanken darüber machen, wie Sie den Inhalt auf eine Weise beschreiben, die den Benutzer erfreut.</span><span class="sxs-lookup"><span data-stu-id="6ac9a-119">When designing for speech, you should think about how to verbally describe the content in a way that delights the user.</span></span>  
