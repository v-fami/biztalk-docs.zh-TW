---
title: 從使用 BizTalk Server 的 SAP 接收輸入的 RFC 呼叫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RFC calls, receiving using BizTalk Server
ms.assetid: 822fd9fb-772f-4910-a11e-25c1d5dca6e1
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e70e2b81fd71a01ef6eae9e77ae3efea8cbf494
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986983"
---
# <a name="receive-inbound-rfc-calls-from-sap-using-biztalk-server"></a>從使用 BizTalk Server 的 SAP 接收輸入的 RFC 呼叫
在 RFC 伺服器案例中，有三個實體：  
  
- SAP 用戶端將要求傳送到 SAP，叫用 RFC。 這可能會叫用使用 SAP GUI 或藉由透過呼叫 RFC 用戶端[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
- SAP 系統，其中包含 SAP 用戶端叫用 RFC 函式定義。 SAP 系統將傳遞至 RFC 伺服器 （介面卡） 的 在要求上。 這是配接器用來取得 SAP 伺服器會讓配接器進入 RFC 呼叫的中繼資料。  
  
- [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] ，做為 RFC 伺服器以及裝載實際的 RFC。  
  
  第一個實體，也就是 SAP 用戶端不是本主題中討論。 如果您使用 SAP GUI 來叫用 RFC，請參閱 SAP 文件。 如果您使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]若要叫用 RFC，請參閱[叫用 Rfc，SAP 使用 BizTalk server 中](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-biztalk-server.md)。  
  
  本節說明如何使用配接器接收 RFC 伺服器呼叫，一旦由 SAP 用戶端叫用 RFC。 如需有關配接器如何支援接收 RFC 伺服器呼叫使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱 <<c2> [ 對 sap Rfc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-rfcs-in-sap.md)。  
  
## <a name="how-to-receive-an-inbound-rfc-call-from-the-sap-system"></a>如何從 SAP 系統接收輸入的 RFC 呼叫？  
 執行 SAP 系統使用運算[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[建立 SAP 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)。 若要從 SAP 系統接收 RFC 呼叫，這些工作如下：  
  
1. 設定您的 SAP 系統，將在此情況下傳送至外部應用程式的 RFC [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
2. 建立 BizTalk 專案，並產生結構描述，如 RFC，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會接收從 SAP 系統。  
  
3. 從 SAP 系統接收訊息，以及傳送回應的 BizTalk 專案中建立訊息。  
  
4. 建立協調流程，以接收來自 SAP 系統的 RFC、 加以處理，以及傳送回應給 SAP 系統。  
  
5. 建置和部署 BizTalk 專案。  
  
6. 設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
7. 啟動 BizTalk 應用程式。  
  
   本主題提供執行這些工作的指示。  
  
## <a name="activities-on-the-sap-system"></a>SAP 系統上的活動  
 使用之前[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]若要從 SAP 系統接收輸入的 RFC 呼叫，請確定您已完成 SAP 系統上的下列工作。  
  
- 必須存在 SAP 配接器的 RFC 目的地。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]收到 SAP 系統，透過 SAP 系統上所定義的 RFC 目的地的 Rfc。 RFC 目的地包含 SAP 閘道器主機 SAP 閘道器服務，您必須在程式碼中指定連線 URI SAP 程式 ID。 如需有關如何設定 SAP RFC 目的地的資訊，請參閱[建立 RFC、 RFC 目的地並傳送從 SAP 系統的 RFC](creating-an-rfc-in-an-sap-system.md)。  
  
- 您必須建立定義於 SAP 系統的 RFC 函式模組。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] SAP 系統上使用 RFC 定義，來擷取 RFC （兩者都在設計階段和執行階段） 的相關中繼資料。 如需詳細資訊，請參閱[SAP 系統中建立的 RFC](../../adapters-and-accelerators/adapter-sap/creating-an-rfc-in-an-sap-system.md)。  
  
   以下是來源上的程式碼會加入兩個整數並傳回其結果的 RFC 的 SAP 系統的範例。 程式碼會透過指定的目的，只是呼叫 RFC。 函式的實作是由 SAP 配接器用戶端程式碼。  
  
  ```  
  FUNCTION Z_RFC_ADD.  
  *"------------------------------------------------------------------  
  *"  
  *"Local interface:  
  *"  IMPORTING  
  *"     VALUE(X) TYPE  INT4  
  *"     VALUE(Y) TYPE  INT4  
  *"     VALUE(DEST) TYPE  CHAR20 DEFAULT 'SAPADAPTER'  
  *"  EXPORTING  
  *"     VALUE(RESULT) TYPE  INT4  
  *"------------------------------------------------------------------  
  CALL FUNCTION 'Z_RFC_ADD' DESTINATION DEST  
    EXPORTING X = X  
              Y = Y  
    IMPORTING RESULT = RESULT.  
  
  ENDFUNCTION.  
  ```  
  
## <a name="sample-based-on-this-topic"></a>根據本主題的範例  
 ，RFCServer，根據本主題也提供了範例[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 適用於 SAP 配接器範例](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md)。  
  
## <a name="generating-the-schema"></a>產生結構描述  
 本主題中，示範如何從 SAP 系統接收輸入的 RFC 呼叫我們產生的結構描述*Z_RFC_ADD* RFC。 您在上一個步驟建立此 RFC。 這個 RFC 會接受兩個整數值，做為輸入參數。  
  
 請參閱[瀏覽、 搜尋及取得中繼資料，在 SAP 中的 RFC 作業的](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md)如需有關如何產生結構描述的特定的 RFC。  
  
> [!IMPORTANT]
>  因為您會產生輸入的 RFC 呼叫的結構描述，請確定您選取**服務 （輸入作業）** 從**選取合約的型別**下拉式清單中的[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您稍早產生的結構描述會描述協調流程中的訊息所需的 「 類型 」。 訊息通常是一個變數，要為其類型會定義對應的結構。 您必須連結您的第一個步驟中的訊息從產生的 BizTalk 專案的 [協調流程] 檢視的結構描述。  
  
 本主題中，您必須建立兩個訊息，一個用來從 SAP 系統，另一個用於傳送回應給 SAP 系統接收訊息。  
  
 執行下列步驟來建立訊息，並將它們連結至結構描述：  
  
#### <a name="to-create-messages-and-link-to-schema"></a>若要建立訊息，並連結至結構描述  
  
1.  將新的協調流程加入至 BizTalk 專案中。  
  
2.  開啟協調流程檢視 BizTalk 專案中，如果未開啟。 按一下 **檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。  
  
3.  在 **協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。  
  
4.  以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。  
  
5.  在 [**屬性**] 窗格**Message_1**，執行下列動作。  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|型別**要求**。|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*RFCServer.SAPBindingSchema.Z_RFC_ADD*，其中*RFCServer*是 BizTalk 專案的名稱。 *SAPBindingSchema*是結構描述產生的 RFC *Z_RFC_ADD*。|  
  
6.  重複步驟 2 來建立新的訊息。 在 **屬性**窗格中的新訊息，執行下列動作。  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|型別**回應**。|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*RFCServer.SAPBindingSchema.Z_RFC_ADDResponse*。|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]從 SAP 系統接收 RFC 伺服器呼叫。 例如，假設 RFC 用戶端將要求傳送至 SAP 系統，以新增兩個整數的位置。 SAP 系統接受要求，以輸入參數，並將它傳遞到外部所裝載的 RFC 伺服器[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]從 SAP 系統中，處理程序要求以加入兩個整數，接收要求和產生回應。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]通過 SAP 系統接著會傳遞至 RFC 用戶端的回應。  
  
 若要這麼做為協調流程的一部分，必須包含協調流程：  
  
- 雙向接收埠以接收來自 SAP 系統的 RFC 伺服器要求，並傳送回應。  
  
- 傳送和接收圖形。  
  
- 建構訊息圖形，以及在其中訊息指派圖形，來處理 RFC 伺服器要求來自 SAP 系統。  
  
  RFC 伺服器呼叫的範例協調流程如下所示。  
  
  ![若要進行 RFC 伺服器呼叫的協調流程](../../adapters-and-accelerators/adapter-sap/media/f5da2947-56d6-41f0-b411-c8e6eacf68cd.gif "f5da2947-56d6-41f0-b411-c8e6eacf68cd")  
  
### <a name="adding-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息 圖形中指定下列屬性。 所列的名稱*圖形*資料行是訊息 圖形的名稱，上述協調流程中所示。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ListenToSAP|Receive|-設定**名稱**到*ListenToSAP*<br />-設定**啟用**到 *，則為 True*|  
|SendResponse|Send|-設定**名稱**到*SendResponse*|  
  
### <a name="adding-construct-message-shape"></a>新增 建構訊息圖形  
 為了處理內送的 RFC 呼叫，以新增兩個整數值，您必須新增 建構訊息 」 圖形，並在其中訊息指派 」 圖形至協調流程，兩者之間傳送圖形。 針對此範例中，叫用 「 訊息指派 」 圖形，以新增兩個整數。 「 訊息指派 」 圖形也會設定為傳送到 SAP 系統的回應動作。  
  
 針對 [建構訊息] 圖形中，設定**建構的訊息**屬性設**回應**。  
  
 程式碼以處理 RFC 要求可能是您的 BizTalk 專案的相同 Visual Studio 方案的一部分。 新增兩個整數的範例程式碼看起來像這樣。  
  
```  
namespace RFCServerResponseCreator  
{  
    public class RFCServerResponseCreator  
    {  
        private static XmlDocument messageIn;  
        private static XmlDocument messageOut;  
        public static XmlDocument CreateRequest(int a, int b, string destination)  
        {  
            messageIn = new XmlDocument();  
            messageIn.LoadXml(  "<Z_RFC_ADD xmlns=\"http://Microsoft.LobServices.Sap/2007/03/Rfc/\">" +  
                                "<DEST>" + destination + "</DEST>" +  
                                "<X>" + a + "</X>" +  
                                "<Y>" + b + "</Y>" +   
                                "</Z_RFC_ADD>"  
                             );  
            return messageIn;  
        }  
        public static XmlDocument CreateResponse(int a, int b)  
        {  
            int c = a + b;  
            messageOut = new XmlDocument();  
            messageOut.LoadXml( "<Z_RFC_ADDResponse xmlns=\"http://Microsoft.LobServices.Sap/2007/03/Rfc/\">" +  
                                "<RESULT>" + c + "</RESULT>" +   
                                "</Z_RFC_ADDResponse>"  
                              );  
            return messageOut;  
        }  
    }  
}  
```  
  
> [!NOTE]
>  建置專案之後，就會建立 RFCServerResponseCreator.dll 專案目錄中。 您必須將此 DLL 加入全域組件快取 (GAC)。  
  
 加入下列運算式來叫用此程式碼從 「 訊息指派 」 圖形，並設定傳送到 SAP 系統的回應動作。 若要新增運算式，請按兩下訊息指派 」 圖形以開啟 運算式編輯器。  
  
```  
Response = RFCServerResponseCreator.RFCServerResponseCreator.CreateResponse(Request.X, Request.Y);  
Response(WCF.Action) = "http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_ADD/response";  
```  
  
> [!IMPORTANT]
>  您必須明確設定回應訊息上的動作。 如果您未設定此動作，Wcf-custom 配接器在到達動作訊息附加至要求的動作的 「 回應 」。 因此，回應訊息的動作會變成`http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_ADDResponse`。 SapBinding 不過，預期的回應動作藉由附加"/ 回應 」 到所要求的動作，例如`http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_ADD/response`。  
  
### <a name="adding-ports"></a>新增連接埠  
 請確定您指定的邏輯連接埠的下列屬性。 中所列的名稱*連接埠*資料行是顯示在協調流程連接埠的名稱。  
  
|通訊埠|屬性|  
|----------|----------------|  
|RFCServerPort|-設定**識別碼**到*RFCServerPort*<br />-設定**型別**到*RFCServerPortType*<br />-設定**通訊模式**到*要求-回應*<br />-設定**通訊方向**到*接收傳送*|  
  
## <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>為動作圖形指定訊息，並連接到連接埠  
 下表指定之屬性和其值設為指定的動作圖形，並將它們連結至連接埠的訊息。 所列的名稱*圖形*資料行是訊息 圖形的名稱，上述協調流程中所示。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ListenToSAP|-設定**訊息**到*要求*<br />-設定**作業**到*RFCServerPort.Add.Request*|  
|SendResponse|-設定**訊息**到*FuncResponse*<br />-設定**作業**到*RFCServerPort.Add.Response*|  
  
 您指定這些屬性之後，連線的訊息 圖形和連接埠和協調流程已完成。  
  
 您必須立即建置 BizTalk 方案，並再將它部署到 BizTalk Server。 如需詳細資訊，請參閱 <<c0> [ 建置和執行協調流程](../../core/building-and-running-orchestrations.md)。
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在下**協調流程**在 BizTalk Server 管理主控台 窗格。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 如需有關如何設定應用程式的詳細資訊，請參閱 <<c0> [ 如何設定應用程式](../../core/how-to-configure-an-application.md)。
  
 設定應用程式包含：  
  
- 選取應用程式主機。  
  
- 對應您在您在 BizTalk Server 管理主控台中的實體連接埠的協調流程中建立的連接埠。 此協調流程中，您必須：  
  
  - 定義 WCF 自訂或 WCF SAP 接收埠。 此連接埠會從 SAP 系統接收輸入的 RFC 呼叫，而會傳送回應給 SAP 系統。 如需有關如何建立連接埠的資訊，請參閱 <<c0> [ 手動設定 SAP 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md)。  
  
    > [!NOTE]
    >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠設定動作的相關資訊的繫結檔案。 您可以從 BizTalk 管理主控台來建立 （適用於輸出的呼叫） 的傳送埠或接收埠 （適用於輸入的呼叫），以匯入此繫結檔案。 如需詳細資訊，請參閱 <<c0> [ 設定的實體連接埠繫結使用的連接埠繫結檔案至 SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md)。
  
  您也必須在 BizTalk 應用程式中新增 RFCServerResponseCreator 專案的組件。 您建立此專案來處理收到來自 SAP 系統的 RFC 呼叫。 若要這樣做：  
  
1.  BizTalk Server 管理主控台中，您匯入繫結，在 BizTalk 應用程式下的左側的主控台樹狀目錄中以滑鼠右鍵按一下**資源**，指向**新增**，然後按一下**BizTalk 組件**。  
  
2.  在 [**新增資源**] 對話方塊中，按一下**新增**，然後瀏覽至包含 RFCServerResponseCreator.dll 的資料夾。 選取檔案，然後按一下**開啟**。  
  
3.  在 [**新增資源**] 對話方塊中，按一下**確定**。  
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 BizTalk 應用程式，從 SAP 系統接收輸入的 RFC 呼叫。 如需有關啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)，並[如何啟動應用程式](../../core/how-to-start-and-stop-a-biztalk-application.md)。
  
 在這個階段，請確定：  
  
-   WCF 自訂 」 或 「 WCF SAP 接收埠以接收 RFC 呼叫從 SAP 系統正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，您必須傳送到 RFC [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 您可以藉由執行 SAP 系統上的交易 SE37 來這麼做。 您也必須指定於 RFC 呼叫的輸入的參數。 配接器接收的呼叫，以及參數、 加以處理，並傳送回應給 SAP 系統。 您將能夠從您用來傳送 RFC 在同一個交易中看到的回應。  
  
## <a name="possible-exceptions"></a>可能的例外狀況  
 如需從 SAP 系統，請使用 BizTalk Server 接收 RFC 伺服器呼叫時可能發生的例外狀況資訊，請參閱[例外狀況和錯誤處理與 SAP 配接器](../../adapters-and-accelerators/adapter-sap/exceptions-and-error-handling-with-the-sap-adapter.md)。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。 之後產生的繫結檔案時，您可以匯入的組態設定從檔案，讓您不需要建立傳送埠、 接收連接埠、 相同的協調流程等。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用 SAP 配接器繫結](../../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md)。
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)