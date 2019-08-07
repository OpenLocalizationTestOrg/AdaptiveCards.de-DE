---
title: Umgang mit Sprache
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: ea46a1c2c14a4cd2aded9672d7493561bbebbd16
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732617"
---
# <a name="handling-speech"></a><span data-ttu-id="65b94-102">Umgang mit Sprache</span><span class="sxs-lookup"><span data-stu-id="65b94-102">Handling speech</span></span>

<span data-ttu-id="65b94-103">Zur Unterstützung von sprach adaptiven `speak` Karten verfügt über die-Eigenschaft, die Informationen darüber enthält, wie eine Karte an einen Benutzer gelesen werden soll.</span><span class="sxs-lookup"><span data-stu-id="65b94-103">To support speech adaptive Cards has the `speak` property which contains information on how a card should be read aloud to a user.</span></span>

<span data-ttu-id="65b94-104">Das Sprachtag kann mithilfe von [SSML-Markup](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx)kommentiert werden.</span><span class="sxs-lookup"><span data-stu-id="65b94-104">The speech tag can be annotated using  [SSML markup](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx).</span></span> <span data-ttu-id="65b94-105">SSML bietet Ihnen die Möglichkeit, die Geschwindigkeit, den Ton und die Einfügung der Sprache zu steuern.</span><span class="sxs-lookup"><span data-stu-id="65b94-105">SSML gives you the ability control the speed, tone, inflection of the speech.</span></span>  <span data-ttu-id="65b94-106">Es ermöglicht sogar das Streamen von Audiodaten oder das Rendering eines TTS-Audiostreams von Ihrem eigenen Dienst, sodass Sie eine große Menge an Anpassungen vornehmen können.</span><span class="sxs-lookup"><span data-stu-id="65b94-106">It even allows you to stream audio or a render a TTS audio stream from your own service, giving you a great deal of customization.</span></span>

<span data-ttu-id="65b94-107">Es gibt zwei Muster für die Verwendung von Sprachen, die von einer Host Anwendung verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="65b94-107">There are 2 patterns for speak property usage by a host application:</span></span>
* <span data-ttu-id="65b94-108">**bei Übermittlung** : Wenn eine Karte übermittelt wird, kann ein Client die sprach Eigenschaft für die Karte lesen, um die Karte als Ganzes zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="65b94-108">**on delivery** - When a card is delivered a client may opt to read the Speak property for the card to describe the card as a whole.</span></span>
* <span data-ttu-id="65b94-109">**Bedarfs** gesteuert: um ein umfassendem Barrierefreiheits Modell zu unterstützen, unterstützt das Schema ein Sprech Tag pro Element.</span><span class="sxs-lookup"><span data-stu-id="65b94-109">**on demand** - In order to support a richer accessibility model the schema supports a speak tag per element.</span></span>  
<span data-ttu-id="65b94-110">Dies ermöglicht es Clients, jedes Element mit Barrierefreiheits Anforderungen an Empfänger zu lesen.</span><span class="sxs-lookup"><span data-stu-id="65b94-110">This allows for clients to read each element to recipients with accessibility requirements.</span></span>

