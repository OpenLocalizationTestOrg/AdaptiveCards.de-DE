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
# <a name="speech-and-advanced-customization"></a>Sprache und erweiterte Anpassung
Wir leben in einer Ära der Sprachinteraktion über Dienste wie Cortana.  Adaptive Karten werden von Tag a zur Unterstützung von Sprache entwickelt, sodass Sie neue praktische Szenarios ermöglichen.

Mit `speak` dem-Tag kann die Adaptive Karte an eine Umgebung übermittelt werden, in der eine visuelle Darstellung keine primäre Darstellung ist, wie z. b. ein Auto-Dashboard. 

## <a name="speak-property"></a>Eigenschaft "sprechen"
Zur Unterstützung von Sprache verfügen `speak` wir über eine Eigenschaft, die dem Benutzer Text enthält. Der Text kann mit der Sprache Synthese Markup Language ([SSML](https://msdn.microsoft.com/en-us/library/office/hh361578)) kommentiert werden. SSML steuert die Geschwindigkeit, den Ton und die Einfügung der Sprache.  Es ermöglicht Ihnen sogar das Streamen von Audiodaten oder das Rendering eines TTS-Audiostreams von Ihrem eigenen Dienst, sodass Sie viel Flexibilität bei der Anpassung haben.

Es gibt zwei Muster für die Verwendung von Spracheigenschaften durch eine Host Anwendung:

* **Bei der Übermittlung** : Wenn eine Karte übermittelt wird, kann der Client die sprach Eigenschaft für die Karte lesen, um die Karte als Ganzes zu beschreiben.
* **Bei Bedarf** : das Schema unterstützt ein Anfangstag für jedes Element, um ein umfasseneres Barrierefreiheits Modell zu unterstützen. Der Client kann eine Eigenschaft "sprechen" für jedes Element in der Karte lesen.

### <a name="examples"></a>Beispiele

```json
    "speak":"hello world!"

    "speak":"<s>This is sentence 1.</s><s>This is sentence two</s>"

    "speak":"<speak><audio src='https://www.soundjay.com/misc/bell-ringing-04.mp3'/><s>Time to wake up!</s></speak>"
```

## <a name="speech-content-design"></a>Design von Sprachinhalten

Der für Sprache entworfene Inhalt unterscheidet sich von Inhalten, die für die visuelle Darstellung entworfen wurden. Wenn Sie eine Karte entwerfen, entwerfen Sie eine vollständige visuelle Darstellung, um Benutzern Informationen auf eine Weise zur Verfügung zu stellen, die Sie erfreut. Beim Entwerfen der Sprache sollten Sie sich Gedanken darüber machen, wie Sie den Inhalt auf eine Weise beschreiben, die den Benutzer erfreut.  
