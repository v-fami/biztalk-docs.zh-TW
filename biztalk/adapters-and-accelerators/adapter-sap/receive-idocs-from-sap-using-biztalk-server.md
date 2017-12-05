---
title: "從 SAP 使用 BizTalk Server 接收 Idoc |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDOCs, sample (receiving)
- IDOCs, business scenarios for receiving
- IDOCs, receiving from SAP using BizTalk Server
ms.assetid: b904bf07-1108-4ed3-8564-d83eaafff247
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb03368a9d046eacf31f8b7bbed5c0a7f090c3d3
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="receive-idocs-from-sap-using-biztalk-server"></a>從 SAP 使用 BizTalk Server 接收 Idoc
接收 IDOC 包括[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]做為要從 SAP 接收特殊的 RFC 呼叫的 RFC 伺服器。 SAP 配接器可以接收 Idoc 做為 RFC 伺服器或 tRFC 伺服器。 如需使用行為就像是 tRFC 伺服器配接器接收 IDOC 的詳細資訊，請參閱[從交易內容所使用的 BizTalk Server 中的 SAP 接收的 Idoc](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-in-a-transactional-context-using-biztalk-server.md)。  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]可呈現兩個不同接收 Idoc 的作業：  
  
-   **接收**作業可讓配接器接收 Idoc 具有強型別結構描述。  
  
-   **ReceiveIdoc**作業可讓配接器接收 Idoc 具有弱式型別的結構描述。 這項作業在 XML 訊息以字串形式接收 Idoc \<idocData\>標記。  
  
 在配接器端，您可以指定的值**ReceiveIDocFormat**內容繫結至指定的配接器會接收的 IDOC 格式。  
  
-   **輸入**指定配接器將會接收 Idoc，使用強型別結構描述。 這會產生 XML IDOC。  
  
-   **字串**指定配接器將會接收 Idoc 弱型別結構描述。 這會產生的 XML 訊息\<idocData\>標記。  
  
-   **Rfc**指定配接器將會接收 Idoc 中的任何格式。  
  
 接收 Idoc，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]也支援將協調流程中的一組配接器用戶端可以使用的訊息內容屬性。 如需屬性的清單，請參閱[接收 Idoc 的訊息內容屬性](../../adapters-and-accelerators/adapter-sap/message-context-properties-for-receiving-idocs.md)。  
  
 如需有關如何[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援接收 Idoc 從 SAP 系統，請參閱[sap Idoc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md)。 接收 IDOC，訊息的 SOAP 結構的詳細資訊，請參閱[IDOC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md)。  
  
## <a name="biztalk-scenarios-for-receiving-idocs-from-an-sap-system"></a>從 SAP 系統接收 Idoc BizTalk 案例  
 下表提供從 SAP 系統接收 Idoc 的重要 BizTalk 案例：  
  
|從 SAP 配接器輸入|BizTalk 處理|輸出|  
|-------------------------------|------------------------|------------|  
|（透過 tRFC 介面） 的 IDOC|**中繼資料設計階段**<br /><br /> 1.設定繫結屬性 GenerateFlatFileCompatibleIdocSchema 至**True**。<br />2.產生的結構描述**接收**作業特定的 IDOC 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。<br />3.設定繫結屬性 ReceiveIdocFormat 至**具型別**。<br /><br /> **協調流程設計階段**<br /><br /> 1.接收 XML IDOC。<br />2.使用一般檔案組合器將 XML IDOC 轉換成一般檔案。|一般檔案 IDOC|  
|（透過 tRFC 介面） 的 IDOC|**中繼資料設計階段**<br /><br /> 1.設定繫結屬性 GenerateFlatFileCompatibleIdocSchema 至**True**。<br />2.產生的結構描述**接收**作業特定的 IDOC 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。<br />3.設定繫結屬性 ReceiveIdocFormat 至**具型別**。<br /><br /> **協調流程的設計階段**<br /><br /> 接收 XML IDOC。|XML IDOC|  
|（透過 tRFC 介面） 的 IDOC|**中繼資料設計階段**<br /><br /> 1.設定繫結屬性 GenerateFlatFileCompatibleIdocSchema 至**True**。<br />2.產生的結構描述**接收**作業特定的 IDOC 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。<br />3.設定繫結屬性 ReceiveIdocFormat 至**字串**。<br /><br /> **協調流程設計階段**<br /><br /> 1.接收一般檔案 IDOC 中的 XML 訊息\<idocData\>標記。<br />2.用於擷取 XML 訊息從一般檔案 IDoc，接收埠組態使用 WCF 配接器的 XPath 支援。 例如：<br />     `/*[local-name()='ReceiveIdoc']/*[local-name()='idocData']`<br />3.使用一般檔案解譯器將一般檔案 IDOC 轉換成 XML IDOC。<br /><br /> **重要**這種方法可以用來接收 Idoc 使用新 WCF 架構[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]然後直接將它們套用在從現有的 BizTalk SAP 配接器接收的 Idoc 寫入現有的 BizTalk 專案。 這也是使用版本號碼的版次號碼 (SYSREL) 大於或等於接收 Idoc 的建議的方法。|XML IDOC|  
|（透過 tRFC 介面） 的 IDOC|**中繼資料設計階段**<br /><br /> 1.產生的結構描述**ReceiveIdoc**作業從 IDOC 節點使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。<br />2.設定繫結屬性 ReceiveIdocFormat 至**字串**。<br /><br /> **協調流程設計階段**<br /><br /> -接收的 IDOC 中的字串表示的 XML 訊息\<idocData\>標記。|XML 訊息中的一般檔案 IDOC|  
  
## <a name="how-to-receive-an-idoc-from-an-sap-system"></a>如何從 SAP 系統接收 IDOC？  
 執行 SAP 系統使用的作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[建立的 SAP 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)。 若要從 SAP 系統接收 IDOC，這些工作包括：  
  
1.  建立 BizTalk 專案，並產生您想要叫用之 SAP 系統內的 idoc 的結構描述。 產生結構描述時請確定您設定必要的繫結屬性中上, 表中列出。 如需有關如何設定繫結屬性的指示，請參閱[設定 SAP 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sap/configure-the-binding-properties-for-the-sap-adapter.md)。  
  
2.  建立傳送和從 SAP 系統接收訊息的 BizTalk 專案中的訊息。  
  
3.  建立從 SAP 系統接收 IDOC 的協調流程。  
  
4.  建置和部署 BizTalk 專案。  
  
5.  設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
6.  啟動 BizTalk 應用程式。  
  
 本主題提供執行這些工作的指示。  
  
## <a name="samples-based-on-this-topic"></a>根據本主題的範例  
 範例、 ReceiveIDOC 和 ReceiveIDOC_SYSREL，根據本主題也提供與[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱[適用於 SAP 配接器範例](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md)。  
  
## <a name="generating-schema"></a>產生結構描述  
 您必須產生結構描述的*接收*作業*ORDERS03。V3.620*下的 IDOC */IDOC/ORDERS/ORDERS03*節點。 請參閱[瀏覽、 搜尋和 get 中繼資料中 SAP IDOC 作業的](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-idoc-operations-in-sap.md)如需有關如何產生結構描述特定的 IDOC 的指示。 在產生結構描述時，您可能想要設定下列屬性：  
  
-   *GenerateFlatFileCompatibleIDoc* – 產生\<appinfo\>標記可以在 BizTalk 案例中使用 BizTalk 一般檔案剖析器，以支援一般檔案 Idoc。  
  
-   *FlatFileSegmentIndicator* – 指出如果 IDOC 結構描述\<appinfo\>區段定義名稱或區段型別名稱，應包含標記。 這是適用於使用希望傳送/接收一般檔案 IDOC 至/從 SAP。 如果*GenerateFlatFileCompatibleIDoc*設定為 false，則*FlatFileSegmentIndicator*繫結屬性會被忽略。  
  
> [!IMPORTANT]
>  因為您正在產生發話 IDOC 的結構描述，請確定您選取**服務 （輸入作業）**從**選取合約型別**下拉式清單中的[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您先前產生的結構描述會描述 「 類型 」 所需的協調流程中的訊息。 訊息通常是為其型別由對應的結構描述所定義的變數。 您必須連結產生的結構描述您在第一個步驟中的訊息從 BizTalk 專案的協調流程檢視。  
  
 本主題中，您必須建立兩個訊息，一個用於接收 IDOC 從 SAP 系統和其他傳送回應。  
  
 執行下列步驟來建立訊息，並將其連結至結構描述：  
  
#### <a name="to-create-messages-and-link-to-schema"></a>建立訊息，以及連結至結構描述  
  
1.  將新的協調流程加入至 BizTalk 專案。  
  
2.  開啟協調流程檢視 BizTalk 專案中，如果未開啟。 按一下**檢視**，指向 **其他視窗**，然後按一下**協調流程檢視**。  
  
3.  在**協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。  
  
4.  以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。  
  
5.  在**屬性**窗格**Message_1**，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|型別**要求**。|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*ReceiveIDOC.SAPBindingSchema2*，其中*ReceiveIDOC*是您的 BizTalk 專案的名稱。 *SAPBindingSchema2*是針對接收作業所產生的結構描述。|  
  
6.  重複步驟 2 來建立新的訊息。 在**屬性**窗格新訊息中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|型別**回應**。|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*ReceiveIDOC.SAPBindingSchema3*。|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]從 SAP 系統接收 Idoc。 在典型的案例中，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]從 SAP 系統接收 IDOC 呼叫、 處理要求，並傳遞至 SAP 系統的回應。 若要達到此協調流程的一部分，必須包含協調流程：  
  
-   雙向接收埠從 SAP 系統接收 Idoc，並傳送回應。  
  
-   傳送和接收圖形。  
  
-   建構訊息圖形，並在其中訊息指派圖形，以產生要傳送到 SAP 系統的回應。  
  
    > [!NOTE]
    >  如果協調流程包含雙向接收埠 （要求-回應） 用於從 SAP 系統接收 Idoc，協調流程必須傳送回應給 SAP 系統。 如果沒有，SAP 系統不會傳送下一個 IDOC。 不過，如果單向接收埠，協調流程沒有要傳送至 SAP 系統的回應。  
  
-   單向傳送埠以傳送到資料夾從 SAP 系統接收 Idoc。  
  
 從 SAP 系統接收 IDOC 範例協調流程看起來像：  
  
 ![接收 Idoc 的協調流程](../../adapters-and-accelerators/adapter-sap/media/20d4f251-2474-4fd5-becd-2915f9efa81b.gif "20d4f251-2474-4fd5-becd-2915f9efa81b")  
  
### <a name="adding-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息圖形指定下列屬性。 所列的名稱*圖形*資料行名稱就是訊息圖形上述協調流程中所示。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ListenToSAP|Receive|-設定**名稱**至*ListenToSAP*<br /><br /> -設定**啟動**至*，則為 True*|  
|SaveIDOC|Send|-設定**名稱**至*SaveIDOC*|  
|SendResponse|Send|-設定**名稱**至*SendResponse*|  
  
### <a name="adding-construct-message-shape"></a>新增 建構訊息圖形  
 在協調流程中，您必須產生回應，並傳送至 SAP 系統。 若要這樣做，您必須新增建構訊息 」 圖形，並在訊息指派圖形至協調流程。 「 訊息指派 」 圖形會叫用產生回應訊息傳送至 SAP 系統的程式碼。 「 訊息指派 」 圖形也會設定為傳送到 SAP 系統的回應動作。  
  
> [!IMPORTANT]
>  如果協調流程包含雙向接收埠 （要求-回應） 用於從 SAP 系統接收 Idoc，協調流程必須傳送回應給 SAP 系統。 如果沒有，SAP 系統不會傳送下一個 IDOC。 不過，如果單向接收埠，協調流程沒有要傳送至 SAP 系統的回應。  
  
 對於 「 建構訊息 」 圖形，設定**建構訊息**屬性**回應**。  
  
 產生回應的程式碼可能是您的 BizTalk 專案相同的 Visual Studio 方案的一部分。 產生回應訊息的範例程式碼看起來像這樣。  
  
```  
namespace IdocReceiveResponseMessageCreator  
{  
    public class IdocReceiveResponseMessageCreator  
    {  
        private static XmlDocument Message;  
        private static string XmlFileLocation;  
        private static string ResponseDoc;  
  
        public static XmlDocument XMLMessageCreator()  
        {  
            XmlFileLocation = "C:\\test\\in";  
            try  
            {  
                ResponseDoc = (Directory.GetFiles(XmlFileLocation, "*.xml", SearchOption.TopDirectoryOnly))[0];  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Trying to get XML from: " + XmlFileLocation);  
                Console.WriteLine("EXCEPTION: " + ex.ToString());  
                throw ex;  
            }  
            //Create Message From XML  
            Message = new XmlDocument();  
            Message.PreserveWhitespace = true;  
            Message.Load(ResponseDoc);  
            return Message;  
        }   
    }  
}  
```  
  
> [!NOTE]
>  建置專案之後，會建立 IdocReceiveResponseMessageCreator.dll 專案目錄中。 您必須將此 DLL 加入全域組件快取 (GAC)。  
  
 加入下列運算式叫用此程式碼從 「 訊息指派 」 圖形，並設定傳送到 SAP 系統的回應動作。 若要新增運算式，請按兩下訊息指派 」 圖形以開啟運算式編輯器。  
  
```  
Response = IdocReceiveResponseMessageCreator.IdocReceiveResponseMessageCreator.XMLMessageCreator();  
Response(WCF.Action)= "http://Microsoft.LobServices.Sap/2007/03/Idoc/3/ORDERS03//620/Receive/response";  
```  
  
> [!IMPORTANT]
>  您必須明確設定回應訊息上的動作。 如果您未設定此動作，Wcf-custom 配接器到達動作訊息藉由附加 「 回應 」 要求的動作。 因此，回應訊息的動作會變成`http://Microsoft.LobServices.Sap/2007/03/Idoc/3/ORDERS03//620/ReceiveResponse`。 不過，sapBinding 預期的回應動作藉由附加"/ 回應 」 至要求的動作，例如`http://Microsoft.LobServices.Sap/2007/03/Idoc/3/ORDERS03//620/Receive/response`。  
  
### <a name="adding-ports"></a>新增連接埠  
 請確定您指定的邏輯連接埠的下列屬性。 中所列的名稱*連接埠*資料行是顯示在協調流程中的連接埠名稱。  
  
|通訊埠|屬性|  
|----------|----------------|  
|ReceiveIDOCPort|-設定**識別碼**至*ReceiveIDOCPort*<br /><br /> -設定**類型**至*ReceiveIDOCPortType*<br /><br /> -設定**通訊模式**至*要求-回應*<br /><br /> -設定**通訊方向**至*接收傳送*|  
|GetIDOCPort|-設定**識別碼**至*GetIDOCPort*<br /><br /> -設定**類型**至*GetIDOCPortType*<br /><br /> -設定**通訊模式**至*單向*<br /><br /> -設定**通訊方向**至*傳送*|  
  
> [!IMPORTANT]
>  如果協調流程包含雙向接收埠 （要求-回應） 用於從 SAP 系統接收 Idoc，協調流程必須傳送回應給 SAP 系統。 如果沒有，SAP 系統不會傳送下一個 IDOC。  
  
### <a name="adding-a-flat-file-assembler"></a>加入一般檔案組合器  
 您必須加入將內送的 IDOC 訊息轉換成一般檔案組合器。  
  
##### <a name="to-add-a-flat-file-assembler"></a>若要加入一般檔案組合器  
  
1.  以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後選取**新項目**。  
  
2.  從對話方塊中，執行下列作業：  
  
    |使用|動作|  
    |--------------|----------------|  
    |類別|管線檔案|  
    |Visual Studio 安裝的範本|傳送管線|  
    |名稱|SendIDOC|  
  
3.  這會開啟 「 管線設計師 」。 從**BizTalk 管線元件**工具箱，拖曳**一般檔案組合器**管線元件**組合**傳送管線階段。  
  
4.  從**管線元件屬性**檢視中，指定的值**文件結構描述**屬性。 從下拉式清單確認您選取的結構描述對應至 IDOC 接收作業。  
  
## <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>指定動作圖形訊息並連接至連接埠  
 下表指定屬性和其值設為指定的動作圖形，並將它們連結至連接埠的訊息。 所列的名稱*圖形*資料行名稱就是訊息圖形上述協調流程中所示。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ListenToSAP|-設定**訊息**至*要求*<br /><br /> -設定**作業**至*ReceiveIDOCPort.ReceiveIDOC.Request*|  
|SaveIDOC|-設定**訊息**至*要求*<br /><br /> -設定**作業**至*GetIDOCPort.ReceiveIDOC.Request*|  
|SendResponse|-設定**訊息**至*回應*<br /><br /> -設定**作業**至*ReceiveIDOCPort.ReceiveIDOC.Response*|  
  
 您指定這些屬性之後，連接的訊息 圖形和連接埠，而且您的協調流程已完成。  
  
 您現在必須建置 BizTalk 方案，並部署到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱[建置和執行協調流程](../../core/building-and-running-orchestrations.md)
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 部署 BizTalk 專案之後，您稍早建立的協調流程會列在**協調流程**BizTalk Server 管理主控台 窗格。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 如需有關如何設定應用程式的詳細資訊，請參閱[如何設定應用程式](../../core/how-to-configure-an-application.md)。
  
 設定應用程式包括：  
  
-   選取應用程式的主機。  
  
-   對應至 BizTalk Server 管理主控台中的實體連接埠在協調流程中建立的連接埠。 此協調流程中，您必須：  
  
    -   定義傳送位置和實體傳送埠。 這個位置會包含來自 SAP 系統的 Idoc。  
  
        > [!IMPORTANT]
        >  XMLTransmit 管線，請確定您選取***SendIDOC***。 您建立此管線的 BizTalk 專案的一部分。  
  
    -   定義 WCF 自訂或 WCF SAP 接收埠。 此連接埠會從 SAP 系統接收輸入的 IDOC，並將它傳遞至協調流程。 此連接埠也會傳送至 SAP 系統的回應。 如需如何建立連接埠相關資訊，請參閱[以手動方式設定 SAP 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md)。
  
        > [!IMPORTANT]
        >  請確定繫結屬性**ReceiveIDocFormat**設**具型別**。  
  
        > [!IMPORTANT]
        >  如果繫結屬性**EnableBizTalkCompatibilityMode**設為 true，則請確認您新增 BizTalk 屬性結構描述 DLL 的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]為您的 BizTalk 應用程式，也就是在其中應用程式中的資源程式部署專案。 如需將資源加入的指示，請參閱[疑難排解操作問題 SAP 配接器](../../adapters-and-accelerators/adapter-sap/troubleshoot-operational-issues-with-the-sap-adapter.md)。  
  
        > [!NOTE]
        >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠的設定動作的相關資訊的繫結檔案。 您可以從 BizTalk 管理主控台來建立 （適用於傳出呼叫） 的傳送埠或接收埠 （適用於進行傳入呼叫時），以匯入此繫結檔案。 如需詳細資訊，請參閱[設定實體連接埠繫結使用連接埠繫結檔案至 SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md)。
  
 您也必須將 IdocReceiveResponseMessageCreator 專案的組件加入您的 BizTalk 應用程式。 您建立此專案來產生要傳送到 SAP 系統的回應。 若要這樣做：  
  
1.  在 BizTalk Server 管理主控台的 匯入繫結的 BizTalk 應用程式的左半部的主控台樹狀目錄中以滑鼠右鍵按一下**資源**，指向 **新增**然後按一下**BizTalk 組件**。  
  
2.  在**新增資源**對話方塊中，按一下**新增**並瀏覽至包含 IdocReceiveResponseMessageCreator.dll 的資料夾。 選取檔案，然後按一下**開啟**。  
  
3.  在**新增資源**對話方塊中，按一下 **確定**。  
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動從 SAP 系統接收 IDOC 的 BizTalk 應用程式。 如需啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)，或[如何啟動應用程式](../../core/how-to-start-and-stop-a-biztalk-application.md)。
  
 在這個階段，請確定：  
  
-   執行 FILE 傳送埠，以儲存傳入的 IDOC 至檔案位置  
  
-   Wcf-custom 或 WCF SAP 接收埠以接收 Idoc 從 SAP 系統正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，您必須移 SAP 系統，並傳送 IDOC 到配接器。 配接器接收 IDOC，並將它儲存至檔案位置指定為協調流程的一部分。  
  
## <a name="possible-exceptions"></a>可能的例外狀況  
 如需從使用 BizTalk Server 的 SAP 系統接收 IDOC 時可能會遇到的例外狀況資訊，請參閱[例外狀況和錯誤處理與 SAP 配接器](../../adapters-and-accelerators/adapter-sap/exceptions-and-error-handling-with-the-sap-adapter.md)。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。 一旦產生繫結檔案時，您可以匯入組態設定從檔案，因此您不需要建立傳送埠、 接收埠，等。 針對相同的協調流程。 如需繫結檔案的詳細資訊，請參閱[重複使用的 SAP 配接器繫結](../../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md)。
  
## <a name="see-also"></a>請參閱  
[開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)