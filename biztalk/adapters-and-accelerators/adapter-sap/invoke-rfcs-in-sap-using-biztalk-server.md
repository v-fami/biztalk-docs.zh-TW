---
title: 叫用中使用 BizTalk Server 的 SAP Rfc |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RFCs, invoking using BizTalk Server
ms.assetid: cc859ca2-aa9a-48fd-a941-ae28bee96f06
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 381cbebae5e87e459b8283c90b4bbc0de9afb1cc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988783"
---
# <a name="invoke-rfcs-in-sap-using-biztalk-server"></a>叫用 Rfc，SAP 使用 BizTalk Server 中
[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現為配接器用戶端可以叫用的作業由 SAP 系統的 Rfc。 本節說明上使用 SAP 系統中叫用 RFC[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]與 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需有關如何[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援叫用 RFC 在 SAP 系統中，請參閱[對 sap Rfc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-rfcs-in-sap.md)。 更多的叫用 RFC 的 SOAP 訊息結構的詳細資訊，請參閱[RFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)。  
  
## <a name="how-to-invoke-an-rfc-in-an-sap-system"></a>如何叫用 RFC，SAP 系統中？  
 執行 SAP 系統使用運算[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及中所述的程序性工作[建立 SAP 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)。 要叫用 RFC，SAP 系統中，這些工作如下：  
  
1. 建立 BizTalk 專案，並產生您想要在 SAP 系統中叫用 RFC 的結構描述。  
  
2. 建立傳送和接收訊息，從 SAP 系統的 BizTalk 專案中的訊息。  
  
3. 建立協調流程叫用 RFC，SAP 系統中。  
  
4. 建置和部署 BizTalk 專案。  
  
5. 設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
6. 啟動 BizTalk 應用程式。  
  
   本主題提供執行這些工作的指示。  
  
## <a name="generating-schema"></a>產生結構描述  
 本主題中，示範如何叫用 RFC，在 SAP 系統中，我們產生的結構描述*RFC_CUSTOMER_GET*。 請參閱[瀏覽、 搜尋和取得中繼資料，在 SAP 中的 RFC 作業的](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md)如需有關如何產生結構描述。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您稍早產生的結構描述會描述協調流程中的訊息所需的 「 類型 」。 訊息通常是一個變數，要為其類型會定義對應的結構。 您必須連結您所產生的結構描述訊息，從 BizTalk 專案的協調流程檢視。  
  
 本主題中，您必須建立兩個訊息，一個用來將要求傳送至 SAP 系統，另一個用於接收的回應。  
  
 執行下列步驟來建立訊息，並將它們連結至結構描述。  
  
#### <a name="to-create-messages-and-link-to-schema"></a>若要建立訊息，並連結至結構描述  
  
1.  開啟協調流程檢視 BizTalk 專案中，如果未開啟。 按一下 **檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。  
  
2.  在 **協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。  
  
3.  以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。  
  
4.  在 [**屬性**] 窗格**Message_1**，執行下列動作。  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|型別**要求**。|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*InvokeRFC.SAPBindingSchema.RFC_CUSTOMER_GET*，其中*InvokeRFC*是 BizTalk 專案的名稱。  *SAPBindingSchema*是針對產生的結構描述*RFC_CUSTOMER_GET*。|  
  
5.  重複上述步驟來建立新的訊息。 在 **屬性**窗格中的新訊息，執行下列動作。  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|型別**回應**。|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*InvokeRFC.SAPBindingSchema.RFC_CUSTOMER_GETResponse*。|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]叫用 Rfc，SAP 系統中。 在此協調流程中，卸除在要求訊息定義的接收位置。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]取用訊息，並將它傳遞到 SAP 系統。 SAP 系統的回應會儲存到另一個位置。 典型的協調流程叫用 rfc，SAP 系統中會包含：  
  
- 傳送和接收圖形以將訊息傳送至 SAP 系統，並接收回應。  
  
- 單向接收埠以接收要求訊息傳送到 SAP 系統。  
  
- 雙向傳送埠以將要求訊息傳送到 SAP 系統，並接收回應。  
  
- 若要從 SAP 系統的回應傳送到資料夾的單向傳送埠。  
  
  範例協調流程如下所示：  
  
  ![具有連接的連接埠的協調流程](../../adapters-and-accelerators/adapter-sap/media/c228e79f-02e8-4de3-b447-8703caa28d3b.gif "c228e79f-02e8-4de3-b447-8703caa28d3b")  
  
### <a name="adding-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息 圖形中指定下列屬性。 所列的名稱*圖形*資料行是訊息 圖形的名稱，上述協調流程中所示。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|Receive_Request|Receive|-設定**名稱**到 *[receive_request]*<br />-設定**啟用**到 *，則為 True*|  
|Send_LOB|Send|-設定**名稱**到*Send_LOB*|  
|Receive_LOB|Receive|-設定**名稱**到*Receive_LOB*<br />-設定**啟用**到*False*|  
|Send_Response|Send|-設定**名稱**到*Send_Response*|  
  
### <a name="adding-ports"></a>新增連接埠  
 針對每個邏輯連接埠中指定下列屬性。 所列的名稱*連接埠*資料行名稱就是連接埠在協調流程中所示。  
  
|通訊埠|屬性|  
|----------|----------------|  
|ReceiveMsgPort|-設定**識別碼**到*ReceiveMsgPort*<br />-設定**型別**到*ReceiveMsgPortType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*接收*|  
|SendToLOBPort|-設定**識別碼**到*SendToLOBPort*<br />-設定**型別**到*SendToLOBPortType*<br />-設定**通訊模式**到*要求-回應*<br />-設定**通訊方向**到*傳送接收*|  
|SendMsgPort|-設定**識別碼**到*SendMsgPort*<br />-設定**型別**到*SendMsgPortType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*傳送*|  
  
## <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>為動作圖形指定訊息，並連接到連接埠  
 下表指定之屬性和其值設為指定的動作圖形，並將它們連結至連接埠的訊息。 所列的名稱*圖形*資料行是訊息 圖形的名稱，上述協調流程中所示。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|Receive_Request|-設定**訊息**到*要求*<br />-設定**作業**到*ReceiveMsgPort.Operation_1.Request*|  
|Send_LOB|-設定**訊息**到*要求*<br />-設定**作業**到*SendToLOBPort.Operation_1.Request*|  
|Receive_LOB|-設定**訊息**到*回應*<br />-設定**作業**到*SendToLOBPort.Operation_1.Response*|  
|Send_Response|-設定**訊息**到*回應*<br />-設定**作業**到*SendMsgPort.Operation_1.Request*|  
  
 您指定這些屬性之後，連線的訊息 圖形和連接埠和協調流程已完成。  
  
 您現在必須建置 BizTalk 方案，並將其部署至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 建置和執行協調流程](../../core/building-and-running-orchestrations.md)。
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在下**協調流程**在 BizTalk Server 管理主控台 窗格。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 如需有關如何設定應用程式的詳細資訊，請參閱 <<c0> [ 如何設定應用程式](../../core/how-to-configure-an-application.md)。
  
 設定應用程式包含：  
  
- 選取應用程式主機。  
  
- 對應您在您在 BizTalk Server 管理主控台中的實體連接埠的協調流程中建立的連接埠。 此協調流程中，您必須：  
  
  - 定義位置上的硬碟和對應的檔案連接埠，您將會卸除要求訊息。 BizTalk 協調流程將會取用的要求訊息，並將它傳送到 SAP 系統。  
  
  - 定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含來自 SAP 系統的回應的回應訊息。  
  
  - 定義實體 WCF 自訂 」 或 「 WCF SAP 傳送埠將訊息傳送至 SAP 系統。 您也必須在傳送埠中指定的動作。 如需有關如何建立連接埠的資訊，請參閱 <<c0> [ 手動設定 SAP 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md)。
  
    > [!NOTE]
    >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠設定動作的相關資訊的繫結檔案。 您可以從 BizTalk Server 管理主控台，來建立 （適用於輸出的呼叫） 的傳送埠或接收埠 （適用於輸入的呼叫），以匯入此繫結檔案。 如需詳細資訊，請參閱 <<c0> [ 設定的實體連接埠繫結使用的連接埠繫結檔案至 SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md)。
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動叫用 RFC，SAP 系統中的 BizTalk 應用程式。 如需有關啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)或是[如何啟動應用程式](../../core/how-to-start-and-stop-a-biztalk-application.md)。
  
 在這個階段，請確定：  
  
-   FILE 接收埠以接收要求訊息的協調流程正在執行。  
  
-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  
  
-   WCF 自訂 」 或 「 WCF SAP 傳送埠將訊息傳送至 SAP 系統正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，您必須在預先定義的位置中卸除的協調流程的要求訊息。 請參閱[RFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)須知叫用 RFC，SAP 系統中的要求訊息的結構描述。 例如，要叫用 RFC_CUSTOMER_GET 的要求訊息是：  
  
```  
<RFC_CUSTOMER_GET xmlns="http://Microsoft.LobServices.Sap/2007/03/Rfc/">  
  <KUNNR>0000001390</KUNNR>  
  <NAME1>*</NAME1>  
  <CUSTOMER_T/>  
</RFC_CUSTOMER_GET>  
```  
  
 協調流程取用訊息，並將它傳送到 SAP 系統。 SAP 系統的回應會儲存在其他定義協調流程的一部分的檔案位置。 比方說，是來自上述的要求訊息之 SAP 系統的回應：  
  
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
 如需時叫用 RFC，SAP 系統使用 BizTalk Server 中可能發生的例外狀況資訊，請參閱[例外狀況和錯誤處理與 SAP 配接器](../../adapters-and-accelerators/adapter-sap/exceptions-and-error-handling-with-the-sap-adapter.md)。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。 之後產生的繫結檔案時，您可以匯入的組態設定從檔案，讓您不需要建立傳送埠、 接收連接埠、 相同的協調流程等。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用 SAP 配接器繫結](../../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md)。  
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)