---
title: 'Erweiterbarkeit: IOS SDK'
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 13245ced3f4f657e13793bfdf1d212e44d2b6a41
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732947"
---
# <a name="extensibility---ios"></a>Erweiterbarkeit-IOS

## <a name="changing-per-element-rendering"></a>Ändern des Renderings pro Element

Entwickler können das Aussehen von renderred adaptivecards-Elementen, z. b. TextBlock, anpassen.
Im folgenden Beispiel wird gezeigt, wie die Hintergrundfarbe von "numinput" geändert werden kann.

```objective-c
ACRRegistration *registration = [ACRRegistration getInstance];
// register custom renderer with registration
// custom renderer must implement ACRIBaseCardElementRenderer protocol
// for more information, please refer to CustomInputNumberRenderer.mm
 [registration setBaseCardElementRenderer:[CustomInputNumberRenderer getInstance] cardElementType:ACRNumberInput];
 ...
/// CustiomInputNumberRenderer.mm
- (UIView *)render:(UIView<ACRIContentHoldingView> *)viewGroup
              rootViewController:(UIViewController *)vc
              inputs:(NSArray *)inputs
     baseCardElement:(ACOBaseCardElement *)acoElem
          hostConfig:(ACOHostConfig *)acoConfig
  {
      ACRInputNumberRenderer *defaultRenderer = [ACRInputNumberRenderer getInstance];
 
      UIView *input = [defaultRenderer render:viewGroup
                           rootViewController:vc
                                       inputs:inputs
                              baseCardElement:acoElem
                                   hostConfig:acoConfig];
      if(input)
      {   
          // customize background color of input
          [input setBackgroundColor: [UIColor colorWithRed:1.0
                                                     green:59.0/255.0
                                                      blue:48.0/255.0
                                                     alpha:1.0]];
      }
      return input;
  }
  ```

 ## <a name="additional-property"></a>Zusätzliche Eigenschaft

 Entwickler können auch zusätzliche Eigenschaften als Teil der JSON-Nutzlast senden.
Beispielsweise kann neben "Abstand" und "ID" der JSON-Nutzlast für basecardelta "Radius" für Ecken von TextBlock der JSON-Nutzlast hinzugefügt werden.

 ```objective-c
 "type":"TextBlock",
 ...
 "radius":20,
 ...
 ```

 ```objective-c
         NSData *additionalProperty = [acoElem additionalProperty];
          if(additionalProperty) {
              NSDictionary *dictionary = [NSJSONSerialization JSONObjectWithData:additionalProperty options:NSJSONReadingMutableLeaves error:nil];
              radiusForMyTextBlock = dictionary[@"radius"];
          ...
```
 ## <a name="custom-parsing"></a>Benutzerdefinierte Verarbeitung

Entwickler können auch eine benutzerdefinierte Verarbeitung haben und ein neues Benutzeroberflächen Element zur Adpative Karte hinzugefügt haben, z. b. die Statusanzeige. Weitere Informationen finden Sie in der CustomProgressBarRenderer.mm.
Der benutzerdefinierte Parser muss das acoibasecardelta-Parser-Protokoll implementieren. die deserializetocustomelement-Methode muss die angegebene JSON-Nutzlast, die als NSData angegeben ist, analysieren und einen Zeiger auf das UIView-Objekt zurückgeben, das dem gerenderten adaptivecard-Objekt hinzugefügt

```objective-c
      CustomProgressBarRenderer *progressBarRenderer = [[CustomProgressBarRenderer alloc] init];
      [registration setCustomElementParser:progressBarRenderer];
```objective-c