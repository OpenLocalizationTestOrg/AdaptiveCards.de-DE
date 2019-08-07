---
title: Rendering einer Karte Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 5ced7a2217ef6ef475aa344d92ad2f5e567266f8
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733002"
---
# <a name="render-a-card---android"></a>Rendering einer Karte: Android

Im folgenden wird beschrieben, wie Sie eine Karte mithilfe der Android SDK Rendering.

## <a name="create-adaptive-card-object-instance-from-json-text"></a>Erstellen einer adaptiven Karten Objektinstanz aus JSON-Text

```java
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, elementParserRegistration);
AdaptiveCard adaptiveCard = parseResult.GetAdaptiveCard();
```
> [!IMPORTANT]
> **Wichtige Änderungen für v 1.2**
> 

1. Der elementparameserregistration-Parameter wurde in den Parametertext geändert, der ein elementparameserregistration-Objekt und ein aktionseserregistration-Objekt enthält.

```java
ParseContext context = new ParseContext(); // Empty parseContext so only known elements up to v1.2 will be parsed
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

oder

```java
ParseContext context = new ParseContext(elementParserRegistration, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

## <a name="render-a-card"></a>Rendering einer Karte

```java
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
View v = renderedCard.getView();
```
