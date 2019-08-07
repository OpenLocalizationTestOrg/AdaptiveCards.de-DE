---
title: Android-SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: e565606f4a112d4f1fa08e2989f392f1abf0887f
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732537"
---
# <a name="extensibility---android"></a>Erweiterbarkeit: Android

Der Android-Renderer kann erweitert werden, um mehrere Szenarien zu unterstützen, darunter:
* [Benutzerdefinierte Verarbeitung von Karten Elementen](#custom-parsing-of-card-elements)
* [Benutzerdefiniertes Rendering von Karten Elementen](#custom-rendering-of-card-elements)
* [Benutzerdefiniertes Rendering von Aktionen](#custom-rendering-of-actions) (Seit v 1.2)
* [Laden von benutzerdefinierten Images](#custom-image-loading) (Seit v 1.0.1)
* [Laden benutzerdefinierter Medien](#custom-media-loading) (Seit v 1.1)

## <a name="custom-parsing-of-card-elements"></a>Benutzerdefinierte Verarbeitung von Karten Elementen

Sie können den Parser erweitern, um Kartenelemente zu unterstützen, die Sie definiert haben. Angenommen, wir haben einen neuen Elementtyp, der wie folgt aussieht:
```json
{
    "type" : "MyType",
    "MyTypeData" : "My data"
}
```

Anschließend zeigen die folgenden Zeilen, wie Sie Sie in ein cardelta-Element analysieren können, das sich vom basecardelta-Element erstreckt:
```java
public class MyCustomCardElement extends BaseCardElement
{

    public MyCustomCardElement(CardElementType type) {
        super(type);
    }

    public String getMyTypeData()
    {
        return myTypeData;
    }

    public void setMyTypeData(String data)
    {
        myTypeData = data;
    }

    private String myTypeData;
}

public class MyCardElementParser extends BaseCardElementParser
{
    @Override
    public BaseCardElement Deserialize(ElementParserRegistration elementParserRegistration, ActionParserRegistration actionParserRegistration, JsonValue value)
    {
        MyCustomCardElement element = new CustomCardElement(CardElementType.Custom);
        element.SetElementTypeString("MyType");
        String val = value.getString();
        try {
            JSONObject obj = new JSONObject(val);
            element.setMyTypeData(obj.getString("secret"));
        } catch (JSONException e) {
            e.printStackTrace();
            element.setMyTypeData("Failed");
        }
        return element;
    }
}
```

Und auf diese Weise können Sie den Parser registrieren und ein adaptivecard-Objekt abrufen, das das benutzerdefinierte Element enthält:
```java
// Create an ElementParserRegistrationObject and add your parser to it
ElementParserRegistration elementParserRegistration = new ElementParserRegistration();
elementParserRegistration.AddParser("MyType", new MyCardElementParser());

AdaptiveCard adaptiveCard = AdaptiveCard.DeserializeFromString(jsonText, elementParserRegistration);
```

Nächstes kommt zum Rendern des benutzerdefinierten Elements.

## <a name="custom-rendering-of-card-elements"></a>Benutzerdefiniertes Rendering von Karten Elementen

> [!IMPORTANT]
>
> **Liste der wichtigen Änderungen**
>
> [Wichtige Änderungen für v 1.2](#breaking-changes-for-v12)

Um unseren eigenen benutzerdefinierten Renderer für den Typ zu definieren, müssen wir zuerst eine Klasse erstellen, ```BaseCardElementRenderer```die sich von erstreckt:
```java
public class MyCardElementRenderer extends BaseCardElementRenderer
{
    @Override
    public View render(Context context, FragmentManager fragmentManager, ViewGroup viewGroup, BaseCardElement baseCardElement, Vector<IInputHandler> inputActionHandlerList, ICardActionHandler cardActionHandler, HostConfig hostConfig, ContainerStyle containerStyle) {

        //Call findImplObj on baseCardElement to get the instance we returned at parse. We can then cast that object to our type
        CustomCardElement element = (CustomCardElement) baseCardElement.findImplObj();

        //Create some view and add it to the view group
        TextView textView = new TextView(context);
        textView.setText(element.getMyTypeData());
        textView.setAllCaps(true);
        viewGroup.addView(textView);

        //return the view
        return textView;
    }
}
```

Anschließend registrieren wir diesen Renderer wie folgt:
```java
CardRendererRegistration.getInstance().registerRenderer("MyType", new CustomBlahRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler,  hostConfig);
```

### <a name="breaking-changes-for-v12"></a>Wichtige Änderungen für v 1.2

Die ```render``` -Methode wurde so geändert, ```RenderedAdaptiveCard``` dass Sie ```ContainerStyle``` den-Parameter enthält, und wurde für eine renderargs geändert, in der das ContainerStyle jetzt enthalten ist, sodass eine Klasse, die den basecardelta-entrenderer erweitert, wie folgt aussehen sollte:

```
public class MyCardElementRenderer extends BaseCardElementRenderer
{
    @Override
    public View render(RenderedAdaptiveCard renderedAdaptiveCard, Context context, FragmentManager fragmentManager, ViewGroup viewGroup,
                       BaseCardElement baseCardElement, ICardActionHandler cardActionHandler, HostConfig hostConfig, RenderArgs renderArgs)
    { }
}
```

## <a name="custom-parsing-of-card-actions"></a>Benutzerdefinierte Verarbeitung von Karten Aktionen

Ähnlich wie beim Analysieren von benutzerdefinierten Karten Elementen in v 1.2 wurde die Möglichkeit, benutzerdefinierte Aktionen zu analysieren, eingeführt. Angenommen, wir haben einen neuen Aktionstyp, der wie folgt aussieht:
```json
{
    "type" : "MyAction",
    "ActionData" : "My data"
}
```

Anschließend zeigen die folgenden Zeilen, wie Sie Sie in ein "aktionelement" analysieren können, ```BaseActionElement```das sich von erstreckt:
```java
public class MyActionElement extends BaseActionElement
{
    public MyActionElement(ActionType type) 
    {
        super(type);
    }

    public String getActionData()
    {
        return mActionData;
    }

    public void setActionData(String s)
    {
        mActionData = s;
    }

    private String mActionData;
    public static final String MyActionId = "myAction";
}

public class MyActionParser extends ActionElementParser
{
    @Override
    public BaseActionElement Deserialize(ParseContext context, JsonValue value)
    {
        MyActionElement element = new MyActionElement(ActionType.Custom);
        element.SetElementTypeString(MyActionElement.MyActionId);
        String val = value.getString();
        try {
            JSONObject obj = new JSONObject(val);
            element.setActionData(obj.getString("ActionData"));
        } catch (JSONException e) {
            e.printStackTrace();
            element.setActionData("Failure");
        }
        return element;
    }

    @Override
    public BaseActionElement DeserializeFromString(ParseContext context, String jsonString)
    {
        MyActionElement element = new MyActionElement(ActionType.Custom);
        element.SetElementTypeString(MyActionElement.MyActionId);
        try {
            JSONObject obj = new JSONObject(jsonString);
            element.setBackwardString(obj.getString("ActionData"));
        } catch (JSONException e) {
            e.printStackTrace();
            element.setBackwardString("Failure");
        }
        return element;
    }
}
```

In den nächsten Zeilen wird veranschaulicht, wie Sie den Parser registrieren und ein adaptivecard-Objekt abrufen, das das benutzerdefinierte Action-Element enthält:
```java
// Create an ActionParserRegistration and add your parser to it
ActionParserRegistration actionParserRegistration = new ActionParserRegistration();
actionParserRegistration.AddParser(MyActionElement.MyActionId, new MyActionParser());

ParseContext context = new ParseContext(null, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

Nächste Schritte zum Rendern der benutzerdefinierten Aktion

## <a name="custom-rendering-of-actions"></a>Benutzerdefiniertes Rendering von Aktionen

Um einen eigenen benutzerdefinierten aktionsrenderer für den Typ zu definieren, müssen wir zuerst eine Klasse erstellen ```BaseActionElementRenderer```, die sich von erstreckt:
```java
public class MyActionRenderer extends BaseActionElementRenderer
{
    @Override
    public Button render(RenderedAdaptiveCard renderedCard,
                         Context context,
                         FragmentManager fragmentManager,
                         ViewGroup viewGroup,
                         BaseActionElement baseActionElement,
                         ICardActionHandler cardActionHandler,
                         HostConfig hostConfig,
                         RenderArgs renderArgs)
    {
        Button myActionButton = new Button(context);

        CustomActionElement customAction = (CustomActionElement) baseActionElement.findImplObj();

        myActionButton.setBackgroundColor(getResources().getColor(R.color.greenActionColor));
        myActionButton.setText(customAction.getMessage());
        myActionButton.setAllCaps(false);
        myActionButton.setOnClickListener(new BaseActionElementRenderer.ActionOnClickListener(renderedCard, baseActionElement, cardActionHandler));

        viewGroup.addView(myActionButton);

        return myActionButton;
    }
}
```

Anschließend registrieren wir diesen Renderer wie folgt:
```java
CardRendererRegistration.getInstance().registerActionRenderer("myAction", new CustomActionRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
```

## <a name="custom-rendering-of-actions"></a>Benutzerdefiniertes Rendering von Aktionen

[!IMPORTANT]
> Änderungen am benutzerdefinierten Rendering von Aktionen sind für v 1.2 geplant, aber noch nicht abgeschlossen.

## <a name="custom-image-loading"></a>Laden von benutzerdefinierten Images

### <a name="ionlineimageloader"></a>IOnlineImageLoader

> [!IMPORTANT]
> **Es kann nur ein "ionlineimageloader" registriert werden, und es hat Vorrang vor der Standardmethode zum Abrufen von Bildern.**

Um Entwicklern das Abrufen von Bildern zu ermöglichen, die nicht nur aus einer Online Quelle heruntergeladen oder abgerufen werden konnten, bevor Sie abgerufen werden konnten, wurde der ionlineimageloader hinzugefügt, um diese Art von Situationen zu lösen. Um einen onlineimageloader zu implementieren, müssen Sie nur die-Methode implementieren. 

```java
public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException
```

Im folgenden finden Sie ein Beispiel für einen onlineimageloader, der alle Bilder für ein Cat-Bild ändert.

```java
public class OnlineImageLoader implements IOnlineImageLoader
{
    public OnlineImageLoader(){}

    @Override
    public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException
    {
        String catImnageUri = "http://adaptivecards.io/content/cats/1.png";
        byte[] bytes = HttpRequestHelper.get(catImnageUri);
        if (bytes == null)
        {
            throw new IOException("Failed to retrieve content from " + catImnageUri);
        }

        Bitmap bitmap = BitmapFactory.decodeByteArray(bytes, 0, bytes.length);

        if (bitmap == null)
        {
            throw new IOException("Failed to convert content to bitmap: " + new String(bytes));
        }

        return new HttpRequestResult<>(bitmap);
    }
}
```

Zum Registrieren dieses Bild Lade Moduls müssen Sie schließlich nur diese Zeile zum Code hinzufügen.

```java
CardRendererRegistration.getInstance().registerOnlineImageLoader(new OnlineImageLoader());
```

### <a name="iresourceresolver-deprecates-ionlineimageloader"></a>Iresourceresolver (ist von "ionlineimageloader" veraltet)

Für v 1.2 wurde dem Android-Renderer die Unterstützung für Full resourceresolvers hinzugefügt. Die Implementierung eines ressourcenresolvers ähnelt der eines "ionlineimageloader", aber mit resourceresolvers kann ein Entwickler mehrere Methoden zum Abrufen von Bildern aus einer beliebigen Art von Quelle auf einer einzelnen Karte hinzufügen. Dies geschieht durch Verknüpfen der einzelnen resourceresolver. zu einem eindeutigen Präfix, das abgefragt wird, wenn versucht wird, ein Bild abzurufen. 

Sie können einen resourceresolver implementieren, der diesem ähnelt.

```java
public class ResourceResolver implements IResourceResolver
{
    @Override
    public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync) throws IOException, URISyntaxException
    {
        Bitmap bitmap;
        String dataUri = AdaptiveBase64Util.ExtractDataFromUri(uri);
        CharVector decodedDataUri = AdaptiveBase64Util.Decode(dataUri);
        byte[] decodedByteArray = Util.getBytes(decodedDataUri);
        bitmap = BitmapFactory.decodeByteArray(decodedByteArray, 0, decodedByteArray.length);

        return new HttpRequestResult<>(bitmap);
    }

    @Override
    public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync, int maxWidth) throws IOException, URISyntaxException
    {
        Bitmap bitmap;
        String dataUri = AdaptiveBase64Util.ExtractDataFromUri(uri);
        CharVector decodedDataUri = AdaptiveBase64Util.Decode(dataUri);

        if (uri.startsWith("data:image/svg")) {
            String svgString = AdaptiveBase64Util.ExtractDataFromUri(uri);
            String decodedSvgString = URLDecoder.decode(svgString, "UTF-8");
            Sharp sharp = Sharp.loadString(decodedSvgString);
            Drawable drawable = sharp.getDrawable();
            bitmap = ImageUtil.drawableToBitmap(drawable, maxWidth);
        }
        else
        {
            try
            {
                return genericImageLoaderAsync.loadDataUriImage(uri);
            }
            catch (Exception e)
            {
                return new HttpRequestResult<>(e);
            }
        }

        return new HttpRequestResult<>(bitmap);
    }
}
```

Wie bereits erwähnt, können Sie mehrere resourceresolvers registrieren. um einen resourceresolver zu registrieren, können Sie dies tun.

```java
 CardRendererRegistration.getInstance().registerResourceResolver("data", new ResourceResolver());
 CardRendererRegistration.getInstance().registerResourceResolver("anotherPrefix", new AnotherResourceResolver());
```

#### <a name="transforming-an-ionlineimageloader-to-an-iresourceresolver"></a>Transformieren eines "ionlineimageloader" in einen "iresourceresolver" 

Die Transformation von "ionlineimageloader" in "iresourceresolver" ist eine recht einfache Aufgabe, da die Methoden der letzteren versucht haben, so ähnlich wie der "ionlineimageloader" wie möglich zu bleiben.

```java
 // IOnlineImageLoader
 public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException

 // IResourceResolver
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync) throws IOException, URISyntaxException
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync, int maxWidth) throws IOException, URISyntaxException
```

Wie Sie sehen können, sind die größten Änderungen

* ```loadOnlineImage(String, GenericImageLoaderAsync)```wurde umbenannt in```resolveImageResource(String, GenericImageLoaderAsync)```
* eine Überladung ```resolveImageResource(String, GenericImageLoaderAsync)``` für wurde ```resolveImageResource(String, GenericImageLoaderAsync, int)``` hinzugefügt, um Szenarios zu unterstützen, in denen die maximale Breite erforderlich ist.

## <a name="custom-media-loading"></a>Laden benutzerdefinierter Medien

> [!IMPORTANT]
> **Beachten Sie ```IOnlineMediaLoader```,dass die API-Ebene 23 oder Android M hinzugefügt wurde. ```MediaDataSource```**

Zusammen mit der Einbeziehung des Medien Elements war auch die Einbindung der ionlinemedialoader-Schnittstelle, die es Entwicklern ermöglicht, die für das zugrunde liegende Media Player-Element verwendete [mediadatasource](https://developer.android.com/reference/android/media/MediaDataSource) zu überschreiben. **(Erfordert Android M)**

Zuerst müssen Sie eine Klasse erstellen, die "ionlineimageloader" implementiert.

```java
@RequiresApi(api = Build.VERSION_CODES.M)
public class OnlineMediaLoader implements IOnlineMediaLoader
{
    /* This class checks if the media source exists */
    public class OnlineFileAvailableChecker extends AsyncTask<String, Void, Boolean>
    {
        public OnlineFileAvailableChecker(String uri)
        {
            m_uri = uri;
        }

        @Override
        protected Boolean doInBackground(String... strings) {
            // if the provided uri is a valid uri or is valid with the resource resolver, then use that
            // otherwise, try to get the media from a local file
            try
            {
                HttpRequestHelper.query(m_uri);
                return true;
            }
            catch (Exception e)
            {
                // Do nothing if the media was not found at all
                e.printStackTrace();
                return false;
            }
        }

        private String m_uri;
   }

       
   @Override
   public MediaDataSource loadOnlineMedia(MediaSourceVector mediaSources, IMediaDataSourceOnPreparedListener mediaDataSourceOnPreparedListener)
   {
       final long mediaSourcesSize = mediaSources.size();
       for(int i = 0; i < mediaSourcesSize; i++)
       {
           String mediaUri = mediaSources.get(i).GetUrl();

           OnlineFileAvailableChecker checker = new OnlineFileAvailableChecker(mediaUri);
           try
           {
               Boolean fileExists = checker.execute("").get();
               if(fileExists)
               {
                   return new MediaDataSourceImpl(mediaUri, mediaDataSourceOnPreparedListener);
               }
           }
           catch (Exception e) { }
       }
       return null;
    }
}
```

Nachdem Sie diese Klasse implementiert haben, können Sie Ihre onlinemedialoader-Klasse registrieren, indem Sie hinzufügen. 
```java
  CardRendererRegistration.getInstance().registerOnlineMediaLoader(new OnlineMediaLoader());
```
