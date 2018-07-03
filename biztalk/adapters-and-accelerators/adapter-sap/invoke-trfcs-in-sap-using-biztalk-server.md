---
title: 叫用中使用 BizTalk Server 的 SAP 的 Trfc |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tRFCs, invoking using BizTalk Server
ms.assetid: 9489adca-cf2c-4e15-8573-445acd7ebf73
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: baebf2a3f1723265612974f4728797bca7a070a9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989746"
---
# <a name="invoke-trfcs-in-sap-using-biztalk-server"></a>叫用 Trfc SAP 使用 BizTalk Server 中
交易式遠端函式呼叫 (Trfc) 會保證只有一個執行的時間上的 SAP 系統的 RFC。 您可以叫用任何呈現的 Rfc[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]為 tRFC。 叫用 tRFC 大致叫用 RFC (請參閱[叫用 Rfc，SAP 使用 BizTalk server 中](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-biztalk-server.md)) 具有下列差異：  
  
- [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現不同的節點下的 Trfc (**TRFC**) 比 Rfc (**RFC**)。  
  
- tRFC 作業包含對應至由 tRFC SAP 交易識別碼的 GUID 參數[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
- 叫用 tRFC 之後，您必須叫用確認 （認可） 上的 SAP 系統 tRFC RfcConfirmTransID 作業。 這項作業會顯示正下方**TRFC**中的節點[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
  如需有關如何[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援叫用 tRFC，請參閱[對 sap 的 Trfc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md)。 叫用 tRFC，訊息的 SOAP 結構的詳細資訊，請參閱[tRFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-trfc-operations.md)。  
  
## <a name="how-to-invoke-a-trfc-in-an-sap-system-using-biztalk-server"></a>如何叫用 tRFC SAP 系統使用 BizTalk Server 中？  
 執行 SAP 系統使用運算[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[建立 SAP 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)。 要叫用 tRFC，SAP 系統中，這些工作如下：  
  
1. 建立 BizTalk 專案，並產生您想要在 SAP 系統中叫用 tRFC 的結構描述。 您也必須產生結構描述**RfcConfirmTransID**認可 TID SAP 系統中的作業。  
  
2. 建立傳送和接收訊息，從 SAP 系統的 BizTalk 專案中的訊息。  
  
3. 建立 SAP 系統中叫用 tRFC 和然後認可 TID tRFC 呼叫回應中的 SAP 系統中建立協調流程[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
4. 建置和部署 BizTalk 專案。  
  
5. 設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
6. 啟動 BizTalk 應用程式。  
  
   本主題提供執行這些工作的指示。  
  
## <a name="sample-based-on-this-topic"></a>根據本主題的範例  
 ，tRFCClient，根據本主題也提供了範例[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 範例從 SAP 配接器](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md)。  
  
## <a name="generating-schema"></a>產生結構描述  
 本主題中，示範如何叫用 tRFC 使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，我們將產生的結構描述：  
  
- *BAPI_SALESORDER_CREATEFROMDAT2* tRFC。  
  
- RfcConfirmTransID 作業。 您必須使用這項作業，認可會在 SAP 系統中建立的 TID。 SAP 系統收到此呼叫之後它會從系統刪除 TID。  
  
  請參閱[瀏覽、 搜尋及取得 tRFC 作業在 SAP 中的中繼資料](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-trfc-operations-in-sap.md)如需有關如何產生結構描述。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您稍早產生的結構描述會描述協調流程中的訊息所需的 「 類型 」。 訊息通常是一個變數，要為其類型會定義對應的結構。 您必須連結您所產生的結構描述訊息，從 BizTalk 專案的協調流程檢視。  
  
 本主題中，您必須建立四個訊息，設定才能叫用 tRFC 和另一個要求-回應訊息的要求-回應訊息設定為叫用 RfcConfirmTransID 作業。  
  
 執行下列步驟來建立訊息，並將它們連結至結構描述。  
  
#### <a name="to-create-messages-and-link-to-schema"></a>若要建立訊息，並連結至結構描述  
  
1.  開啟協調流程檢視 BizTalk 專案中，如果未開啟。 按一下 **檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。  
  
2.  在 **協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。  
  
3.  以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。  
  
4.  在 [**屬性**] 窗格**Message_1**，執行下列動作。  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|型別**要求**。|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取 訊息類型。 例如，選取*tRFC_Client.SAPBindingSchema1.BAPI_SALESORDER_CREATEFROMDAT2*，其中*tRFC_Client*是 BizTalk 專案的名稱。 *SAPBindingSchema1*是針對產生的結構描述*BAPI_SALESORDER_CREATEFROMDAT2*。|  
  
5.  重複上述步驟來建立三個的多個訊息。 在 **屬性**窗格中新的訊息，執行下列動作。  
  
    |若要設定識別項|若要設定訊息類型|  
    |-----------------------|-------------------------|  
    |回應|*tRFC_Client.SAPBindingSchema1.BAPI_SALESORDER_CREATEFROMDAT2Response*|  
    |TIDRequest|*tRFC_Client.SAPBindingSchema3.RfcConfirmTransID*|  
    |TIDResponse|*tRFC_Client.SAPBindingSchema3.RfcConfirmTransIDResponse*|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]叫用 Trfc，SAP 系統中。 在此協調流程中，您將會卸除在要求訊息定義的接收位置。 協調流程會取用這個訊息，並將它傳遞到 SAP 系統。 從 SAP 接收的回應，且會儲存在另一個位置。 回應訊息包含的 GUID。 協調流程包含**建構的訊息**圖形以從回應中擷取 GUID，並建構訊息的結構描述符合**RfcConfirmTransID**作業。 要叫用的訊息**RfcConfirmTransID**作業傳送至 SAP 系統具有 GUID 為參數 _ 典型的協調流程叫用 Trfc，在 SAP 系統中，後面接著**RfcConfirmTransID**作業會包含：  
  
- 傳送和接收圖形以將訊息傳送至 SAP 系統，並接收回應。  
  
- 「 建構訊息 」 圖形內的 「 訊息指派圖形來建構的訊息並**RfcConfirmTransID**作業。  
  
- 單向接收埠以接收要求訊息傳送至 SAP 系統，來叫用 tRFC。  
  
- 雙向傳送埠以傳送訊息，以叫用 tRFC 並接收回應。  
  
- 雙向傳送埠以傳送訊息來叫用**RfcConfirmTransID**作業並接收回應。  
  
- 兩個單向傳送埠從 SAP 系統的回應傳送到資料夾。  
  
  範例協調流程如下所示：  
  
  ![進行 tRFC 用戶端呼叫的協調流程](../../adapters-and-accelerators/adapter-sap/media/369d62dd-9ae4-4673-b346-03d2acfb453a.gif "369d62dd-9ae4-4673-b346-03d2acfb453a")  
  
### <a name="adding-message-shapes"></a>新增訊息圖形  
 針對每個訊息 圖形中指定下列屬性。 所列的名稱*圖形*資料行是訊息 圖形的名稱，上述協調流程中所示。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveXml|Receive|-設定**名稱**到*ReceiveXml*<br />-設定**啟用**到 *，則為 True*|  
|SendToLOB|Send|-設定**名稱**到*SendToLOB*|  
|ReceiveResponse|Receive|-設定**名稱**到*ReceiveResponse*<br />-設定**啟用**到*False*|  
|SendResponse|Send|-設定**名稱**到*SendResponse*|  
|SendTIDMsg|Send|-設定**名稱**到*SendTIDMsg*|  
|ReceiveTIDRsp|Receive|-設定**名稱**到*ReceiveTIDRsp*<br />-設定**啟用**到*False*|  
|SendTIDRsp|Send|-設定**名稱**到*SendTIDRsp*|  
  
### <a name="adding-the-construct-message-shape"></a>新增 建構訊息圖形  
 TRFC 呼叫之 SAP 系統的回應包含的 GUID。 若要認可的 tRFC 呼叫，您必須傳遞相同的 GUID RfcConfirmTransID 作業。 若要這樣做，您必須包含 「 建構訊息 」 圖形中，並在其中 「 訊息指派圖形，協調流程中。 在這裡，「 建構訊息 」 圖形的目的是：  
  
- 若要擷取 tRFC 呼叫之 SAP 系統從收到的回應中的 GUID。  
  
- 若要建構的訊息符合 RfcConfirmTransID 作業的訊息結構描述。  
  
  針對 [建構訊息] 圖形中，您必須設定**建構的訊息**屬性設**TIDRequest**。  
  
  您必須在訊息指派 」 圖形中新增下列程式碼的摘錄：  
  
```  
XmlDoc = new System.Xml.XmlDocument();  
XmlDoc.LoadXml("<RfcConfirmTransID xmlns='http://Microsoft.LobServices.Sap/2007/03/RfcApi/'><TransactionalRfcOperationIdentifier /></RfcConfirmTransID>");  
TIDRequest = XmlDoc;  
TIDRequest.TransactionalRfcOperationIdentifier = xpath(Response,"string(/*[local-name()='BAPI_SALESORDER_CREATEFROMDAT2Response']/*[local-name()='TransactionalRfcOperationIdentifier']/text())");  
```  
  
 若要使用上述程式碼的摘錄，您必須具備：  
  
-   建立變數， **XmlDoc**，在您的 BizTalk 專案，然後將其類型設為 System.Xml.XmlDocument。 如需建立變數的詳細資訊，請參閱 <<c0> [ 在協調流程中使用變數](../../core/using-variables-in-orchestrations.md)。
  
-   升階**TransactionalRfcOperationIdentifier** RfcConfirmTransID 作業的結構描述中的屬性。 如需有關如何升級屬性的詳細資訊，請參閱 <<c0> [ 升級屬性](../../core/promoting-properties.md)。
  
### <a name="adding-ports"></a>新增連接埠  
 請確定您針對每個邏輯連接埠中指定下列屬性。 所列的名稱*連接埠*資料行名稱就是連接埠在協調流程中所示。  
  
|通訊埠|屬性|  
|----------|----------------|  
|FileIn|-設定**識別碼**到*FileIn*<br />-設定**型別**到*FileInPortType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*接收*|  
|tRFC_Port|-設定**識別碼**到*tRFC_Port*<br />-設定**型別**到*tRFC_PortType*<br />-設定**通訊模式**到*要求-回應*<br />-設定**通訊方向**到*傳送接收*|  
|SavetRFCResponse|-設定**識別碼**到*SavetRFCResponse*<br />-設定**型別**到*SavetRFCResponsePortType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*傳送*|  
|TID_Port|-設定**識別碼**到*TID_Port*<br />-設定**型別**到*TIDPortType*<br />-設定**通訊模式**到*要求-回應*<br />-設定**通訊方向**到*傳送接收*|  
|SaveTIDResponse|-設定**識別碼**到*SaveTIDResponse*<br />-設定**型別**到*SaveTIDResponsePortType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*傳送*|  
  
## <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>為動作圖形指定訊息，並連接到連接埠  
 下表指定之屬性和其值設為指定的動作圖形，並將它們連結至連接埠的訊息。 所列的名稱*圖形*資料行名稱就是訊息 圖形上的協調流程中所示。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveXml|-設定**訊息**到*要求*<br />-設定**作業**到*FileIn.tRFC.Request*|  
|SendToLOB|-設定**訊息**到*要求*<br />-設定**作業**到*tRFC_Port.tRFC.Request*|  
|ReceiveResponse|-設定**訊息**到*回應*<br />-設定**作業**到*tRFC_Port.tRFC.Response*|  
|SendResponse|-設定**訊息**到*回應*<br />-設定**作業**到*SavetRFCResponse.tRFC.Request*|  
|SendTIDMsg|-設定**訊息**到*TIDRequest*<br />-設定**作業**到*TID_Port.TID.Request*|  
|ReceiveTIDRsp|-設定**訊息**到*TIDResponse*<br />-設定**作業**到*TID_Port.TID.Response*|  
|SendTIDRsp|-設定**訊息**到*TIDResponse*<br />-設定**作業**到*SaveTIDResponse.TID.Request*|  
  
 您指定這些屬性之後，連線的訊息 圖形和連接埠和協調流程已完成。  
  
 您必須立即建置 BizTalk 方案，並再將它部署到 BizTalk Server。 如需詳細資訊，請參閱 <<c0> [ 建置和執行協調流程](../../core/building-and-running-orchestrations.md)。  
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在下**協調流程**在 BizTalk Server 管理主控台 窗格。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 如需有關如何設定應用程式的詳細資訊，請參閱 <<c0> [ 如何設定應用程式](../../core/how-to-configure-an-application.md)。
  
 設定應用程式包含：  
  
- 選取應用程式主機。  
  
- 對應您在您在 BizTalk Server 管理主控台中的實體連接埠的協調流程中建立的連接埠。 此協調流程中，您必須：  
  
  - 定義位置上的硬碟和對應的檔案連接埠，您將會卸除要求訊息。 BizTalk 協調流程將會取用要傳送至 SAP 系統的要求訊息。  
  
  - 定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含來自 SAP 系統的回應的回應訊息。  
  
  - 定義實體的 Wcf-custom 或 WCF SAP 傳送埠 （各一個 tRFC 要求訊息和 RfcConfirmTransID 訊息） 將訊息傳送至 SAP 系統。 您也必須在傳送埠中指定的動作。 如需有關如何建立連接埠的資訊，請參閱 <<c0> [ 手動設定 SAP 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md)。
  
    > [!NOTE]
    >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠設定動作的相關資訊的繫結檔案。 您可以從 BizTalk Server 管理主控台，來建立 （適用於輸出的呼叫） 的傳送埠或接收埠 （適用於輸入的呼叫），以匯入此繫結檔案。 如需詳細資訊，請參閱 <<c0> [ 設定的實體連接埠繫結使用的連接埠繫結檔案至 SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md)。
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 BizTalk 應用程式，來叫用 Trfc，SAP 系統中。 如需有關啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)，或[如何啟動應用程式](../../core/how-to-start-and-stop-a-biztalk-application.md)。  
  
 在這個階段，請確定：  
  
-   FILE 接收埠以接收要求訊息的協調流程正在執行。  
  
-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  
  
-   WCF 自訂 」 或 「 WCF SAP 傳送埠將訊息傳送至 SAP 系統正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，您必須先卸除的協調流程的要求訊息。 請參閱[tRFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-trfc-operations.md)須知叫用 tRFC，SAP 系統中的要求訊息的結構描述。 例如，要叫用 tRFC 為 BAPI_SALEASORDER_CREATEFROMDAT2 的要求訊息是：  
  
```  
<BAPI_SALESORDER_CREATEFROMDAT2 xmlns="http://Microsoft.LobServices.Sap/2007/03/Trfc/">  
  <ORDER_HEADER_IN>  
    <DOC_TYPE xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">TA</DOC_TYPE>  
    <SALES_ORG xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">1000</SALES_ORG>  
    <DISTR_CHAN xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">10</DISTR_CHAN>  
    <DIVISION xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">00</DIVISION>  
    <SALES_OFF xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">1000</SALES_OFF>  
    <REQ_DATE_H xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">2006-09-01T23:50:00</REQ_DATE_H>  
    <PURCH_DATE xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">2006-08-25T23:50:00</PURCH_DATE>  
    <PURCH_NO_C xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">Cust PO</PURCH_NO_C>  
    <CURRENCY xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">EUR</CURRENCY>  
  </ORDER_HEADER_IN>  
  <ORDER_ITEMS_IN>  
    <BAPISDITM xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
      <MATERIAL>P-109</MATERIAL>  
      <PLANT>1000</PLANT>  
      <TARGET_QU>ST</TARGET_QU>  
    </BAPISDITM>  
  </ORDER_ITEMS_IN>  
  <ORDER_PARTNERS>  
    <BAPIPARNR xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
      <PARTN_ROLE>AG</PARTN_ROLE>  
      <PARTN_NUMB>0000001390</PARTN_NUMB>  
    </BAPIPARNR>  
  </ORDER_PARTNERS>  
  <RETURN/>  
  <TransactionalRfcOperationIdentifier>def689b1-b514-4627-a861-d6d7f51c84e3</TransactionalRfcOperationIdentifier>  
</BAPI_SALESORDER_CREATEFROMDAT2>  
```  
  
 協調流程會取用訊息、 將它傳遞到 SAP 系統，並接收來自 SAP 系統的回應。 回應訊息會儲存在其他協調流程中指定的檔案位置。 SAP 系統的回應包含的 GUID。 然後協調流程會產生另一個要求訊息從回應，並將它傳遞至 SAP 系統，以執行 RfcConfirmTransID。 從 SAP 系統 RfcConfirmTransID 作業收到回應後，會將它複製到檔案位置。 總結來說，此作業已成功執行之後：  
  
-   來自 SAP 的回應訊息，來叫用 tRFC 會複製到檔案位置。 這包含已傳送至 SAP 系統的 GUID 相同。 因為 tRFC 叫用 BAPI_SALESORDER_CREATEFROMDAT2 回應訊息：  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <BAPI_SALESORDER_CREATEFROMDAT2Response xmlns="http://Microsoft.LobServices.Sap/2007/03/Trfc/">  
      <TransactionalRfcOperationIdentifier>def689b1-b514-4627-a861-d6d7f51c84e3</TransactionalRfcOperationIdentifier>  
    </BAPI_SALESORDER_CREATEFROMDAT2Response>  
    ```  
  
-   RfcConfirmTransID 的回應訊息會複製到相同的位置。 這是空的回應。 RfcConfirmTransID 的回應訊息是：  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <RfcConfirmTransIDResponse xmlns="http://Microsoft.LobServices.Sap/2007/03/RfcApi/"></RfcConfirmTransIDResponse>  
    ```  
  
> [!NOTE]
>  您可以使用**ConvertGuidToTid()** SAP 配接器組件，擷取對應至 GUID 的 SAP 系統中的 TID 所公開的公用方法。 如需詳細資訊，請參閱 <<c0> [ 特殊作業](../../adapters-and-accelerators/adapter-sap/special-operations.md)。  
  
## <a name="possible-exceptions"></a>可能的例外狀況  
 如需叫用 tRFC，在 SAP 系統中使用 BizTalk Server 時可能會遇到的例外狀況資訊，請參閱[例外狀況和錯誤處理與 SAP 配接器](../../adapters-and-accelerators/adapter-sap/exceptions-and-error-handling-with-the-sap-adapter.md)。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。 之後產生的繫結檔案時，您可以匯入的組態設定從檔案，讓您不需要建立傳送埠、 接收連接埠、 相同的協調流程等。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用 SAP 配接器繫結](../../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md)。
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)