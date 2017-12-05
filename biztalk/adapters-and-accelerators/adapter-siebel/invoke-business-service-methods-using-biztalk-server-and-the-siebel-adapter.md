---
title: "叫用商務服務方法使用 BizTalk Server 和 Siebel 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- how to, invoke business service methods
- business service methods, invoking
ms.assetid: cf437c4f-fa65-4f89-a197-c83869930b2c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79a11d3be19ca27bd27146ef728ce168c3285884
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="invoke-business-service-methods-using-biztalk-server-and-the-siebel-adapter"></a>叫用商務服務方法使用 BizTalk Server 和 Siebel 配接器
Siebel 商務服務是可以在 Siebel 中直接叫用的商務方法的集合。 如需有關如何[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]支援叫用商務服務在 Siebel 系統中，請參閱[在 Siebel 商務服務的相關作業](../../adapters-and-accelerators/adapter-siebel/operations-on-business-services-in-siebel.md)。 執行商務服務作業，訊息的 SOAP 結構的詳細資訊，請參閱[商務服務作業的訊息結構描述](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-service-operations.md)。  
  
## <a name="how-to-invoke-business-services"></a>如何叫用商務服務？  
 使用 Siebel 系統上執行操作[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[Siebel 配接器建立 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)。 要叫用商務服務，這些工作包括：  
  
1.  建立 BizTalk 專案，並產生您想要叫用商務服務方法的結構描述。  
  
2.  建立傳送和接收來自 Siebel 系統訊息的 BizTalk 專案中的訊息。  
  
3.  建立協調流程叫用商務服務方法在 Siebel 系統。  
  
4.  建置和部署 BizTalk 專案。  
  
5.  設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
6.  啟動 BizTalk 應用程式。  
  
 本主題提供執行這些工作的指示。  
  
## <a name="sample-based-on-this-topic"></a>根據本主題的範例  
 基礎的範例，BusinessService，本主題也會提供[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱[Siebel 配接器的範例](../../adapters-and-accelerators/adapter-siebel/samples-for-the-siebel-adapter.md)。  
  
## <a name="generating-schema"></a>產生結構描述  
 在本主題中，以示範如何叫用商務服務方法，我們還會產生結構描述**Execute**所公開的方法**時間戳記**商務服務。 請參閱[擷取 Siebel 作業在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md)如需有關如何產生結構描述。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您先前產生的結構描述會描述 「 類型 」 所需的協調流程中的訊息。 訊息通常是為其型別由對應的結構描述所定義的變數。 您必須連結產生的結構描述您在第一個步驟中的訊息從 BizTalk 專案的協調流程檢視。  
  
 本主題中，您必須建立兩個訊息，其中將要求傳送至 Siebel 系統，而另一個則接收回應。  
  
 執行下列步驟來建立訊息，並將其連結至結構描述：  
  
#### <a name="to-create-messages-and-link-to-schema"></a>建立訊息，以及連結至結構描述  
  
1.  開啟協調流程檢視 BizTalk 專案中，如果未開啟。 按一下**檢視**，指向 **其他視窗**，然後按一下**協調流程檢視**。  
  
2.  在**協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。  
  
3.  以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。  
  
4.  在**屬性**窗格**Message_1**，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|型別**要求**。|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*BusinessService.SiebelBindingSchema.Execute*，其中*BusinessService*是您的 BizTalk 專案的名稱。 *SiebelBindingSchema*是叫用所產生的結構描述*Execute*商務服務方法。|  
  
5.  重複上述步驟，建立新的訊息。 在**屬性**窗格新訊息中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|型別**回應**。|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*BusinessService.SiebelBindingSchema.ExecuteResponse*。|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]叫用商務服務。 在此協調流程中，卸除要求訊息已定義的接收位置。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]會取用這個訊息，並將它傳遞到 Siebel 系統。 來自 Siebel 系統的回應會儲存到另一個位置。 典型的協調流程叫用商務服務方法就會包含：  
  
-   傳送和接收圖形以將訊息傳送到 Siebel 並接收回應。  
  
-   單向接收埠以接收要求訊息傳送到 Siebel。  
  
-   雙向傳送埠以將要求訊息傳送到 Siebel 並接收回應。  
  
-   單向傳送埠，以便從 Siebel 傳送回應到資料夾。  
  
 範例協調流程呼叫*Execute*方法*時間戳記*商務服務類似如下所示：  
  
 ![叫用商務服務的協調流程](../../adapters-and-accelerators/adapter-siebel/media/5a776e5d-855f-4d1b-8d26-7de747b1865d.gif "5a776e5d-855f-4d1b-8d26-7de747b1865d")  
  
### <a name="adding-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息圖形指定下列屬性。 所列的名稱*圖形*資料行名稱就是訊息圖形上述協調流程中所示。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveXML|Receive|-設定**名稱**至*ReceiveXML*<br />-設定**啟動**至*，則為 True*|  
|SendToLOB|Send|-設定**名稱**至*SendToLOB*|  
|ReceiveResponse|Receive|-設定**名稱**至*ReceiveResponse*<br />-設定**啟動**至*False*|  
|SendResponse|Send|-設定**名稱**至*SendResponse*|  
  
### <a name="adding-ports"></a>新增連接埠  
 請確定您針對每個邏輯連接埠指定下列屬性。 所列的名稱*連接埠*資料行是連接埠的名稱，顯示在 協調流程中。  
  
|通訊埠|屬性|  
|----------|----------------|  
|FileIn|-設定**識別碼**至*FileIn*<br />-設定**類型**至*FileInType*<br />-設定**通訊模式**至*單向*<br />-設定**通訊方向**至*接收*|  
|LOBPort|-設定**識別碼**至*LOBPort*<br />-設定**類型**至*LOBPortType*<br />-設定**通訊模式**至*要求-回應*<br />-設定**通訊方向**至*傳送接收*|  
|SaveResponse|-設定**識別碼**至*SaveResponse*<br />-設定**類型**至*SaveResponseType*<br />-設定**通訊模式**至*單向*<br />-設定**通訊方向**至*傳送*|  
  
## <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>指定動作圖形訊息並連接至連接埠  
 下表指定屬性和其值設為指定的動作圖形，並將它們連結至連接埠的訊息。 所列的名稱*圖形*資料行名稱就是訊息圖形上述協調流程中所示。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveXML|-設定**訊息**至*要求*<br />-設定**作業**至*FileIn.ServiceInvoke.Request*|  
|SendToLOB|-設定**訊息**至*要求*<br />-設定**作業**至*LOBPort.ServiceInvoke.Request*|  
|ReceiveResponse|-設定**訊息**至*回應*<br />-設定**作業**至*LOBPort.ServiceInvoke.Response*|  
|SendResponse|-設定**訊息**至*回應*<br />-設定**作業**至*SaveResponse.ServiceInvoke.Request*|  
  
 您指定這些屬性之後，連接的訊息 圖形和連接埠，而且您的協調流程已完成。  
  
 您現在必須建置 BizTalk 方案，並部署到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱[如何建置協調流程](../../core/how-to-build-orchestrations.md)和[從到 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。 
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 部署 BizTalk 專案之後，您稍早建立的協調流程會列在**協調流程**BizTalk Server 管理主控台 窗格。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 如需有關如何設定應用程式的詳細資訊，請參閱[如何建立應用程式](../../core/how-to-create-an-application.md)。  
  
 設定應用程式包括：  
  
-   選取應用程式的主機。  
  
-   對應至 BizTalk Server 管理主控台中的實體連接埠在協調流程中建立的連接埠。 此協調流程中，您必須：  
  
    -   定義位置上的硬碟和對應的檔案連接埠，您將在此置放要求訊息。 BizTalk 協調流程會使用要求訊息，並將它傳送至 Siebel 系統。  
  
    -   定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含來自 Siebel 系統的回應的回應訊息。  
  
    -   定義將訊息傳送至 Siebel 系統實體 Wcf-custom 或 Wcf-siebel 傳送埠。 您也必須在傳送埠中指定的動作。 如需如何建立連接埠相關資訊，請參閱[手動設定在 Siebel 介面卡的實體連接埠繫結](../../adapters-and-accelerators/adapter-siebel/manually-configure-a-physical-port-binding-to-the-siebel-adapter.md)。
  
        > [!NOTE]
        >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠的設定動作的相關資訊的繫結檔案。 您可以從 BizTalk 管理主控台建立傳送埠 （適用於傳出呼叫） 來匯入此繫結檔案。 如需詳細資訊，請參閱[設定實體連接埠繫結使用連接埠繫結檔案至 Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-physical-port-binding-using-a-port-binding-file-to-siebel.md)。
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 BizTalk 應用程式執行*Execute*方法*時間戳記*在 Siebel 商務服務。 如需啟動 BizTalk 應用程式的指示，請參閱[啟動 BizTalk 應用程式](../../core/how-to-start-and-stop-a-biztalk-application.md)或[啟動協調流程](../../core/how-to-start-an-orchestration.md)。
  
 在這個階段，請確定：  
  
-   FILE 接收埠以接收要求訊息的協調流程執行。  
  
-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  
  
-   Wcf-custom 或 Wcf-siebel 傳送埠將訊息傳送至 Siebel 系統正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 您必須將要求訊息卸除檔案接收位置。 要求訊息的結構描述必須確認以您稍早在本主題中所產生的結構描述。 請參閱[商務服務作業的訊息結構描述](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-service-operations.md)如需有關在叫用商務服務的結構描述。 例如，要叫用的要求訊息*Execute*方法*時間戳記*商務服務是：  
  
```  
<Execute xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/TimeStamp/Operation" />  
```  
  
 協調流程會使用要求訊息，並將其傳遞至 Siebel 系統。 來自 Siebel 系統的回應會儲存在檔案傳送位置。 上述的要求訊息的回應是：  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<ExecuteResponse xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/TimeStamp/Operation">  
  <ExecuteResult>  
    <Time xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/TimeStamp">2007-11-25T20:42:11.0000000</Time>  
  </ExecuteResult>  
</ExecuteResponse>  
```  
  
## <a name="possible-exceptions"></a>可能的例外狀況  
 例外狀況的資訊可能會遇到對執行作業時使用的商務服務[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[例外狀況和錯誤處理 Siebel 配接器](../../adapters-and-accelerators/adapter-siebel/exceptions-and-error-handling-with-the-siebel-adapter.md)。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。 一旦產生繫結檔案時，您可以匯入組態設定從檔案，因此您不需要建立傳送埠、 接收埠，等。 針對相同的協調流程。 如需繫結檔案的詳細資訊，請參閱[重複使用 Siebel 配接器中的配接器繫結](../../adapters-and-accelerators/adapter-siebel/reuse-adapter-bindings-in-the-siebel-adapter.md)。
  
## <a name="see-also"></a>請參閱  
[若要建立 Siebel 配接器的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)