---
title: "接收使用 FOR XML 子句中使用 BizTalk Server 的 SQL SELECT 陳述式的輪詢訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65c629c1-9ef7-4aa1-8ec1-f94a3cb41cb0
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77ac34fb06497f72b778592b3ce4c927b0ca3a07
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="receive-polling-messages-using-select-statements-with-for-xml-clause-from-sql-using-biztalk-server"></a>接收輪詢訊息使用 FOR XML 子句中使用 BizTalk Server 的 SQL SELECT 陳述式
您可以設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]接收使用 SELECT 陳述式或包含 FOR XML 子句的預存程序的 SQL Server 資料表或檢視表的週期性的資料變更訊息。 您可以指定這些陳述式與執行以輪詢資料庫配接器的輪詢陳述式。 輪詢陳述式可以是 SELECT 陳述式或預存程序會傳回結果集。  
  
 如需有關如何配接器支援在輪詢的詳細資訊，請參閱[支援輪詢](https://msdn.microsoft.com/library/dd788416.aspx)。 輪詢作業的 SOAP 訊息結構的相關資訊，請參閱[輪詢和 TypedPolling 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-the-polling-and-typedpolling-operations.md)。 SQL [FOR XML 子句](https://docs.microsoft.com/sql/relational-databases/xml/for-xml-sql-server)提供更多詳細資料。
  
> [!NOTE]
>  本主題示範如何使用**XmlPolling**輸入接收輪詢訊息的作業。 **XmlPolling**作業用來輪詢使用 SELECT 陳述式或包含 FOR XML 子句的預存程序的 SQL Server 資料庫。 針對訊息**XmlPolling**作業包含在 SQL Server Management Studio 中執行 SELECT 陳述式或預存程序接收的 xml 訊息。  
>   
>  您也可以使用配接器接收不同類型的輪詢訊息。  
>   
>  -   如果您想要收到弱型別輪詢的訊息，您必須使用輪詢作業。 如需詳細資訊，請參閱[從 SQL Server 所使用的 BizTalk Server 收到輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-biztalk.md)。  
> -   如果您想要取得強型別輪詢訊息，您必須使用**TypedPolling**作業。 您也必須使用**TypedPolling**作業使用單一的 BizTalk 應用程式中的多個輪詢作業。 如需有關如何執行指示**TypedPolling**作業，請參閱[接收強型別輪詢基礎資料變更訊息使用 BizTalk Server 從 SQL Server](../../adapters-and-accelerators/adapter-sql/receive-strongly-typed-polling-based-data-changed-messages-from-sql-in-biztalk.md)。  
  
> [!IMPORTANT]
>  如果您想要在單一的 BizTalk 應用程式中有一個以上的輪詢作業，您必須指定**InboundID**一部分連線 URI 成為唯一的連接屬性。 使用一個唯一的連接 URI，您可以建立多個接收輪詢相同的資料庫或甚至相同資料庫的資料表中的連接埠。 如需詳細資訊，請參閱[收到輪詢訊息跨多個接收埠使用 BizTalk Server 的 sql](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk.md)。  
  
## <a name="how-this-topic-demonstrates-polling"></a>本主題示範輪詢的方式  
 本主題中，以示範如何[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]支援接收資料變更訊息中，我們使用含有 FOR XML 子句的 SELECT 陳述式來輪詢 SQL Server 資料庫。 當您叫用 SQL Server Management Studio 中的這類的陳述式時，輸出為 xml 訊息的格式。 若要使用這類陳述式來輪詢 SQL Server 資料庫，您必須回應 xml 訊息結構描述。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]需要來執行 FOR XML 子句的 SELECT 陳述式之後收到輪詢此結構描述。 因此，若要使用 FOR XML 子句的 SELECT 陳述式來輪詢 SQL Server 資料庫，您必須執行下列工作集合。  
  
1.  產生含有 FOR XML 子句的 SELECT 陳述式的 XML 回應訊息的結構描述。  
  
2.  建立 BizTalk 專案，並將產生的結構描述加入至專案。  
  
3.  接收來自 SQL Server 資料庫的 XML 回應訊息的 BizTalk 專案中建立訊息。  
  
4.  建立協調流程接收訊息，從 SQL Server 資料庫，並將它們儲存到資料夾。  
  
5.  建置和部署 BizTalk 專案。  
  
6.  設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
    > [!IMPORTANT]
    >  輸入的輪詢案例對於您永遠必須設定單向的 WCF 自訂或 WCF SQL 接收埠。 雙向 Wcf-custom 或 WCF SQL 接收埠的輸入作業不支援。  
  
7.  啟動 BizTalk 應用程式。  
  
##  <a name="BKMK_RespSchema"></a>產生回應訊息的結構描述的 SELECT 陳述式  
 您可以產生 SELECT 陳述式的回應訊息的結構描述包括`xmlschema`子句搭配`for xml`子句。 在本主題中，我們可以使用 SELECT 陳述式擷取給定的員工識別碼的員工詳細資料 若要擷取之結構描述執行 SELECT 陳述式，SELECT 陳述式必須以下列方式撰寫：  
  
```  
SELECT Employee_ID ,Name ,Designation FROM Employee for xml auto, xmlschema  
```  
  
 執行這個 SELECT 陳述式來取得回應訊息的結構描述。 儲存結構描述。 您現在必須建立 BizTalk 專案中的[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]並將此結構描述加入至專案。 針對此範例中，您可以命名此結構描述為**PollingResponse.xsd**。  
  
> [!IMPORTANT]
>  請確定您移除`xmlschema`子句之後產生結構描述的 SELECT 陳述式執行。 如果您無法這樣做，請在最後執行的 SELECT 陳述式透過 BizTalk XmlPolling 作業的一部分時，您將回應訊息中，重新產生結構描述。 因此，為了取得回應訊息為 xml，您必須移除`xmlschema`子句。  
  
#### <a name="to-add-the-schema-to-a-biztalk-project"></a>若要將結構描述加入 BizTalk 專案  
  
1.  建立 BizTalk 專案中的[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。  
  
2.  加入您的 BizTalk 專案的預存程序所產生的回應結構描述。 以滑鼠右鍵按一下 方案總管 中的 BizTalk 專案，指向**新增**，然後按一下 **現有項目**。 在 [加入現有項目] 對話方塊中，瀏覽至您儲存的結構描述和按一下位置**新增**。  
  
3.  開啟中的結構描述[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]並進行下列變更。  
  
    1.  將節點加入至結構描述，並移動現有的根節點，在這個新加入的節點。 為指定的根節點的名稱。 本主題中，重新命名的根節點**根**。  
  
    2.  SELECT 陳述式所產生的回應結構描述參考 sqltypes.xsd。 您可以取得 sqltypes.xsd 結構描述從[http://go.microsoft.com/fwlink/p/?LinkId=131087](http://go.microsoft.com/fwlink/p/?LinkId=131087)。 Sqltypes.xsd 結構描述加入 BizTalk 專案。  
  
    3.  在 SELECT 陳述式所產生的結構描述，將值變更`import schemaLocation`下。  
  
        ```  
        import schemaLocation=”sqltypes.xsd”  
        ```  
  
         因為您已加入至您的 BizTalk 專案 sqltypes.xsd 結構描述，您可以這麼做。  
  
    4.  提供結構描述目標命名空間。 按一下**\<結構描述 >**  節點，並在 屬性 窗格中，指定的命名空間中**目標命名空間**屬性。 本主題中，為提供的命名空間為`http://ForXmlPolling/namespace`。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您先前產生的結構描述會描述 「 類型 」 所需的協調流程中的訊息。 訊息通常是為其型別由對應的結構描述所定義的變數。 一旦產生結構描述時，您必須訊息連結之協調流程檢視中的 BizTalk 專案。  
  
 本主題中，您必須建立一個從 SQL Server 資料庫接收訊息的訊息。  
  
 執行下列步驟來建立訊息，並將它們連結至結構描述。  
  
#### <a name="to-create-messages-and-link-to-schema"></a>建立訊息，以及連結至結構描述  
  
1.  BizTalk 專案中新增協調流程。 從 方案總管 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下 **新項目**。 輸入 BizTalk 協調流程的名稱，然後按一下**新增**。  
  
2.  如果它尚未開啟，請開啟 BizTalk 專案中，[協調流程檢視] 視窗。 按一下**檢視**，指向 **其他視窗**，然後按一下 **協調流程檢視**。  
  
3.  在**協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。  
  
4.  以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。  
  
5.  在**屬性**窗格**Message_1**，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|型別**PollingMessage**。|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*ForXMLPolling.PollingResponse*，其中*ForXMLPolling*是您的 BizTalk 專案的名稱。 *PollingResponse*是藉由執行 SELECT 陳述式，如底下所述產生的回應結構描述名稱[接收使用 FOR XML 子句中使用 BizTalk Server 的 SQL SELECT 陳述式的輪詢訊息](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-using-select-with-for-xml-clause-with-the-sql-adapter.md)。|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]接收訊息以輪詢為基礎的資料變更從 SQL Server 資料庫。 在此協調流程中，配接器接收的 select 陳述式指定的回應**PollingStatement**繫結屬性。 SELECT 陳述式的回應會儲存到檔案位置。 用於輪詢 SQL Server 資料庫的一般協調流程就會包含：  
  
-   接收和傳送圖形，從 SQL Server 接收訊息，並分別將傳送至檔案連接埠。  
  
-   單向接收埠以接收來自 SQL Server 訊息。  
  
    > [!IMPORTANT]
    >  輸入的輪詢案例，您必須一律先設定單向接收埠。 雙向接收埠不支援的輸入操作。  
  
-   單向傳送埠以傳送輪詢回應從 SQL Server 資料庫，到資料夾。  
  
 範例協調流程如下。  
  
 ![用於輪詢 SQL Server 資料庫的協調流程](../../adapters-and-accelerators/adapter-sql/media/5cf65d53-d70d-444d-82f7-2561efcd9ee4.gif "5cf65d53-d70d-444d-82f7-2561efcd9ee4")  
  
### <a name="adding-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息圖形指定下列屬性。 圖形資料行中所列的名稱是訊息 圖形的名稱，為顯示在剛才提及的協調流程中。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveMessage|Receive|-設定**名稱**至*ReceiveMessage*<br /><br /> -設定**啟動**至*，則為 True*|  
|SaveMessage|Send|-設定**名稱**至*SaveMessage*|  
  
### <a name="adding-ports"></a>新增連接埠  
 請確定您針對每個邏輯連接埠指定下列屬性。 連接埠資料行中所列的名稱是連接埠的名稱，為顯示協調流程中。  
  
|通訊埠|屬性|  
|----------|----------------|  
|SQLReceivePort|-設定**識別碼**至*SQLReceivePort*<br /><br /> -設定**類型**至*SQLReceivePortType*<br /><br /> -設定**通訊模式**至*單向*<br /><br /> -設定**通訊方向**至*接收*|  
|SaveMessagePort|-設定**識別碼**至*SaveMessagePort*<br /><br /> -設定**類型**至*SaveMessagePortType*<br /><br /> -設定**通訊模式**至*單向*<br /><br /> -設定**通訊方向**至*傳送*|  
  
### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>指定動作圖形訊息並連接至連接埠  
 下表指定屬性和其值，您應該設定來指定動作圖形的訊息，以及連結至連接埠的訊息。 圖形資料行中所列的名稱是 「 訊息 」 圖形的名稱，為顯示在協調流程中先前所述。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveMessage|-設定**訊息**至*接收*<br /><br /> -設定**作業**至*SQLReceivePort.XmlPolling.Request*|  
|SaveMessage|-設定**訊息**至*接收*<br /><br /> -設定**作業**至*SaveMessagePort.XmlPolling.Request*|  
  
 您指定這些屬性之後，連接的訊息 圖形和連接埠，而且您的協調流程已完成。  
  
 您現在必須建置 BizTalk 方案，並部署到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱[建置和執行協調流程](../../core/building-and-running-orchestrations.md)。
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 部署 BizTalk 專案之後，您稍早建立的協調流程會列在**協調流程**BizTalk Server 管理主控台 窗格。 您必須使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定應用程式。 如需逐步解說，請參閱[逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。
  
 設定應用程式包括：  
  
-   選取應用程式的主機。  
  
-   對應至 BizTalk Server 管理主控台中的實體連接埠在協調流程中建立的連接埠。 此協調流程中，您必須：  
  
    -   定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程會放置的位置將訊息從 SQL Server 資料庫。 這些訊息會在您指定的接收埠對輪詢陳述式。  
  
    -   定義實體的 WCF 自訂或 WCF-SQL 單向接收埠。 此連接埠輪詢 SQL Server 資料庫與您指定連接埠輪詢陳述式。 如需如何建立連接埠相關資訊，請參閱[手動設定 SQL 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)。 請確定指定接收埠的下列繫結屬性。  
  
        > [!IMPORTANT]
        >  您不需要執行這個步驟，如果您指定在設計階段的繫結屬性。 在此情況下，您可以建立 wcf-custom 或 WCF SQL 接收埠，設定必要的繫結屬性，藉由匯入所建立之繫結檔案[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 如需詳細資訊，請參閱[設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。  
  
        |繫結屬性|值|  
        |----------------------|-----------|  
        |**InboundOperationType**|請確定您設定為**XmlPolling**。|  
        |**PolledDataAvailableStatement**|請確定您指定 SQL 陳述式。 本主題中，指定：<br /><br /> `SELECT COUNT(*) FROM Employee`|  
        |**PollingStatement**|請確定您提供相同的陳述式，而不`xmlschema`子句，您指定在產生結構描述中所述[接收輪詢訊息使用 FOR XML 子句中使用 BizTalk ServerSQLSELECT陳述式](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-using-select-with-for-xml-clause-with-the-sql-adapter.md).<br /><br /> `SELECT Employee_ID ,Name ,Designation FROM Employee for xml auto`<br /><br /> **注意：**請注意，SELECT 陳述式不包含`xmlschema`子句。|  
        |**XmlStoredProcedureRootNodeName**|指定的根節點底下所述，您加入至您的 SELECT 陳述式中，所產生的回應結構描述名稱[產生回應訊息的 SELECT 陳述式的結構描述](#BKMK_RespSchema)。 如本主題中，將此設**根**。|  
        |**XmlStoredProcedureRootNodeNamespace**|指定您的 SELECT 陳述式中，所產生的回應結構描述的目標命名空間，如底下所述[產生回應訊息的 SELECT 陳述式的結構描述](#BKMK_RespSchema)。 如本主題中，將此設`http://ForXmlPolling/namespace`。|  
  
         如需不同的繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
        > [!NOTE]
        >  我們建議您執行使用的輸入的操作時設定的交易隔離等級和異動逾時[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 您可以執行新增服務行為設定 Wcf-custom 或 WCF-SQL 時接收埠。 如需如何新增服務行為的指示，請參閱[設定交易隔離等級和交易逾時，使用 SQL](../../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md)。  
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 SQL Server 資料庫從接收訊息的 BizTalk 應用程式。 如需啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。
  
 在這個階段，請確定：  
  
-   Wcf-custom 或 WCF-SQL 單向接收埠，會使用指定的陳述式的 SQL Server 資料庫的輪詢**PollingStatement**繫結屬性，正在執行。  
  
-   FILE 傳送埠，從 SQL Server 所接收訊息，正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，執行下列一進行，以相同順序：  
  
-   執行配接器**PolledDataAvailableStatement** employee 資料表，並判斷資料表是否有記錄進行輪詢。  
  
-   配接器執行輪詢陳述式，並收到來自 SQL Server 資料庫輪詢訊息。 輪詢陳述式包含 FOR XML 子句的 SELECT 陳述式，因為接收配接器的輪詢訊息如下所示：  
  
    ```  
    \<?xml version="1.0" encoding="utf-8" ?>   
    <Root xmlns="http://ForXmlPolling/namespace">  
      <Employee Employee_ID="10765" Name="John" Designation="Tester" xmlns="" />   
      <Employee Employee_ID="10766" Name="Sam" Designation="Manager" xmlns="" />   
      .....  
      .....  
    </Root>  
    ```  
  
     請注意，輪詢接收到訊息中相同的結構描述所執行 SELECT 陳述式，以產生**xmlschema**子句。 也請注意，根節點和命名空間是您指定的值為相同**XmlStoredProcedureRootNodeName**和**XmlStoredProcedureRootNodeNamespace**分別繫結屬性。  
  
> [!NOTE]
>  [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]將繼續輪詢直到您明確地停用接收埠從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。 一旦產生繫結檔案時，可以組態設定匯入檔案，使您不需要建立傳送埠和接收相同的協調流程連接埠。 如需繫結檔案的詳細資訊，請參閱[重複使用配接器繫結](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md)。
  
## <a name="see-also"></a>另請參閱  
 [輪詢 SQL Server 與 BizTalk Server 使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-biztalk-server.md)