---
title: Android-SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 4723175bf94685c22d99fb15f3d1887ac37b8c57
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733007"
---
# <a name="getting-started---android"></a>Einstieg: Android

Dies ist ein Renderer, der auf Android native-Steuerelemente abzielt.

## <a name="install-maven-package"></a>Maven-Paket installieren

[![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)

Sie finden die veröffentlichten Pakete. ![hier,](https://search.maven.org/search?q=g:io.adaptivecards)

Wenn Sie die Bibliothek in Ihr Projekt einschließen möchten, müssen Sie diese Zeile in das Projekt "gradle. Build" im Abschnitt "Abhängigkeiten" einschließen.

```build.gradle
 implementation 'io.adaptivecards:adaptivecards-android:1.1.0'
```
Abhängig von der Version, die Sie in Ihr Projekt einschließen möchten, müssen Sie die Versionsnummer ändern.

## <a name="add-import"></a>Import hinzufügen

Fügen Sie diesen Import hinzu, um das Objektmodell einzubeziehen.

```
 import io.adaptivecards.objectmodel.*;
```

Um den Renderer einzuschließen, fügen Sie diesen Import hinzu.

```
 import io.adaptivecards.renderer.*;
```

## <a name="next-steps"></a>Nächste Schritte

Die nächsten Schritte finden Sie unter [Rendering a Card](render-a-card.md) !
