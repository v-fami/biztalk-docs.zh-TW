---
title: "步驟 3： 實作 Echo 介面卡的連線 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc223901-3ad3-4e71-8672-fea6bb4efe65
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a735654fd03f5efb39fe73eb845f4db3632d283
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-implement-the-connection-for-the-echo-adapter"></a>步驟 3： 實作 Echo 介面卡的連線
![步驟 3 的 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-3of9.gif "Step_3of9")  
  
 **若要完成的時間：** 45 分鐘的時間  
  
 在此步驟中，您可以實作回應配接器的連線能力。 根據[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，您連接到目標系統時必須實作下列的抽象類別和介面。  
  
-   `Microsoft.ServiceModel.Channels.Common.ConnectionUri`  
  
-   `Microsoft.ServiceModel.Channels.Common.IConnection`  
  
-   `Microsoft.ServiceModel.Channels.Common.IConnectionFactory`  
  
 而不是衍生自上述抽象類別和介面，[!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]會自動產生三個衍生的類別、 EchoAdapterConnection、 EchoAdapterConnectionUri 和 EchoAdapterConnectionFactory。 除了建立類別，每個有預設的方法會擲回特定例外狀況， `System.NotImplementedException`。  這個陳述式會提醒開發人員實作每個類別。  類別實作時，您必須移除這個擲回例外狀況的陳述式。  
  
 在下列區段中，您可以更新這些三個類別，以取得更深入了解如何處理連接、 URI 結構為何，以及如何以程式設計方式擷取各種 URI 項目，然後使用 配接器內的這些項目。  
  
## <a name="prerequisites"></a>必要條件  
 在開始此步驟之前，您必須已順利完成[步驟 2： 分類的介面卡和連接屬性](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-categorize-the-adapter-and-connection-properties.md)。 而且您應該已經清楚了解`Microsoft.ServiceModel.Channels.Common.IConnection`， `Microsoft.ServiceModel.Channels.Common.IConnectionFactory`，和`Microsoft.ServiceModel.Channels.Common.ConnectionUri`類別。  
  
## <a name="connection-related-classes"></a>連線相關類別  
 [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]產生三個衍生的類別、 EchoAdapterConnection、 EchoAdapterConnectionUri 和 EchoAdapterConnectionFactory。 下面提供方法的每個相關聯的簡短概觀。  
  
### <a name="echoadapterconnection"></a>EchoAdapterConnection  
 根據您的配接器複雜度，您可能需要實作所有下列五個方法。 為了回應配接器，也不支援大多數，因為回應配接器範例並不包含任何目標系統。  
  
|**方法**|**說明**|  
|----------------|---------------------|  
|public void 關閉 （TimeSpan 逾時）|關閉的連接到目標系統。 回應配接器會使用這個方法只將追蹤事件加入至追蹤接聽程式。|  
|公用 bool IsValid （TimeSpan 逾時）|傳回值，指出連接是否仍然有效。<br /><br /> 不支援回應配接器。|  
|public void 開啟 （TimeSpan 逾時）|開啟 連接到目標系統。<br /><br /> 不適用於 「 回應配接器。 不過，此範例示範您如何使用稱為 enableAuthentication URI 項目以要求使用者提供的使用者名稱。|  
|public void ClearContext()|清除連接內容。 連接重設為連接集區時，會呼叫這個方法。<br /><br /> 不支援回應配接器。|  
|public void abort （)|中止連線到目標系統。<br /><br /> 不支援回應配接器。|  
  
### <a name="echoadapterconnectionfactory"></a>EchoAdapterConnectionFactory  
 連線 factory 會負責建立連線。 根據預設，您必須在連接到目標系統時，才修改這個類別。 雖然回應配接器不含任何目標系統，它會顯示您如何使用自訂的 URI 項目，如果您的連線要求使用者驗證呼叫 enableAuthentication。  
  
> [!NOTE]
>  EnableAuthentication 不能是關鍵字，只是變數的名稱。 因此，您可以選擇任何名稱。  
  
### <a name="echoadapterconnectionuri"></a>EchoAdapterConnectionUri  
 這表示目標系統的連接字串。  
  
|**方法**|**說明**|  
|----------------|---------------------|  
|Uri 的 Uri 的公用覆寫|取得和設定的 Uri。 若要建置 Uri 字串取得及設定剖析 Uri 的字串。|  
|公用 EchoAdapterConnectionUri()|初始化 ConnectionUri 類別的新執行個體。|  
|公用覆寫字串 SampleUriString|傳回 EchoAdapter.SCHEME +": //{hostname}/{application}?enableAuthentication={True &#124;False}"。<br /><br /> 這個傳回的字串會顯示為**範例**中[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]工具，如下圖所示。|  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/e4b9d0b8-f07f-4342-815f-9ef1507b0980.gif "e4b9d0b8-f07f-4342-815f-9ef1507b0980")  
  
## <a name="echo-adapter-connection-uri"></a>回應配接器的連線 URI  
 範例回應配接器連線 URI 如下： EchoAapter.SCHEME://{hostname}/{application}?enableAuthentication={true &#124; false}  
  
 由於 EchoAapter.SCHEME echov2，連線 URI 是：  
  
 echo2: / lobhostname/lobapplication？ enableAuthentication = {true &#124; false}  
  
 您可以讀取先前的連線 URI 時 enableAuthentication = false，如下所示：  
  
 使用 echov2 傳輸結構描述，請移至名為 lobhostname，電腦名為不需要任何驗證的 lobapplication 的應用程式正在等待您的連線。  
  
 或者，當 enableAuthentication = true 時，讀取連接，如下所示：  
  
 使用 echov2 傳輸結構描述，請移至名為 lobhostname，電腦名為 lobapplication 的應用程式預期驗證正在等候您的連線。 回應配接器，使用者則只需要名稱。  
  
 具有已定義的 URI，可以透過程式設計方式取用及剖析進行連接，並設定。 如果連接需要使用者名稱和密碼等機密資料，並包含在 URI 中的這類資訊。 相反地，將在這類資訊`System.ServiceModel.Description.ClientCredentials`物件。 您加入的程式碼範例會示範如何執行這項操作。  
  
 下列程式碼，回應配接器會建構兩種方式可以顯示配接器可以如何使用各種 URI 項目修改配接器功能中的 URI。  
  
 echo2: / lobhostname/lobapplication？ enableAuthentication = [true &#124; false]  
  
 echo2: / lobhostname/lobapplication？ enableAuthentication = [true &#124; false] （& s) echoInUpperCase = true  
  
### <a name="retrieving-the-uri-element"></a>擷取 URI 項目  
 您可以剖析 URI 中的各個項目的回應配接器 URI echo2: / lobhostname/lobapplication？ enableAuthentication = false & echoInUpperCase = false。  下表中列出的 URI 項目值和相關聯的方法：  
  
|**URI 的項目值**|**方法**|  
|---------------------------|----------------|  
|lobhostname|`System.Uri.Host%2A`若要擷取的主機名稱|  
|Lobapplication|`System.Uri.AbsolutePath%2A`若要擷取的目標應用程式名稱|  
|enableAuthentation = false|GetQueryStringValue("enableAuthentication")<br /><br /> 使用此 URI 的項目，來驗證使用者認證**附註：** GetQueryStringValue 是中定義的靜態方法`Microsoft.ServiceModel.Channels.Common.ConnectionUri`|  
|echoInUpperValue = false|GetQueryStringValue("echoInUpperValue")<br /><br /> 您可以使用此 URI 項目，將傳入的字串轉換為大寫。|  
  
### <a name="enableauthentication-uri-element"></a>EnableAuthentication URI 項目  
 目標系統通常會要求您提供用戶端認證以連接到目標系統。 如前所述，回應配接器不包括任何目標系統。 雖然作為範例，它會示範如何使用自訂的 URI 項目，稱為 enableAuthentication 提供的認證。  
  
```  
 public class EchoAdapterConnection : IConnection   
{  
….  
   public void Open(TimeSpan timeout)  
  {  
    // only validate the credentials if EnableAuthentication  
    // connection property value is true  
    if (this.ConnectionFactory.ConnectionUri.EnableAuthentication)  
    {  
        // this adapter expects a value in username  
        if (this.connectionFactory.ClientCredentials != null &&  
            string.IsNullOrEmpty(this.connectionFactory.ClientCredentials.UserName.UserName))  
        {  
            throw new CredentialsException("Username is expected.");  
        }  
  }  
}  
```  
  
 程式碼會檢查以查看 enableAuthentication 為 true，如果未提供使用者名稱。如果未提供使用者名稱，就會擲回的例外狀況，它會攔截[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]工具，如下所示：  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/901095c7-c70d-491a-a1ae-8f37f22a61a7.gif "901095c7-c70d-491a-a1ae-8f37f22a61a7")  
  
 若要提供使用者名稱，也可以輸入在設定配接器 對話方塊中[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]工具，如下圖所示：  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/e4069a7d-1403-4195-b0b5-21ad97dbc3ce.gif "e4069a7d-1403-4195-b0b5-21ad97dbc3ce")  
  
### <a name="echoinuppercase-uri-element"></a>EchoInUpperCase URI 項目  
 布林旗標，例如，您可以參考 EchoInUpperCase URI 項目。 如果旗標為 true，配接器會轉換 EchoStrings 作業的輸入的字串為大寫。  
  
 若要變更預設值的 echoInUpperCase URI 項目，使用 [URI 屬性] 索引標籤中設定的介面卡[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，如下所示。  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/f22511b2-3fca-4875-ac65-8e61f4367e94.gif "f22511b2-3fca-4875-ac65-8e61f4367e94")  
  
## <a name="updating-echoadapterconnection"></a>更新 EchoAdapterConnection  
 您實作 IsValid、 開啟和關閉 EchoAdapterConnection 類別的方法。  
  
#### <a name="to-update-the-echoadapterconnection-class"></a>若要更新 EchoAdapterConnection 類別  
  
1.  在**方案總管 中**，連按兩下**EchoAdapterConnection.cs**檔案。  
  
2.  在 Visual Studio 編輯器中，以滑鼠右鍵按一下任何位置內編輯器] 的內容功能表，指向**大綱**，然後按一下 [**取消大綱**。  
  
3.  在 Visual Studio 編輯器中，尋找**IsValid**方法。 內部**IsValid**方法，取代現有的實作如下：  
  
    ```csharp  
    return true;  
    ```  
  
4.  在 Visual Studio 編輯器中，尋找**開啟**方法。 內部**開啟**方法，以下列實作取代現有的實作。 這會顯示您如何使用 URI enableAuthentication 項目，以確保在提供使用者名稱：  
  
    ```csharp  
    // only validate the credentials if EnableAuthentication  
    // connection property value is true  
    if (this.ConnectionFactory.ConnectionUri.EnableAuthentication)  
    {  
        // this adapter expects a value in username  
        // it just logs the credentials in the trace file  
        if (this.connectionFactory.ClientCredentials != null &&  
            string.IsNullOrEmpty(this.connectionFactory.ClientCredentials.UserName.UserName))  
        {  
            throw new CredentialsException("Username is expected.");  
        }  
        // got the username, log it in trace file  
        EchoAdapterUtilities.Trace.Trace(System.Diagnostics.TraceEventType.Information, "EchoAdapterConnection::Open", "Username is " + this.connectionFactory.ClientCredentials.UserName.UserName);  
    }  
    EchoAdapterUtilities.Trace.Trace(System.Diagnostics.TraceEventType.Information, "EchoAdapterConnection::Open", "Connection successfully established!");  
    ```  
  
5.  在 Visual Studio 編輯器中，尋找**關閉**方法。 內部**關閉**方法，加入下列單一陳述式：  
  
    ```csharp  
    EchoAdapterUtilities.Trace.Trace(System.Diagnostics.TraceEventType.Information, "EchoAdapterConnection::Close", "Connection successfully closed!");  
    ```  
  
## <a name="updating-the-echoadapterconnectionfactory"></a>更新 EchoAdapterConnectionFactory  
 您實作 EchoAdapterConnectionFactory 建構函式，並加入稱為 ClientCredentials 和 ConnectionUri 的兩個屬性。  
  
#### <a name="to-update-the-echoadapterconnectionfactory-class"></a>若要更新 EchoAdapterConnectionFactory 類別  
  
1.  在**方案總管 中**，連按兩下**EchoAdapterConnectionFactory.cs**檔案。  
  
2.  在 Visual Studio 編輯器中，以滑鼠右鍵按一下任何位置內編輯器] 的內容功能表，指向**大綱**，然後按一下 [**取消大綱**。  
  
3.  在 Visual Studio 編輯器中，尋找**私用欄位**區域。 加入下列單一陳述式：  
  
    ```csharp  
    private EchoAdapterConnectionUri connectionUri;  
    ```  
  
     您的私用欄位的清單應該符合下列各項：  
  
    ```csharp  
    // Stores the client credentials  
    private ClientCredentials clientCredentials;  
    // Stores the adapter class  
    private EchoAdapter adapter;  
    private EchoAdapterConnectionUri connectionUri;  
    ```  
  
4.  在 Visual Studio 編輯器中，尋找**EchoAdapterConnectionFactory**方法。 內部**EchoAdapterConnectionFactory**建構函式方法之前"}"，做為最後一個陳述式加入下列單一陳述式。  
  
    ```csharp  
    this.connectionUri = connectionUri as EchoAdapterConnectionUri;  
    ```  
  
     實作**EchoAdapterConnectionFactory**方法應符合下列：  
  
    ```csharp  
    /// <summary>  
    /// Initializes a new instance of the EchoAdapterConnectionFactory class  
    /// </summary>  
    public EchoAdapterConnectionFactory(ConnectionUri connectionUri  
        , ClientCredentials clientCredentials  
        , EchoAdapter adapter)  
    {  
        this.clientCredentials = clientCredentials;  
        this.adapter = adapter;  
        //added  
        this.connectionUri = connectionUri as EchoAdapterConnectionUri;  
    }  
    ```  
  
5.  在 Visual Studio 編輯器中，尋找**公用屬性**區域。 加入下列程式碼：  
  
    ```csharp  
    /// <summary>  
    /// Returns the client credentials  
    /// </summary>  
    public ClientCredentials ClientCredentials  
    {  
        get  
        {  
            return this.clientCredentials;  
        }  
    }  
  
    /// <summary>  
    /// Returns the Connection Uri for this adapter  
    /// </summary>  
    public EchoAdapterConnectionUri ConnectionUri  
    {  
        get  
        {  
            return this.connectionUri;  
        }  
    }  
    ```  
  
## <a name="updating-the-echoadapterconnectionuri"></a>更新 EchoAdapterConnectionUri  
 實作 EchoAdapterConnectionUri 預設建構函式、 EchoAdapterConnectionUri(Uri uri) 多載建構函式，而且公用覆寫 Uri Uri 屬性。  
  
#### <a name="to-update-the-echoadapterconnectionuri-class"></a>若要更新 EchoAdapterConnectionUri 類別  
  
1.  在**方案總管 中**，連按兩下**EchoAdapterConnectionUri.cs**檔案。  
  
2.  在 Visual Studio 編輯器中，以滑鼠右鍵按一下任何位置內編輯器] 的內容功能表，指向**大綱**，然後按一下 [**取消大綱**。  
  
3.  在 Visual Studio 編輯器中，尋找**建構函式**區域。 內部**EchoAdapterConnectionUri()**預設建構函式中，加入下列陳述式：  
  
    ```csharp  
    Uri = new Uri("echov2://lobhostname/lobapplication?enableauthentication=False");  
    ```  
  
4.  在 Visual Studio 編輯器中，內部**EchoAdapterConnectionUri (Uri uri)**多載建構函式，並加入下列陳述式：  
  
    ```csharp  
    Uri = uri;  
    ```  
  
     EchoAdapterConnectionUri(Uri uri) 方法的實作應該符合下列各項：  
  
    ```csharp  
    public EchoAdapterConnectionUri(Uri uri)  
        : base()  
    {  
        Uri = uri;  
    }  
    ```  
  
5.  在 Visual Studio 編輯器中，內部**公用覆寫 Uri Uri**方法，取代現有的使用下列邏輯。 取得建置 echoInUpperCase 不論它的 Uri。 將剖析的 URI 來擷取主機名稱、 資料庫名稱和查詢值。  
  
    ```csharp  
    get  
    {  
        // Build the uri  
        if (String.IsNullOrEmpty(this.hostname)) throw new InvalidUriException("Invalid target system host name.");  
        if (String.IsNullOrEmpty(this.application)) throw new InvalidUriException("Invalid target system data source name.");  
        if (EchoInUpperCase)  
        {  
            // build the uri with echoInUpperCase= query string  
            return new Uri(EchoAdapter.SCHEME + "://" + Hostname + "/" + Application + "?" + "enableAuthentication=" + EnableAuthentication + "&" + "echoInUpperCase=" + echoInUpperCase);  
        }  
        else  
        {  
            // build the uri without echoInUpperCase= query string  
            return new Uri(EchoAdapter.SCHEME + "://" + Hostname + "/" + Application + "?" + "enableAuthentication=" + EnableAuthentication);  
        }  
    }  
    set  
    {  
        // Parse the uri  
        String[] enableAuthValue = GetQueryStringValue(value, "enableAuthentication");  
        if (enableAuthValue.Length > 0) this.enableAuthentication = Boolean.Parse(enableAuthValue[0]);  
        String[] echoInUpperValue = GetQueryStringValue(value, "echoInUpperCase");  
        if (echoInUpperValue.Length > 0) this.echoInUpperCase = Boolean.Parse(echoInUpperValue[0]);  
  
        this.hostname = value.Host;  
        String[] applicationValue = value.AbsolutePath.Split('/');  
        if (applicationValue.Length > 1) this.Application = applicationValue[1];  
    }  
    ```  
  
6.  在 Visual Studio 中，在**檔案**功能表上，按一下 **全部儲存**。  
  
7.  按一下 [ **建置** ] 功能表上的 [ **建置方案**]。 您應該成功編譯專案。 如果沒有，請確定您已依照上述每個步驟。  
  
> [!NOTE]
>  您應該已經儲存您的工作結果。 您可以安全地關閉目前的 Visual Studio 或移至下一個步驟中，[步驟 4： 實作回應配接器中繼資料瀏覽的處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md)。  
  
## <a name="what-did-i-just-do"></a>我剛剛做什麼？  
 您實作回應配接器的連接。 您已了解連接元件的[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]、 連線 URI 的基本結構、 如何以程式設計方式剖析 URI 的項目，以及如何使用 URI 項目來變更介面卡功能。  
  
## <a name="next-steps"></a>後續步驟  
 您可以實作中繼資料瀏覽、 搜尋和解析功能，以及輸出的訊息交換。 最後，您會建置並部署配接器。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 4： 回應配接器實作中繼資料瀏覽的處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md)   
 [教學課程 1： 在開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)