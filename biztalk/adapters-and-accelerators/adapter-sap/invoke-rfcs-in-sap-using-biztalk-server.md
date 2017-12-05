---
title: "叫用中使用 BizTalk Server 的 SAP Rfc |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: RFCs, invoking using BizTalk Server
ms.assetid: cc859ca2-aa9a-48fd-a941-ae28bee96f06
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3db5180d8b4183a2a48c726fd5e73b3347f82dc
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="invoke-rfcs-in-sap-using-biztalk-server"></a>叫用中使用 BizTalk Server 的 SAP Rfc
[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]介面上做為配接器用戶端可以叫用的作業由 SAP 系統的 Rfc。 此章節提供的指示以 SAP 系統的 RFC 叫用使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]與 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需有關如何[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援叫用 RFC SAP 系統，請參閱[作業中 SAP Rfc](../../adapters-and-accelerators/adapter-sap/operations-on-rfcs-in-sap.md)。 更多的叫用 RFC 的 SOAP 訊息結構的詳細資訊，請參閱[RFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)。  
  
## <a name="how-to-invoke-an-rfc-in-an-sap-system"></a>叫用 SAP 系統中的 RFC 如何？  
 執行 SAP 系統使用的作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[建立的 SAP 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)。 要叫用 RFC，SAP 系統中，這些工作包括：  
  
1.  建立 BizTalk 專案，並產生您想要叫用 SAP 系統中的 RFC 的結構描述。  
  
2.  建立傳送和從 SAP 系統接收訊息的 BizTalk 專案中的訊息。  
  
3.  建立協調流程叫用 RFC，SAP 系統中。  
  
4.  建置和部署 BizTalk 專案。  
  
5.  設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
6.  啟動 BizTalk 應用程式。  
  
 本主題提供執行這些工作的指示。  
  
## <a name="generating-schema"></a>產生結構描述  
 本主題中，以示範如何在 SAP 系統中，叫用 RFC 我們產生的結構描述*RFC_CUSTOMER_GET*。 請參閱[瀏覽、 搜尋和取得中繼資料中 SAP RFC 作業的](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md)如需有關如何產生結構描述。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您先前產生的結構描述會描述 「 類型 」 所需的協調流程中的訊息。 訊息通常是為其型別由對應的結構描述所定義的變數。 您必須連結到訊息的您所產生的結構描述之協調流程檢視中的 BizTalk 專案。  
  
 本主題中，您必須建立兩個訊息，其中將要求傳送至 SAP 系統，而另一個則接收回應。  
  
 執行下列步驟來建立訊息，並將其連結至結構描述。  
  
#### <a name="to-create-messages-and-link-to-schema"></a>建立訊息，以及連結至結構描述  
  
1.  開啟協調流程檢視 BizTalk 專案中，如果未開啟。 按一下**檢視**，指向 **其他視窗**，然後按一下**協調流程檢視**。  
  
2.  在**協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。  
  
3.  以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。  
  
4.  在**屬性**窗格**Message_1**，執行下列動作。  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|型別**要求**。|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*InvokeRFC.SAPBindingSchema.RFC_CUSTOMER_GET*，其中*InvokeRFC*是您的 BizTalk 專案的名稱。  *SAPBindingSchema*是針對產生的結構描述*RFC_CUSTOMER_GET*。|  
  
5.  重複上述步驟，建立新的訊息。 在**屬性**窗格新訊息中，執行下列動作。  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|型別**回應**。|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*InvokeRFC.SAPBindingSchema.RFC_CUSTOMER_GETResponse*。|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]叫用 Rfc，SAP 系統中。 在此協調流程中，卸除要求訊息已定義的接收位置。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]取用訊息，並將它傳遞至 SAP 系統。 從 SAP 系統的回應會儲存到另一個位置。 典型的協調流程叫用的 rfc，SAP 系統中會包含：  
  
-   傳送和接收圖形以將訊息傳送至 SAP 系統，並接收回應。  
  
-   單向接收埠以接收要求訊息傳送到 SAP 系統。  
  
-   雙向傳送埠以將要求訊息傳送至 SAP 系統，並接收回應。  
  
-   單向傳送埠，以便從 SAP 系統的回應傳送到資料夾。  
  
 範例協調流程如下所示：  
  
 ![具有連接的連接埠的協調流程](../../adapters-and-accelerators/adapter-sap/media/c228e79f-02e8-4de3-b447-8703caa28d3b.gif "c228e79f-02e8-4de3-b447-8703caa28d3b")  
  
### <a name="adding-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息圖形指定下列屬性。 所列的名稱*圖形*資料行名稱就是訊息圖形顯示在上述的協調流程中。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|Receive_Request|Receive|-設定**名稱**至*Receive_Request*<br />-設定**啟動**至*，則為 True*|  
|Send_LOB|Send|-設定**名稱**至*Send_LOB*|  
|Receive_LOB|Receive|-設定**名稱**至*Receive_LOB*<br />-設定**啟動**至*False*|  
|Send_Response|Send|-設定**名稱**至*Send_Response*|  
  
### <a name="adding-ports"></a>新增連接埠  
 針對每個邏輯連接埠中指定下列屬性。 所列的名稱*連接埠*資料行是連接埠的名稱，顯示在 協調流程中。  
  
|通訊埠|屬性|  
|----------|----------------|  
|ReceiveMsgPort|-設定**識別碼**至*ReceiveMsgPort*<br />-設定**類型**至*ReceiveMsgPortType*<br />-設定**通訊模式**至*單向*<br />-設定**通訊方向**至*接收*|  
|SendToLOBPort|-設定**識別碼**至*SendToLOBPort*<br />-設定**類型**至*SendToLOBPortType*<br />-設定**通訊模式**至*要求-回應*<br />-設定**通訊方向**至*傳送接收*|  
|SendMsgPort|-設定**識別碼**至*SendMsgPort*<br />-設定**類型**至*SendMsgPortType*<br />-設定**通訊模式**至*單向*<br />-設定**通訊方向**至*傳送*|  
  
## <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>指定動作圖形訊息並連接至連接埠  
 下表指定屬性和其值設為指定的動作圖形，並將它們連結至連接埠的訊息。 所列的名稱*圖形*資料行名稱就是訊息圖形顯示在上述的協調流程中。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|Receive_Request|-設定**訊息**至*要求*<br />-設定**作業**至*ReceiveMsgPort.Operation_1.Request*|  
|Send_LOB|-設定**訊息**至*要求*<br />-設定**作業**至*SendToLOBPort.Operation_1.Request*|  
|Receive_LOB|-設定**訊息**至*回應*<br />-設定**作業**至*SendToLOBPort.Operation_1.Response*|  
|Send_Response|-設定**訊息**至*回應*<br />-設定**作業**至*SendMsgPort.Operation_1.Request*|  
  
 您指定這些屬性之後，連接的訊息 圖形和連接埠，而且您的協調流程已完成。  
  
 您現在必須建置 BizTalk 方案，並部署到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱[建置和執行協調流程](../../core/building-and-running-orchestrations.md)。
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 部署 BizTalk 專案之後，您稍早建立的協調流程會列在**協調流程**BizTalk Server 管理主控台 窗格。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 如需有關如何設定應用程式的詳細資訊，請參閱[如何設定應用程式](../../core/how-to-configure-an-application.md)。
  
 設定應用程式包括：  
  
-   選取應用程式的主機。  
  
-   對應至 BizTalk Server 管理主控台中的實體連接埠在協調流程中建立的連接埠。 此協調流程中，您必須：  
  
    -   定義位置上的硬碟和對應的檔案連接埠，您將在此置放要求訊息。 BizTalk 協調流程會使用要求訊息，並將它傳送至 SAP 系統。  
  
    -   定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含 SAP 系統從回應的回應訊息。  
  
    -   定義將訊息傳送至 SAP 系統實體 Wcf-custom 或 WCF SAP 傳送埠。 您也必須在傳送埠中指定的動作。 如需如何建立連接埠相關資訊，請參閱[以手動方式設定 SAP 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md)。
  
        > [!NOTE]
        >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠的設定動作的相關資訊的繫結檔案。 您可以從 BizTalk Server 管理主控台來建立 （適用於傳出呼叫） 的傳送埠或接收埠 （適用於進行傳入呼叫時），以匯入此繫結檔案。 如需詳細資訊，請參閱[設定實體連接埠繫結使用連接埠繫結檔案至 SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md)。
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動叫用 RFC，SAP 系統中的 BizTalk 應用程式。 如需啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)或[如何啟動應用程式](../../core/how-to-start-and-stop-a-biztalk-application.md)。
  
 在這個階段，請確定：  
  
-   FILE 接收埠以接收要求訊息的協調流程執行。  
  
-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  
  
-   Wcf-custom 或 WCF SAP 傳送埠將訊息傳送至 SAP 系統正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，您必須在預先定義的位置中卸除協調流程的要求訊息。 請參閱[RFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)知道 SAP 系統中叫用 RFC 的要求訊息的結構描述。 例如，要叫用 RFC_CUSTOMER_GET 的要求訊息是：  
  
```  
<RFC_CUSTOMER_GET xmlns="http://Microsoft.LobServices.Sap/2007/03/Rfc/">  
  <KUNNR>0000001390</KUNNR>  
  <NAME1>*</NAME1>  
  <CUSTOMER_T/>  
</RFC_CUSTOMER_GET>  
```  
  
 協調流程取用訊息，並將它傳送至 SAP 系統。 從 SAP 系統的回應會儲存在其他的協調流程中定義的檔案位置。 比方說，是來自上述的要求訊息的 SAP 系統的回應：  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<RFC_CUSTOMER_GETResponse xmlns="http://Microsoft.LobServices.Sap/2007/03/Rfc/">  
  <CUSTOMER_T>  
    <RFCCUST xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
      <KUNNR>0000001390</KUNNR>   
      <ANRED>Firma</ANRED>   
      <NAME1>Contoso, Ltd.</NAME1>   
      <PFACH />   
      <STRAS>4567 Main Street</STRAS>   
      <PSTLZ>98052</PSTLZ>   
      <ORT01>USA</ORT01>   
      <TELF1>555-0101</TELF1>   
      <TELFX>555-0102</TELFX>   
    </RFCCUST>  
  </CUSTOMER_T>  
</RFC_CUSTOMER_GETResponse>  
```  
  
## <a name="possible-exceptions"></a>可能的例外狀況  
 如需時叫用 RFC，SAP 系統使用 BizTalk Server 中可能會遇到的例外狀況資訊，請參閱[例外狀況和錯誤處理與 SAP 配接器](../../adapters-and-accelerators/adapter-sap/exceptions-and-error-handling-with-the-sap-adapter.md)。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。 一旦產生繫結檔案時，您可以匯入組態設定從檔案，因此您不需要建立傳送埠、 接收埠，等。 針對相同的協調流程。 如需繫結檔案的詳細資訊，請參閱[重複使用的 SAP 配接器繫結](../../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md)。  
  
## <a name="see-also"></a>請參閱  
[開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)