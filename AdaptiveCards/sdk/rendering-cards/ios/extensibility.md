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
# <a name="extensibility---ios"></a><span data-ttu-id="2d479-102">Erweiterbarkeit-IOS</span><span class="sxs-lookup"><span data-stu-id="2d479-102">Extensibility - iOS</span></span>

## <a name="changing-per-element-rendering"></a><span data-ttu-id="2d479-103">Ändern des Renderings pro Element</span><span class="sxs-lookup"><span data-stu-id="2d479-103">Changing per element rendering</span></span>

<span data-ttu-id="2d479-104">Entwickler können das Aussehen von renderred adaptivecards-Elementen, z. b. TextBlock, anpassen.</span><span class="sxs-lookup"><span data-stu-id="2d479-104">Developers can customize the look of renderred AdaptiveCards elements such as TextBlock.</span></span>
<span data-ttu-id="2d479-105">Im folgenden Beispiel wird gezeigt, wie die Hintergrundfarbe von "numinput" geändert werden kann.</span><span class="sxs-lookup"><span data-stu-id="2d479-105">Following example shows how one can change background color of NumberInput.</span></span>

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

 ## <a name="additional-property"></a><span data-ttu-id="2d479-106">Zusätzliche Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="2d479-106">Additional Property</span></span>

 <span data-ttu-id="2d479-107">Entwickler können auch zusätzliche Eigenschaften als Teil der JSON-Nutzlast senden.</span><span class="sxs-lookup"><span data-stu-id="2d479-107">Developers can also send in additional properties as part of json payload.</span></span>
<span data-ttu-id="2d479-108">Beispielsweise kann neben "Abstand" und "ID" der JSON-Nutzlast für basecardelta "Radius" für Ecken von TextBlock der JSON-Nutzlast hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="2d479-108">For example, in addition to "spacing" and "id" of json payload for BaseCardElement, one can add radius for corners of TextBlock to its json payload.</span></span>

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
 ## <a name="custom-parsing"></a><span data-ttu-id="2d479-109">Benutzerdefinierte Verarbeitung</span><span class="sxs-lookup"><span data-stu-id="2d479-109">Custom Parsing</span></span>

<span data-ttu-id="2d479-110">Entwickler können auch eine benutzerdefinierte Verarbeitung haben und ein neues Benutzeroberflächen Element zur Adpative Karte hinzugefügt haben, z. b. die Statusanzeige.</span><span class="sxs-lookup"><span data-stu-id="2d479-110">Developers can also have custom parsing and have new UI element added to adpative card such as progress bar.</span></span> <span data-ttu-id="2d479-111">Weitere Informationen finden Sie in der CustomProgressBarRenderer.mm.</span><span class="sxs-lookup"><span data-stu-id="2d479-111">Please check CustomProgressBarRenderer.mm for detail.</span></span>
<span data-ttu-id="2d479-112">Der benutzerdefinierte Parser muss das acoibasecardelta-Parser-Protokoll implementieren.</span><span class="sxs-lookup"><span data-stu-id="2d479-112">Custom parser must implement ACOIBaseCardElementParser protocol.</span></span> <span data-ttu-id="2d479-113">die deserializetocustomelement-Methode muss die angegebene JSON-Nutzlast, die als NSData angegeben ist, analysieren und einen Zeiger auf das UIView-Objekt zurückgeben, das dem gerenderten adaptivecard-Objekt hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="2d479-113">deserializeToCustomElement method should parses given json payload given as NSData and return a pointer to UIView object that will be added to AdaptiveCard rendered object.</span></span>

```objective-c
      CustomProgressBarRenderer *progressBarRenderer = [[CustomProgressBarRenderer alloc] init];
      [registration setCustomElementParser:progressBarRenderer];
```objective-c