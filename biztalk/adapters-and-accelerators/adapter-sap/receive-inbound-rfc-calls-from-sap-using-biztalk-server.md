---
title: "從 SAP 使用 BizTalk Server 接收輸入 RFC 呼叫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: RFC calls, receiving using BizTalk Server
ms.assetid: 822fd9fb-772f-4910-a11e-25c1d5dca6e1
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b949ae0d6d5938493c78ed542a67d3c8bd09b48
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="receive-inbound-rfc-calls-from-sap-using-biztalk-server"></a>從 SAP 使用 BizTalk Server 接收輸入 RFC 呼叫
在 RFC 伺服器案例中，有三個實體：  
  
-   SAP 用戶端傳送要求給 SAP RFC 叫用。 這無法叫用使用 SAP GUI，或進行 RFC 用戶端，透過呼叫[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
-   SAP 系統，其中包含 SAP 用戶端叫用的 RFC 函式定義。 SAP 系統將傳遞至 RFC 伺服器 （配接器） 的 在要求上。 這是配接器用來取得 RFC 呼叫使配接器到 SAP 伺服器的中繼資料。  
  
-   [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] ，做為 RFC 伺服器，並在裝載實際的 RFC。  
  
 在本主題不討論第一個實體，也就是 SAP 用戶端。 如果您用來叫用 RFC，SAP GUI，請參閱 SAP 文件集。 如果您使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]要叫用 RFC，請參閱[叫用的 Rfc，SAP 使用 BizTalk server 中](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-biztalk-server.md)。  
  
 本節提供如何使用配接器收到 RFC 伺服器呼叫，一旦 RFC 叫用由 SAP 用戶端上的指示。 如需有關如何配接器支援接收 RFC 伺服器呼叫使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱[作業中 SAP Rfc](../../adapters-and-accelerators/adapter-sap/operations-on-rfcs-in-sap.md)。  
  
## <a name="how-to-receive-an-inbound-rfc-call-from-the-sap-system"></a>如何從 SAP 系統接收輸入的 RFC 呼叫？  
 執行 SAP 系統使用的作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[建立的 SAP 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)。 若要從 SAP 系統接收的 RFC 呼叫，這些工作包括：  
  
1.  設定 SAP 系統，在此情況下傳送至外部應用程式的 RFC [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
2.  建立 BizTalk 專案，並產生結構描述，如 RFC，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]將接收從 SAP 系統。  
  
3.  從 SAP 系統接收訊息，並傳送回應的 BizTalk 專案中建立訊息。  
  
4.  建立協調流程，以接收來自 SAP 系統的 RFC、 處理它，並傳送回應給 SAP 系統。  
  
5.  建置和部署 BizTalk 專案。  
  
6.  設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
7.  啟動 BizTalk 應用程式。  
  
 本主題提供執行這些工作的指示。  
  
## <a name="activities-on-the-sap-system"></a>SAP 系統上的活動  
 使用之前[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]若要從 SAP 系統接收傳入的 RFC 呼叫時，請確定您已完成的 SAP 系統上的下列工作。  
  
-   必須存在 SAP 配接器的 RFC 目的地。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]接收從 SAP 系統，透過 SAP 系統上所定義的 RFC 目的地的 Rfc。 RFC 目的地包含 SAP 閘道器主機 SAP 閘道器服務，您必須在程式碼中指定連線 URI SAP 程式 ID。 如需如何設定 SAP RFC 目的地資訊，請參閱[建立 RFC、 RFC 目的地並傳送從 SAP 系統的 RFC](creating-an-rfc-in-an-sap-system.md)。  
  
-   您必須建立定義 RFC，SAP 系統的函式模組。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]使用 RFC 定義 SAP 系統上擷取 RFC （兩者都在設計階段和執行階段） 有關的中繼資料。 如需詳細資訊，請參閱[SAP 系統中建立 RFC](../../adapters-and-accelerators/adapter-sap/creating-an-rfc-in-an-sap-system.md)。  
  
     以下是原始程式碼的將兩個整數並傳回其結果的 RFC 之 SAP 系統上的範例。 程式碼只會將 RFC 呼叫透過指定的目的地。 函式的實作方式是 SAP 配接器用戶端程式碼。  
  
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
 基礎的範例，RFCServer，本主題也會提供[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱[適用於 SAP 配接器範例](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md)。  
  
## <a name="generating-the-schema"></a>產生結構描述  
 本主題中，以示範如何從 SAP 系統中，會收到輸入的 RFC 呼叫我們產生的結構描述*Z_RFC_ADD* RFC。 您在上一個步驟中建立這個 RFC。 這個 RFC 會接受兩個整數值做為輸入參數。  
  
 請參閱[瀏覽、 搜尋和 get 中繼資料中 SAP RFC 作業的](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md)如需有關如何產生結構描述特定的 RFC 的指示。  
  
> [!IMPORTANT]
>  因為您正在產生輸入 RFC 呼叫的結構描述，請確定您選取**服務 （輸入作業）**從**選取合約型別**下拉式清單中的[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您先前產生的結構描述會描述 「 類型 」 所需的協調流程中的訊息。 訊息通常是為其型別由對應的結構描述所定義的變數。 您必須連結產生的結構描述您在第一個步驟中的訊息從 BizTalk 專案的協調流程檢視。  
  
 本主題中，您必須建立兩個訊息，一個用於接收從 SAP 系統，並將回應傳送至 SAP 系統的其他訊息。  
  
 執行下列步驟來建立訊息，並將其連結至結構描述：  
  
#### <a name="to-create-messages-and-link-to-schema"></a>建立訊息，以及連結至結構描述  
  
1.  將新的協調流程加入至 BizTalk 專案。  
  
2.  開啟協調流程檢視 BizTalk 專案中，如果未開啟。 按一下**檢視**，指向 **其他視窗**，然後按一下**協調流程檢視**。  
  
3.  在**協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。  
  
4.  以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。  
  
5.  在**屬性**窗格**Message_1**，執行下列動作。  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|型別**要求**。|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*RFCServer.SAPBindingSchema.Z_RFC_ADD*，其中*RFCServer*是您的 BizTalk 專案的名稱。 *SAPBindingSchema*是結構描述產生的 RFC *Z_RFC_ADD*。|  
  
6.  重複步驟 2 來建立新的訊息。 在**屬性**窗格新訊息中，執行下列動作。  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|型別**回應**。|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*RFCServer.SAPBindingSchema.Z_RFC_ADDResponse*。|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]從 SAP 系統接收 RFC 伺服器呼叫。 例如，假設其中 RFC 用戶端將要求傳送至 SAP 系統加入兩個整數。 SAP 系統收到要求，具有輸入參數，並將它傳遞至外部所裝載的 RFC 伺服器[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]從 SAP 系統中，處理序要求以加入兩個整數，接收要求和產生回應。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會傳遞至 SAP 系統，接著會傳遞至 RFC 用戶端的回應。  
  
 若要達到此協調流程的一部分，必須包含協調流程：  
  
-   雙向接收埠以接收來自 SAP 系統的 RFC 伺服器要求並傳送回應。  
  
-   傳送和接收圖形。  
  
-   建構訊息圖形，並在訊息指派圖形，來處理 RFC 伺服器要求來自 SAP 系統。  
  
 RFC 伺服器呼叫範例協調流程如下。  
  
 ![進行 RFC 伺服器呼叫的協調流程](../../adapters-and-accelerators/adapter-sap/media/f5da2947-56d6-41f0-b411-c8e6eacf68cd.gif "f5da2947-56d6-41f0-b411-c8e6eacf68cd")  
  
### <a name="adding-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息圖形指定下列屬性。 所列的名稱*圖形*資料行名稱就是訊息圖形顯示在上述的協調流程中。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ListenToSAP|Receive|-設定**名稱**至*ListenToSAP*<br />-設定**啟動**至*，則為 True*|  
|SendResponse|Send|-設定**名稱**至*SendResponse*|  
  
### <a name="adding-construct-message-shape"></a>新增 建構訊息圖形  
 為了處理內送的 RFC 呼叫加入兩個整數值，您必須新增建構訊息 」 圖形，並在訊息指派 」 圖形至協調流程中，兩者之間傳送圖形。 針對此範例中，「 訊息指派 」 圖形會叫用加入兩個整數。 「 訊息指派 」 圖形也會設定為傳送到 SAP 系統的回應動作。  
  
 「 建構訊息 」 圖形，設定**建構訊息**屬性**回應**。  
  
 處理 RFC 要求程式碼可能是您的 BizTalk 專案相同的 Visual Studio 方案的一部分。 將兩個整數的範例程式碼看起來像這樣。  
  
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
>  建置專案之後，會建立 RFCServerResponseCreator.dll 專案目錄中。 您必須將此 DLL 加入全域組件快取 (GAC)。  
  
 加入下列運算式叫用此程式碼從 「 訊息指派 」 圖形，並設定傳送到 SAP 系統的回應動作。 若要新增運算式，請按兩下訊息指派 」 圖形以開啟運算式編輯器。  
  
```  
Response = RFCServerResponseCreator.RFCServerResponseCreator.CreateResponse(Request.X, Request.Y);  
Response(WCF.Action) = "http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_ADD/response";  
```  
  
> [!IMPORTANT]
>  您必須明確設定回應訊息上的動作。 如果您未設定此動作，Wcf-custom 配接器到達動作訊息藉由附加 「 回應 」 要求的動作。 因此，回應訊息的動作會變成`http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_ADDResponse`。 不過，sapBinding 預期的回應動作藉由附加"/ 回應 」 至要求的動作，例如`http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_ADD/response`。  
  
### <a name="adding-ports"></a>新增連接埠  
 請確定您指定的邏輯連接埠的下列屬性。 中所列的名稱*連接埠*資料行是顯示在協調流程中的連接埠名稱。  
  
|通訊埠|屬性|  
|----------|----------------|  
|RFCServerPort|-設定**識別碼**至*RFCServerPort*<br />-設定**類型**至*RFCServerPortType*<br />-設定**通訊模式**至*要求-回應*<br />-設定**通訊方向**至*接收傳送*|  
  
## <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>指定動作圖形訊息並連接至連接埠  
 下表指定屬性和其值設為指定的動作圖形，並將它們連結至連接埠的訊息。 所列的名稱*圖形*資料行名稱就是訊息圖形顯示在上述的協調流程中。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ListenToSAP|-設定**訊息**至*要求*<br />-設定**作業**至*RFCServerPort.Add.Request*|  
|SendResponse|-設定**訊息**至*FuncResponse*<br />-設定**作業**至*RFCServerPort.Add.Response*|  
  
 您指定這些屬性之後，連接的訊息 圖形和連接埠，而且您的協調流程已完成。  
  
 您必須現在可以建置 BizTalk 方案，然後再將它部署至 BizTalk Server。 如需詳細資訊，請參閱[建置和執行協調流程](../../core/building-and-running-orchestrations.md)。
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 部署 BizTalk 專案之後，您稍早建立的協調流程會列在**協調流程**BizTalk Server 管理主控台 窗格。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 如需有關如何設定應用程式的詳細資訊，請參閱[如何設定應用程式](../../core/how-to-configure-an-application.md)。
  
 設定應用程式包括：  
  
-   選取應用程式的主機。  
  
-   對應至 BizTalk Server 管理主控台中的實體連接埠在協調流程中建立的連接埠。 此協調流程中，您必須：  
  
    -   定義 WCF 自訂或 WCF SAP 接收埠。 此連接埠會從 SAP 系統接收傳入的 RFC 呼叫時，會傳送回應給 SAP 系統。 如需如何建立連接埠相關資訊，請參閱[以手動方式設定 SAP 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md)。  
  
        > [!NOTE]
        >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠的設定動作的相關資訊的繫結檔案。 您可以從 BizTalk 管理主控台來建立 （適用於傳出呼叫） 的傳送埠或接收埠 （適用於進行傳入呼叫時），以匯入此繫結檔案。 如需詳細資訊，請參閱[設定實體連接埠繫結使用連接埠繫結檔案至 SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md)。
  
 您也必須將 RFCServerResponseCreator 專案的組件加入您的 BizTalk 應用程式。 您建立此專案來處理從 SAP 系統接收到 RFC 呼叫。 若要這樣做：  
  
1.  在 BizTalk Server 管理主控台的 匯入繫結的 BizTalk 應用程式的左半部的主控台樹狀目錄中以滑鼠右鍵按一下**資源**，指向 **新增**，然後按一下**BizTalk 組件**。  
  
2.  在**新增資源**對話方塊中，按一下**新增**，然後瀏覽至包含 RFCServerResponseCreator.dll 的資料夾。 選取檔案，然後按一下**開啟**。  
  
3.  在**新增資源**對話方塊中，按一下 **確定**。  
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動從 SAP 系統接收輸入的 RFC 呼叫的 BizTalk 應用程式。 如需啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)，和[如何啟動應用程式](../../core/how-to-start-and-stop-a-biztalk-application.md)。
  
 在這個階段，請確定：  
  
-   Wcf-custom 或 WCF SAP 接收埠以接收 RFC 呼叫從 SAP 系統正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，您必須傳送至 RFC [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 您可以藉由執行 SAP 系統上的交易 SE37 來這麼做。 您也必須指定於 RFC 呼叫的輸入的參數。 配接器接收的呼叫和參數、 加以處理，並傳送回應給 SAP 系統。 您可以針對相同的交易從 RFC 的傳送位置查看回應。  
  
## <a name="possible-exceptions"></a>可能的例外狀況  
 如需例外狀況的資訊可能會遇到的 SAP 系統，使用 BizTalk Server 從接收的 RFC 伺服器呼叫時，請參閱[例外狀況和錯誤處理與 SAP 配接器](../../adapters-and-accelerators/adapter-sap/exceptions-and-error-handling-with-the-sap-adapter.md)。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。 一旦產生繫結檔案時，您可以匯入組態設定從檔案，因此您不需要建立傳送埠、 接收埠，等。 針對相同的協調流程。 如需繫結檔案的詳細資訊，請參閱[重複使用的 SAP 配接器繫結](../../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md)。
  
## <a name="see-also"></a>請參閱  
[開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)