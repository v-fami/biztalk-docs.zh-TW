---
title: 從使用 BizTalk Server 的 SAP 接收 Idoc |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDOCs, sample (receiving)
- IDOCs, business scenarios for receiving
- IDOCs, receiving from SAP using BizTalk Server
ms.assetid: b904bf07-1108-4ed3-8564-d83eaafff247
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3620ea444dd42863ea8242640fb94c873f63c001
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989767"
---
# <a name="receive-idocs-from-sap-using-biztalk-server"></a>從使用 BizTalk Server 的 SAP 接收 Idoc
接收 IDOC 包括[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]做為要從 SAP 接收特殊的 RFC 呼叫 RFC 伺服器。 SAP 配接器可以接收 Idoc 做為 RFC 伺服器或 tRFC 伺服器。 如需使用行為就像是 tRFC 伺服器的配接器接收 IDOC 的詳細資訊，請參閱[接收的 Idoc，從交易內容所使用的 BizTalk Server 中的 SAP](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-in-a-transactional-context-using-biztalk-server.md)。  

 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現兩個不同接收 Idoc 的作業：  

- **接收**作業可讓配接器接收 Idoc 具有強型別結構描述。  

- **ReceiveIdoc**作業可讓配接器接收 Idoc 具有弱式型別結構描述。 這項作業下的 XML 訊息中的字串形式接收 Idoc \<idocData\>標記。  

  在配接器端，您可以指定的值**ReceiveIDocFormat**繫結至指定的配接器會接收的 IDOC 格式的屬性。  

- **輸入**指定配接器將會接收 Idoc，使用強型別結構描述。 這會產生 XML IDOC。  

- **字串**指定配接器將會接收 Idoc 弱型別結構描述。 這會產生的 XML 訊息\<idocData\>標記。  

- **Rfc**指定配接器將會接收 Idoc 中的任何格式。  

  接收 Idoc，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]也支援協調流程中的 訊息內容屬性，配接器用戶端可以使用一組。 如需屬性的清單，請參閱[接收的 Idoc 的訊息內容屬性](../../adapters-and-accelerators/adapter-sap/message-context-properties-for-receiving-idocs.md)。  

  如需有關如何[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援接收 Idoc，從 SAP 系統，請參閱[對 sap Idoc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md)。 如以便接收 IDOC，訊息的 SOAP 結構的詳細資訊，請參閱 < [IDOC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md)。  

## <a name="biztalk-scenarios-for-receiving-idocs-from-an-sap-system"></a>從 SAP 系統接收 Idoc BizTalk 案例  
 下表將提供從 SAP 系統接收 Idoc BizTalk 的重要案例：  


| 從 SAP 配接器輸入 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        BizTalk 處理                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |            輸出             |
|---------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------|
| （透過 tRFC 介面） 的 IDOC |                                                                                                                                                                                                                                                                                                                                           **中繼資料設計階段**<br /><br /> 1.設定繫結屬性 GenerateFlatFileCompatibleIdocSchema 來 **，則為 True**。<br />2.產生的結構描述**接收**作業特定的 IDOC 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。<br />3.設定繫結屬性 ReceiveIdocFormat 來**具型別**。<br /><br /> **協調流程設計階段**<br /><br /> 1.接收 XML IDOC。<br />2.您可以使用一般檔案組合器將 XML IDOC 轉換成一般檔案。                                                                                                                                                                                                                                                                                                                                           |        一般檔案 IDOC         |
| （透過 tRFC 介面） 的 IDOC |                                                                                                                                                                                                                                                                                                                                                                             **中繼資料設計階段**<br /><br /> 1.設定繫結屬性 GenerateFlatFileCompatibleIdocSchema 來 **，則為 True**。<br />2.產生的結構描述**接收**作業特定的 IDOC 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。<br />3.設定繫結屬性 ReceiveIdocFormat 來**具型別**。<br /><br /> **協調流程的設計階段**<br /><br /> 接收 XML IDOC。                                                                                                                                                                                                                                                                                                                                                                              |           XML IDOC            |
| （透過 tRFC 介面） 的 IDOC | **中繼資料設計階段**<br /><br /> 1.設定繫結屬性 GenerateFlatFileCompatibleIdocSchema 來 **，則為 True**。<br />2.產生的結構描述**接收**作業特定的 IDOC 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。<br />3.設定繫結屬性 ReceiveIdocFormat 來**字串**。<br /><br /> **協調流程設計階段**<br /><br /> 1.接收 XML 訊息中的一般檔案 IDOC \<idocData\>標記。<br />2.使用 接收埠組態 WCF 配接器的 XPath 支援，來擷取 XML 訊息的一般檔案 IDoc。 例如：<br />     `/*[local-name()='ReceiveIdoc']/*[local-name()='idocData']`<br />3.您可以使用一般檔案解譯器將一般檔案 IDOC 轉換成 XML IDOC。<br /><br /> **重要**這種方法可以用來接收 Idoc 使用新 wcf[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]並直接將它們套用到從現有的 BizTalk SAP 配接器接收 Idoc 寫入現有的 BizTalk 專案中。 這也是建議的方法，用於接收 Idoc 版本號碼小於版次號碼 (SYSREL)。 |           XML IDOC            |
| （透過 tRFC 介面） 的 IDOC |                                                                                                                                                                                                                                                                                                                                                                                     **中繼資料設計階段**<br /><br /> 1.產生的結構描述**ReceiveIdoc** IDOC 節點使用的作業[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。<br />2.設定繫結屬性 ReceiveIdocFormat 來**字串**。<br /><br /> **協調流程設計階段**<br /><br /> 接收 XML 訊息與表示為字串中的 IDOC \<idocData\>標記。                                                                                                                                                                                                                                                                                                                                                                                     | XML 訊息中的一般檔案 IDOC |

## <a name="how-to-receive-an-idoc-from-an-sap-system"></a>如何從 SAP 系統接收 IDOC？  
 執行 SAP 系統使用運算[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[建立 SAP 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)。 若要從 SAP 系統接收 IDOC，這些工作如下：  

1. 建立 BizTalk 專案，並產生您想要叫用 SAP 系統中 IDOC 的結構描述。 產生結構描述時請確定您設定必要的繫結的屬性上, 表中所示。 如需有關如何設定繫結屬性的指示，請參閱 <<c0> [ 設定 SAP 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sap/configure-the-binding-properties-for-the-sap-adapter.md)。  

2. 建立傳送和接收訊息，從 SAP 系統的 BizTalk 專案中的訊息。  

3. 建立 SAP 系統接收 IDOC 的協調流程。  

4. 建置和部署 BizTalk 專案。  

5. 設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  

6. 啟動 BizTalk 應用程式。  

   本主題提供執行這些工作的指示。  

## <a name="samples-based-on-this-topic"></a>根據本主題的範例  
 範例、 ReceiveIDOC 和 ReceiveIDOC_SYSREL，根據本主題也會提供與[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 適用於 SAP 配接器範例](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md)。  

## <a name="generating-schema"></a>產生結構描述  
 您必須產生結構描述*接收*營運*ORDERS03。V3.620*下的 IDOC */IDOC/ORDERS/ORDERS03*節點。 請參閱[瀏覽、 搜尋及取得中繼資料中 SAP IDOC 作業的](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-idoc-operations-in-sap.md)如需有關如何產生特定的 IDOC 的結構描述。 在產生結構描述時，您可能想要設定下列屬性：  

-   *GenerateFlatFileCompatibleIDoc* – 產生\<appinfo\>標記，以便可以在 BizTalk 案例中使用 BizTalk 一般檔案剖析器，以支援一般檔案 Idoc。  

-   *FlatFileSegmentIndicator* – 指出如果 IDOC 結構描述\<appinfo\>標記應該包含區段定義名稱或區段型別名稱。 這是適用於使用希望傳送/接收往返 SAP 的一般檔案 IDOC。 如果*GenerateFlatFileCompatibleIDoc*設為 false，則*FlatFileSegmentIndicator*屬性繫結會被忽略。  

> [!IMPORTANT]
>  因為您會產生錯誤的 「 發話 IDOC 的結構描述，請確定您選取**服務 （輸入作業）** 從**選取合約的型別**下拉式清單中的[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。  

## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您稍早產生的結構描述會描述協調流程中的訊息所需的 「 類型 」。 訊息通常是一個變數，要為其類型會定義對應的結構。 您必須連結您的第一個步驟中的訊息從產生的 BizTalk 專案的 [協調流程] 檢視的結構描述。  

 本主題中，您必須建立兩個訊息，一個用於接收 IDOC，從 SAP 系統，另一個用於傳送回應。  

 執行下列步驟來建立訊息，並將它們連結至結構描述：  

#### <a name="to-create-messages-and-link-to-schema"></a>若要建立訊息，並連結至結構描述  

1.  將新的協調流程加入至 BizTalk 專案中。  

2.  開啟協調流程檢視 BizTalk 專案中，如果未開啟。 按一下 **檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。  

3.  在 **協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。  

4.  以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。  

5.  在 [**屬性**] 窗格**Message_1**，執行下列動作：  

    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|型別**要求**。|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*ReceiveIDOC.SAPBindingSchema2*，其中*ReceiveIDOC*是 BizTalk 專案的名稱。 *SAPBindingSchema2*是針對接收作業產生的結構描述。|  

6.  重複步驟 2 來建立新的訊息。 在 **屬性**窗格中的新訊息，執行下列動作：  

    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|型別**回應**。|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*ReceiveIDOC.SAPBindingSchema3*。|  

## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]從 SAP 系統接收 idoc 用的。 在典型的案例中，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]從 SAP 系統接收 IDOC 呼叫、 處理要求，並傳遞至 SAP 系統的回應。 若要這麼做為協調流程的一部分，必須包含協調流程：  

- 雙向接收埠從 SAP 系統接收 Idoc，並傳送回應。  

- 傳送和接收圖形。  

- 建構訊息圖形，並在其中訊息指派圖形，以產生要傳送至 SAP 系統的回應。  

  > [!NOTE]
  >  如果協調流程包含雙向接收埠 （要求-回應），若要從 SAP 系統接收 Idoc，協調流程必須傳送回應給 SAP 系統。 否則，SAP 系統不會傳送下一步 的 IDOC。 不過，如果單向接收埠，協調流程沒有要傳送到 SAP 系統的回應。  

- 單向傳送埠以傳送 Idoc 從 SAP 系統接收到的資料夾。  

  從 SAP 系統接收 IDOC 範例協調流程看起來像：  

  ![接收 Idoc 的協調流程](../../adapters-and-accelerators/adapter-sap/media/20d4f251-2474-4fd5-becd-2915f9efa81b.gif "20d4f251-2474-4fd5-becd-2915f9efa81b")  

### <a name="adding-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息 圖形中指定下列屬性。 所列的名稱*圖形*資料行是訊息 圖形的名稱，上述協調流程中所示。  

|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ListenToSAP|Receive|-設定**名稱**到*ListenToSAP*<br /><br /> -設定**啟用**到 *，則為 True*|  
|SaveIDOC|Send|-設定**名稱**到*SaveIDOC*|  
|SendResponse|Send|-設定**名稱**到*SendResponse*|  

### <a name="adding-construct-message-shape"></a>新增 建構訊息圖形  
 在協調流程中，您必須產生回應，並將它傳送到 SAP 系統。 若要這樣做，您必須加入 「 建構訊息 」 圖形，並在其中 「 訊息指派圖形至協調流程。 「 訊息指派 」 圖形叫用產生回應訊息傳送至 SAP 系統的程式碼。 「 訊息指派 」 圖形也會設定為傳送到 SAP 系統的回應動作。  

> [!IMPORTANT]
>  如果協調流程包含雙向接收埠 （要求-回應），若要從 SAP 系統接收 Idoc，協調流程必須傳送回應給 SAP 系統。 否則，SAP 系統不會傳送下一步 的 IDOC。 不過，如果單向接收埠，協調流程沒有要傳送到 SAP 系統的回應。  

 針對 「 建構訊息 」 圖形中，設定**建構的訊息**屬性設**回應**。  

 若要產生回應的程式碼可以是相同的 Visual Studio 方案，為您的 BizTalk 專案的一部分。 產生回應訊息的範例程式碼看起來像這樣。  

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
>  建置專案之後，就會建立 IdocReceiveResponseMessageCreator.dll 專案目錄中。 您必須將此 DLL 加入全域組件快取 (GAC)。  

 加入下列運算式來叫用此程式碼從 「 訊息指派 」 圖形，並設定傳送到 SAP 系統的回應動作。 若要新增運算式，請按兩下訊息指派 」 圖形以開啟 運算式編輯器。  

```  
Response = IdocReceiveResponseMessageCreator.IdocReceiveResponseMessageCreator.XMLMessageCreator();  
Response(WCF.Action)= "http://Microsoft.LobServices.Sap/2007/03/Idoc/3/ORDERS03//620/Receive/response";  
```  

> [!IMPORTANT]
>  您必須明確設定回應訊息上的動作。 如果您未設定此動作，Wcf-custom 配接器在到達動作訊息附加至要求的動作的 「 回應 」。 因此，回應訊息的動作會變成`http://Microsoft.LobServices.Sap/2007/03/Idoc/3/ORDERS03//620/ReceiveResponse`。 SapBinding 不過，預期的回應動作藉由附加"/ 回應 」 到所要求的動作，例如`http://Microsoft.LobServices.Sap/2007/03/Idoc/3/ORDERS03//620/Receive/response`。  

### <a name="adding-ports"></a>新增連接埠  
 請確定您指定的邏輯連接埠的下列屬性。 中所列的名稱*連接埠*資料行是顯示在協調流程連接埠的名稱。  

|通訊埠|屬性|  
|----------|----------------|  
|ReceiveIDOCPort|-設定**識別碼**到*ReceiveIDOCPort*<br /><br /> -設定**型別**到*ReceiveIDOCPortType*<br /><br /> -設定**通訊模式**到*要求-回應*<br /><br /> -設定**通訊方向**到*接收傳送*|  
|GetIDOCPort|-設定**識別碼**到*GetIDOCPort*<br /><br /> -設定**型別**到*GetIDOCPortType*<br /><br /> -設定**通訊模式**到*單向*<br /><br /> -設定**通訊方向**到*傳送*|  

> [!IMPORTANT]
>  如果協調流程包含雙向接收埠 （要求-回應），若要從 SAP 系統接收 Idoc，協調流程必須傳送回應給 SAP 系統。 否則，SAP 系統不會傳送下一步 的 IDOC。  

### <a name="adding-a-flat-file-assembler"></a>新增一般檔案組合器  
 您必須新增將內送的 IDOC 訊息轉換成一般檔案組合器。  

##### <a name="to-add-a-flat-file-assembler"></a>若要加入一般檔案組合器  

1.  以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後選取**新項目**。  

2.  從對話方塊中，執行下列作業：  

    |使用|以進行此動作|  
    |--------------|----------------|  
    |類別|管線檔案|  
    |Visual Studio 安裝的範本|傳送管線|  
    |[屬性]|SendIDOC|  

3.  這會開啟 「 管線設計師 」。 從**BizTalk 管線元件**工具箱，拖曳**一般檔案組合器**管線元件**組合**傳送管線階段。  

4.  從**管線元件屬性**檢視中，為指定值**文件結構描述**屬性。 從下拉式清單確定您選取的結構描述對應至 IDOC 接收作業。  

## <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>為動作圖形指定訊息，並連接到連接埠  
 下表指定之屬性和其值設為指定的動作圖形，並將它們連結至連接埠的訊息。 所列的名稱*圖形*資料行是訊息 圖形的名稱，上述協調流程中所示。  

|形狀圖|屬性|  
|-----------|----------------|  
|ListenToSAP|-設定**訊息**到*要求*<br /><br /> -設定**作業**到*ReceiveIDOCPort.ReceiveIDOC.Request*|  
|SaveIDOC|-設定**訊息**到*要求*<br /><br /> -設定**作業**到*GetIDOCPort.ReceiveIDOC.Request*|  
|SendResponse|-設定**訊息**到*回應*<br /><br /> -設定**作業**到*ReceiveIDOCPort.ReceiveIDOC.Response*|  

 您指定這些屬性之後，連線的訊息 圖形和連接埠和協調流程已完成。  

 您現在必須建置 BizTalk 方案，並將其部署至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱[建置和執行協調流程](../../core/building-and-running-orchestrations.md)

## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在下**協調流程**在 BizTalk Server 管理主控台 窗格。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 如需有關如何設定應用程式的詳細資訊，請參閱 <<c0> [ 如何設定應用程式](../../core/how-to-configure-an-application.md)。

 設定應用程式包含：  

- 選取應用程式主機。  

- 對應您在您在 BizTalk Server 管理主控台中的實體連接埠的協調流程中建立的連接埠。 此協調流程中，您必須：  

  - 定義傳送位置和實體傳送埠。 此位置會包含來自 SAP 系統的 Idoc。  

    > [!IMPORTANT]
    >  XMLTransmit 管線，請確定您選取***SendIDOC***。 您已建立此管線的 BizTalk 專案的一部分。  

  - 定義 WCF 自訂或 WCF SAP 接收埠。 此連接埠會接收來自 SAP 系統的輸入的 IDOC，並將它傳遞至協調流程。 此連接埠也會傳送到 SAP 系統的回應。 如需有關如何建立連接埠的資訊，請參閱 <<c0> [ 手動設定 SAP 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md)。

    > [!IMPORTANT]
    >  請確定繫結屬性**ReceiveIDocFormat**設為**具型別**。  
    > 
    > [!IMPORTANT]
    >  如果繫結屬性**EnableBizTalkCompatibilityMode**設定為 true，則請確定您新增 BizTalk 屬性結構描述 DLL 的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]為您的 BizTalk 應用程式，也就是所在的應用程式中的資源程式部署專案。 如需將資源加入所需的指示，請參閱[與 SAP 配接器疑難排解操作問題](../../adapters-and-accelerators/adapter-sap/troubleshoot-operational-issues-with-the-sap-adapter.md)。  
    > 
    > [!NOTE]
    >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠設定動作的相關資訊的繫結檔案。 您可以從 BizTalk 管理主控台來建立 （適用於輸出的呼叫） 的傳送埠或接收埠 （適用於輸入的呼叫），以匯入此繫結檔案。 如需詳細資訊，請參閱 <<c0> [ 設定的實體連接埠繫結使用的連接埠繫結檔案至 SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md)。

  您也必須在 BizTalk 應用程式中新增 IdocReceiveResponseMessageCreator 專案的組件。 您建立此專案以產生要傳送至 SAP 系統的回應。 若要這樣做：  

1.  BizTalk Server 管理主控台中，您匯入繫結，在 BizTalk 應用程式下的左側的主控台樹狀目錄中以滑鼠右鍵按一下**資源**，指向**新增**，然後按一下**BizTalk 組件**。  

2.  在 [**新增資源**] 對話方塊中，按一下**新增**並瀏覽至包含 IdocReceiveResponseMessageCreator.dll 的資料夾。 選取檔案，然後按一下**開啟**。  

3.  在 [**新增資源**] 對話方塊中，按一下**確定**。  

## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 BizTalk 應用程式，以便從 SAP 系統接收 IDOC。 如需有關啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)，或[如何啟動應用程式](../../core/how-to-start-and-stop-a-biztalk-application.md)。

 在這個階段，請確定：  

-   執行 FILE 傳送埠，以將內送的 IDOC 儲存至檔案位置  

-   WCF 自訂 」 或 「 WCF SAP 接收埠以接收 Idoc 從 SAP 系統正在執行。  

-   BizTalk 協調流程的作業正在執行。  

## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，您必須移 SAP 系統，並傳送 IDOC 到配接器。 配接器接收 IDOC，並將它儲存至檔案位置指定為協調流程的一部分。  

## <a name="possible-exceptions"></a>可能的例外狀況  
 如需從 SAP 系統，請使用 BizTalk Server 接收 IDOC 時可能發生的例外狀況資訊，請參閱[例外狀況和錯誤處理與 SAP 配接器](../../adapters-and-accelerators/adapter-sap/exceptions-and-error-handling-with-the-sap-adapter.md)。  

## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。 之後產生的繫結檔案時，您可以匯入的組態設定從檔案，讓您不需要建立傳送埠、 接收連接埠、 相同的協調流程等。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用 SAP 配接器繫結](../../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md)。

## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)