---
title: Native Formatierung-Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: c3190fbb31480f92c774d233476436ee2cfc52b3
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733022"
---
# <a name="native-styling---android"></a>Native Formatierung: Android

Das Native formatieren wird für den Android-Renderer nicht unterstützt, mit v 1.2 wird die Unterstützung für das Formatieren einiger Eigenschaften eingeführt

## <a name="action-sentiment"></a>Aktions Stimmung

Die Stimmungs Stimmung ist in **v 1.2** enthalten und unterstützt nicht so viele Stile wie andere Versionen. Aktionen mit *destruktiver* oder *positiver* Stimmungslage können durch Implementieren eines gültigen Stils und durch Hinzufügen der folgenden Zeile zum Styles. XML für Ihr Projekt

```styles.xml
 <item name="adaptiveActionDestructive">@style/adaptiveActionDestructive</item>
 <item name="adaptiveActionPositive">@style/adaptiveActionPositive</item>
```

## <a name="inline-action"></a>Inline Aktion

Text Eingaben mit einer Inline Aktion ermöglichen das Formatieren der Aktion, die gerendert wird. Dies ermöglicht das Formatieren der Aktion als Schaltfläche (adaptiveinlineaction) oder als Bild (adaptiveinlineaction Image).

```styles.xml
 <item name="adaptiveInlineAction">@style/adaptiveInlineAction</item>
 <item name="adaptiveInlineActionImage">@style/adaptiveInlineActionImage</item>
```

> [!IMPORTANT]
> Alle Elementnamen müssen wie hier gezeigt beibehalten werden, da der Renderer genau nach diesen Namen sucht.
