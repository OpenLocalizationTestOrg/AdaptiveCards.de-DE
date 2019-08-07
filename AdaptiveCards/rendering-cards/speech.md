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
# <a name="handling-speech"></a>Umgang mit Sprache

Zur Unterstützung von sprach adaptiven `speak` Karten verfügt über die-Eigenschaft, die Informationen darüber enthält, wie eine Karte an einen Benutzer gelesen werden soll.

Das Sprachtag kann mithilfe von [SSML-Markup](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx)kommentiert werden. SSML bietet Ihnen die Möglichkeit, die Geschwindigkeit, den Ton und die Einfügung der Sprache zu steuern.  Es ermöglicht sogar das Streamen von Audiodaten oder das Rendering eines TTS-Audiostreams von Ihrem eigenen Dienst, sodass Sie eine große Menge an Anpassungen vornehmen können.

Es gibt zwei Muster für die Verwendung von Sprachen, die von einer Host Anwendung verwendet werden:
* **bei Übermittlung** : Wenn eine Karte übermittelt wird, kann ein Client die sprach Eigenschaft für die Karte lesen, um die Karte als Ganzes zu beschreiben.
* **Bedarfs** gesteuert: um ein umfassendem Barrierefreiheits Modell zu unterstützen, unterstützt das Schema ein Sprech Tag pro Element.  
Dies ermöglicht es Clients, jedes Element mit Barrierefreiheits Anforderungen an Empfänger zu lesen.

