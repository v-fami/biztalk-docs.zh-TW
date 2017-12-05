---
title: "使用 BizTalk Server 從 SQL Server 接收輪詢基礎資料變更的訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9ecaf6f7-974b-4487-8c65-d1ab628cbfeb
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2251ec6f5019fab4eecff36ac35314183f9a7d61
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="receive-polling-based-data-changed-messages-from-sql-server-using-biztalk-server"></a>使用 BizTalk Server 從 SQL Server 接收輪詢基礎資料變更的訊息
您可以設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]接收 SQL Server 資料表或檢視表的週期性的資料變更訊息。 您可以指定執行以輪詢資料庫配接器的輪詢陳述式。 輪詢陳述式可以是 SELECT 陳述式或預存程序會傳回結果集。  

  
 如需有關如何配接器支援在輪詢的詳細資訊，請參閱[支援輪詢](https://msdn.microsoft.com/library/dd788416.aspx)。 輪詢作業的 SOAP 訊息結構的相關資訊，請參閱[輪詢和 TypedPolling 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-the-polling-and-typedpolling-operations.md)。  
  
> [!NOTE]
>  本主題示範如何使用**輪詢**輸入作業使用輪詢訊息。 輪詢作業的訊息不是強型別，以及在執行階段訊息擷取輪詢的物件結構描述。 如果您想要取得強型別輪詢訊息，您必須使用**TypedPolling**作業。 您也必須使用**TypedPolling**作業使用單一的 BizTalk 應用程式中的多個輪詢作業。 如需有關如何執行指示**TypedPolling**作業，請參閱[接收強型別輪詢基礎資料變更訊息從 SQL Server 使用 BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-strongly-typed-polling-based-data-changed-messages-from-sql-in-biztalk.md)。  
  
> [!IMPORTANT]
>  如果您想要在單一的 BizTalk 應用程式中有一個以上的輪詢作業，您必須指定**InboundID**一部分連線 URI 成為唯一的連接屬性。 使用一個唯一的連接 URI，您可以建立多個接收輪詢相同的資料庫或甚至相同資料庫的資料表中的連接埠。 如需詳細資訊，請參閱[收到輪詢訊息跨多個接收埠使用 BizTalk Server 的 sql](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk.md)。  
  
## <a name="how-this-topic-demonstrates-polling"></a>本主題示範輪詢的方式  
 本主題中，以示範如何[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]接收資料的支援變更訊息、 建立 BizTalk 專案和產生結構描述的**輪詢**作業。 如果您想要指定輪詢相關設計階段繫結屬性，指定**PolledDataAvailableStatement**為：  
  
```  
SELECT COUNT(*) FROM Employee  
```  
  
 **PolledDataAvailableStatement**必須傳回一個結果集包含正值的第一個儲存格。 如果第一個資料格不包含正值，配接器不會執行輪詢陳述式。  
  
 輪詢陳述式的一部分，執行下列作業：  
  
-   選取從 Employee 資料表的所有資料列。  
  
-   執行預存程序 (MOVE_EMP_DATA) 會將所有的記錄從 Employee 資料表 EmployeeHistory 資料表。  
  
-   執行預存程序 (ADD_EMP_DETAILS) Employee 資料表中加入新的記錄。 此程序會接受員工名稱、 指定和薪資做為參數。  
  
 若要執行這些作業，您必須指定下列**PollingStatement**繫結屬性：  
  
```  
SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000   
```  
  
 執行輪詢陳述式之後，選取從 Employee 資料表的所有記錄，則從 SQL Server 會捨棄訊息至接收位置。 一旦執行 MOVE_EMP_DATA 預存程序之後，配接器，所有的記錄會移至 EmployeeHistory 資料表。 然後，ADD_EMP_DETAILS 預存程序會執行以將新記錄新增至 Employee 資料表。 下次輪詢執行只會傳回單一記錄。 此週期會繼續執行，直到您停用接收輪詢 SQL Server 的連接埠。  
  
## <a name="configuring-a-polling-query-with-the-sql-adapter-binding-properties"></a>使用 SQL 配接器繫結屬性中設定輪詢查詢  
 下表摘要說明[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結，您用來設定配接器來接收資料變更訊息的屬性。 您必須同時設定接收埠中的指定這些繫結屬性[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
> [!NOTE]
>  您可以選擇指定這些繫結內容產生的結構描述時**輪詢**作業，即使它不是強制性。 如果您這樣做，連接埠繫結檔，[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生的中繼資料產生的組件也包含您指定的繫結屬性的值。 您可以稍後匯入此繫結檔案[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台建立 wcf-custom 或 WCF SQL 接收埠以繫結已設定的屬性。 如需有關如何建立使用該繫結檔案的連接埠的詳細資訊，請參閱[設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。  
  
|繫結屬性|Description|  
|---|---|  
|**InboundOperationType**|指定您是否要執行**輪詢**， **TypedPolling**，或**通知**輸入作業。 預設值是**輪詢**。|  
|**PolledDataAvailableStatement**|指定的 SQL 陳述式來判斷是否可用於輪詢的任何資料執行配接器。 SQL 陳述式必須傳回的結果集資料列和資料行所組成。 只有一個資料列是否可用，SQL 陳述式指定**PollingStatement**繫結屬性將會執行。|  
|**PollingIntervalInSeconds**|指定間隔，以秒為單位，此時[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]執行陳述式指定**PolledDataAvailableStatement**繫結屬性。 預設值是 30 秒。 輪詢間隔會決定後續輪詢間隔時間。 如果指定的間隔內執行的陳述式，則配接器就會等候剩餘的時間間隔中。|  
|**PollingStatement**|指定輪詢 SQL Server 資料庫資料表的 SQL 陳述式。 您可以指定簡單的 SELECT 陳述式或預存程序輪詢陳述式。 預設值是 null。 您必須指定的值**PollingStatement**來啟用輪詢。 輪詢陳述式在沒有進行輪詢，取決於可用的資料時，才會執行**PolledDataAvailableStatement**繫結屬性。 您可以指定任意數目的 SQL 陳述式以分號分隔。|  
|**PollWhileDataFound**|指定是否[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]忽略的輪詢間隔，並為指定的 SQL 陳述式會持續執行**PolledDataAvailableStatement**如果輪詢資料表中的資料可繫結屬性。 如果沒有資料可在資料表中，配接器會還原為執行 SQL 陳述式，在指定的輪詢間隔。 預設值是**false**。|  
  
 如需這些屬性的更完整說明，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。 如需完整的說明，如何使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]進一步來輪詢 SQL Server，請閱讀。  
  
## <a name="how-to-receive-data-change-messages-from-the-sql-server-database"></a>如何接收來自 SQL Server 資料庫的資料變更訊息  
 使用 SQL Server 資料庫上執行操作[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及程序中所述的工作[開發 BizTalk 應用程式與 SQL 配接器的建置組塊](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)。 若要設定要接收的資料變更訊息的介面卡，這些工作包括：  
  
1.  建立 BizTalk 專案，然後再產生結構描述的**輪詢**作業。 您可以選擇性地指定值**PolledDataAvailableStatement**和**PollingStatement**繫結屬性。  
  
2.  從 SQL Server 資料庫接收訊息的 BizTalk 專案中建立訊息。  
  
3.  建立協調流程接收訊息，從 SQL Server 資料庫，並將它們儲存到資料夾。  
  
4.  建置和部署 BizTalk 專案。  
  
5.  設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
    > [!IMPORTANT]
    >  輸入的輪詢案例對於您永遠必須設定單向的 WCF 自訂或 WCF SQL 接收埠。 雙向 Wcf-custom 或 WCF SQL 接收埠的輸入作業不支援。  
  
6.  啟動 BizTalk 應用程式。  
  
 本主題提供執行這些工作的指示。  
  
## <a name="generating-schema"></a>產生結構描述  
 您必須產生的結構描述**輪詢**作業。 請參閱[擷取中繼資料，使用 SQL 配接器的 Visual Studio 中的 SQL Server 作業的](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)如需有關如何產生結構描述。 產生結構描述時，請執行下列工作。 如果您不要指定繫結屬性在設計階段，請略過第一個步驟。  
  
1.  指定的值**PolledDataAvailableStatement**和**PollingStatement**時產生結構描述繫結屬性。 如需此繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
     如需有關如何指定繫結屬性的指示，請參閱[設定 SQL 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md)。  
  
2.  選取合約類型為**服務 （輸入作業）**。  
  
3.  產生結構描述的**輪詢**作業。  
  
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
    |識別碼|型別**接收**。|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*PollingQuery.Polling*，其中*PollingQuery*是您的 BizTalk 專案的名稱。 *輪詢*是針對產生的結構描述**輪詢**作業。|  
  
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
|ReceiveMessage|-設定**訊息**至*接收*<br /><br /> -設定**作業**至*SQLReceivePort.Polling.Request*|  
|SaveMessage|-設定**訊息**至*接收*<br /><br /> -設定**作業**至*SaveMessagePort.Polling.Request*|  
  
 您指定這些屬性之後，連接的訊息 圖形和連接埠，而且您的協調流程已完成。  
  
 您現在必須建置 BizTalk 方案，並部署到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱[建置和執行協調流程](../../core/building-and-running-orchestrations.md)。 
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 部署 BizTalk 專案之後，您稍早建立的協調流程會列在**協調流程**BizTalk Server 管理主控台 窗格。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 如需逐步解說，請參閱[逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。  
  
 設定應用程式包括：  
  
-   選取應用程式的主機。  
  
-   對應至 BizTalk Server 管理主控台中的實體連接埠在協調流程中建立的連接埠。 此協調流程中，您必須：  
  
    -   定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程會放置的位置將訊息從 SQL Server 資料庫。 這些訊息會在您指定的接收埠對輪詢陳述式。  
  
    -   定義實體的 WCF 自訂或 WCF-SQL 單向接收埠。 此連接埠輪詢 SQL Server 資料庫與您指定連接埠輪詢陳述式。 如需如何建立連接埠相關資訊，請參閱[手動設定 SQL 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)。 請確定指定接收埠的下列繫結屬性。  
  
        > [!IMPORTANT]
        >  您不需要執行這個步驟，如果您指定在設計階段的繫結屬性。 在此情況下，您可以建立 wcf-custom 或 WCF SQL 接收埠，設定必要的繫結屬性，藉由匯入所建立之繫結檔案[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 如需詳細資訊，請參閱[設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。  
  
        |繫結屬性|值|  
        |----------------------|-----------|  
        |**InboundOperationType**|請確定您設定為**輪詢**。|  
        |**PolledDataAvailableStatement**|請確定您指定 SQL 陳述式。 本主題中，指定：<br /><br /> `SELECT COUNT(*) FROM Employee`|  
        |**PollingStatement**|請確定您指定輪詢陳述式。 本主題中，指定：<br /><br /> `SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000`|  
  
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
  
-   配接器執行輪詢陳述式。 輪詢陳述式包含 SELECT 陳述式和預存程序，因為配接器的其他之後不會執行所有陳述式一個。  
  
    -   配接器會先執行 SELECT 陳述式會傳回 Employee 資料表中的所有記錄。  
  
    -   然後執行 MOVE_EMP_DATA 預存程序，會從 Employee 資料表的所有資料都移至 EmployeeHistory 資料表配接器。 這個預存程序沒有傳回任何值。  
  
    -   然後執行配接器加入 Employee 資料表中的一筆記錄的 ADD_EMP_DETAILS 預存程序。 這個預存程序傳回的員工識別碼插入記錄。  
  
     因此，從 SQL Server 收到的訊息將包含多個結果集 （如 SELECT 陳述式以及 ADD_EMP_DETAILS 預存程序），並將如下所示：  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <Polling xmlns="http://schemas.microsoft.com/Sql/2008/05/Polling/">  
      <PolledData>  
        <DataSet xmlns="http://schemas.datacontract.org/2004/07/System.Data">  
          <xs:schema id="NewDataSet" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
            <xs:element msdata:IsDataSet="true" name="NewDataSet">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element minOccurs="0" maxOccurs="unbounded" name="NewTable">  
                    <xs:complexType>  
                      <xs:sequence>  
                        <xs:element minOccurs="0" name="Employee_ID" type="xs:int" />   
                        <xs:element minOccurs="0" name="Name" type="xs:string" />   
                        <xs:element minOccurs="0" name="DOJ" type="xs:dateTime" />   
                        <xs:element minOccurs="0" name="Designation" type="xs:string" />   
                        <xs:element minOccurs="0" name="Job_Description" type="xs:string" />   
                        <xs:element minOccurs="0" name="Photo" type="xs:base64Binary" />   
                        <xs:element minOccurs="0" name="Rating" type="xs:string" />   
                        <xs:element minOccurs="0" name="Salary" type="xs:decimal" />   
                        <xs:element minOccurs="0" name="Last_Modified" type="xs:base64Binary" />   
                      </xs:sequence>  
                    </xs:complexType>  
                  </xs:element>  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:schema>  
          <diffgr:diffgram xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
            <NewDataSet xmlns="">  
              <NewTable>  
                <Employee_ID>10001</Employee_ID>   
                <Name>John</Name>   
                <Designation>Tester</Designation>   
                <Salary>100000.00</Salary>   
                <Last_Modified>AAAAAAAAF34=</Last_Modified>   
              </NewTable>  
              ........  
              ........  
              <NewTable>  
                <Employee_ID>10005</Employee_ID>   
                <Name>Wilson</Name>   
                <Designation>Tester3</Designation>   
                <Salary>100000.00</Salary>   
                <Last_Modified>AAAAAAAAF4E=</Last_Modified>   
              </NewTable>  
            </NewDataSet>  
          </diffgr:diffgram>  
        </DataSet>  
        <DataSet xmlns="http://schemas.datacontract.org/2004/07/System.Data">  
          <xs:schema id="NewDataSet" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
            <xs:element msdata:IsDataSet="true" name="NewDataSet">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element minOccurs="0" maxOccurs="unbounded" name="NewTable">  
                    <xs:complexType>  
                      <xs:sequence>  
                        <xs:element minOccurs="0" name="Employee_ID" type="xs:int" />   
                      </xs:sequence>  
                    </xs:complexType>  
                  </xs:element>  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:schema>  
          <diffgr:diffgram xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
            <NewDataSet xmlns="">  
              <NewTable>  
                <Employee_ID>10006</Employee_ID>  
              </NewTable>  
            </NewDataSet>  
          </diffgr:diffgram>  
        </DataSet>  
      </PolledData>  
    </Polling>  
    ```  
  
     上述的回應包含兩個資料集。 第一個資料集包含 SELECT 陳述式的回應。 SELECT 陳述式選取 Employee 資料表中的所有記錄。 第二個資料集是 ADD_EMP_DETAILS 預存程序。 這個預存程序會將記錄加入 Employee 資料表，並傳回新的記錄的員工識別碼。  
  
    > [!NOTE]
    >  MOVE_EMP_DATA 預存程序不會傳回結果集。 因此，回應訊息中沒有任何對應的資料集。  
  
-   當配接器執行**PollDataAvailableStatement**同樣地，它會尋找一筆記錄 ADD_EMP_DETAILS 所插入的預存程序。 然後執行所有三個陳述式所指定的配接器**PollingStatement**繫結屬性。 這次會從 SQL Server 的回應包含 SELECT 陳述式只有一項記錄，並且 ADD_EMP_DETAILS 的一筆記錄的預存程序。 所有後續輪詢會傳回類似的回應。  
  
> [!NOTE]
>  [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]將繼續輪詢直到您明確地停用接收埠從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。 一旦產生繫結檔案時，可以組態設定匯入檔案，使您不需要建立傳送埠和接收相同的協調流程連接埠。 如需繫結檔案的詳細資訊，請參閱[重複使用配接器繫結](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md)。
  
## <a name="see-also"></a>請參閱  
 [與 BizTalk Server 使用 SQL 配接器的輪詢 SQL Server](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-biztalk-server.md)