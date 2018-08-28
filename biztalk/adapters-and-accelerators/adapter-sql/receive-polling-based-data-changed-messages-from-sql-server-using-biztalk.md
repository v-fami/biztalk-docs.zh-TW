---
title: 使用 BizTalk Server 從 SQL Server 接收以輪詢為基礎的資料變更訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ecaf6f7-974b-4487-8c65-d1ab628cbfeb
caps.latest.revision: 26
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 168a7421aee7a33f1f400815153f5f217bb914b8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972887"
---
# <a name="receive-polling-based-data-changed-messages-from-sql-server-using-biztalk-server"></a>使用 BizTalk Server 從 SQL Server 接收以輪詢為基礎的資料變更訊息
您可以設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]接收 SQL Server 資料表或檢視表的定期的資料變更訊息。 您可以指定要輪詢的資料庫執行的配接器的輪詢陳述式。 輪詢陳述式可以是 SELECT 陳述式或預存程序會傳回結果集。  

  
 如需有關配接器如何支援輪詢的詳細資訊，請參閱[輪詢支援](https://msdn.microsoft.com/library/dd788416.aspx)。 輪詢作業的 SOAP 訊息結構的相關資訊，請參閱[輪詢和 TypedPolling 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-the-polling-and-typedpolling-operations.md)。  
  
> [!NOTE]
>  本主題示範如何使用**輪詢**輸入作業使用輪詢訊息。 輪詢作業的訊息不是強型別和輪詢的物件的結構描述會同時在執行階段訊息擷取。 如果您想要取得強型別輪詢訊息時，您必須使用**TypedPolling**作業。 您也必須使用**TypedPolling**單一的 BizTalk 應用程式中有多個輪詢作業的作業。 如需有關如何執行**TypedPolling**作業，請參閱[接收強型別輪詢為基礎的資料變更訊息從 SQL Server 使用 BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-strongly-typed-polling-based-data-changed-messages-from-sql-in-biztalk.md)。  
  
> [!IMPORTANT]
>  如果您想要在單一的 BizTalk 應用程式中有一個以上的輪詢作業，您必須指定**InboundID**一部分的連線 URI，使其成為唯一的連接屬性。 使用唯一連線 URI，您可以建立多個接收輪詢相同的資料庫或甚至是相同的資料表在資料庫中的連接埠。 如需詳細資訊，請參閱 <<c0> [ 接收輪詢訊息跨多個接收埠從使用 BizTalk Server 的 SQL](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk.md)。  
  
## <a name="how-this-topic-demonstrates-polling"></a>本主題將輪詢的示範  
 本主題中，以示範如何[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]支援的接收資料變更訊息、 建立 BizTalk 專案，並產生結構描述**輪詢**作業。 如果您想要指定輪詢相關的設計階段的繫結屬性，指定**PolledDataAvailableStatement**為：  
  
```  
SELECT COUNT(*) FROM Employee  
```  
  
 **PolledDataAvailableStatement**必須傳回含有包含正值的第一個儲存格的結果集。 如果第一個資料格不包含正值，配接器不會執行輪詢陳述式。  
  
 輪詢陳述式的一部分，執行下列作業：  
  
- 從 [員工] 資料表中選取所有資料列。  
  
- 執行預存程序 (MOVE_EMP_DATA) 將從 Employee 資料表的所有記錄都移至 EmployeeHistory 資料表。  
  
- 執行預存程序 (ADD_EMP_DETAILS)，將新記錄新增至 [員工] 資料表。 此程序會接受員工名稱、 指定和薪資做為參數。  
  
  若要執行這些作業，您必須指定下列**PollingStatement**繫結屬性：  
  
```  
SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000   
```  
  
 執行輪詢陳述式之後，選取從 Employee 資料表的所有記錄，並從 SQL Server 訊息拖曳至接收位置。 一旦由配接器執行 MOVE_EMP_DATA 預存程序之後，所有的記錄會移至 EmployeeHistory 資料表中。 然後，會執行 ADD_EMP_DETAILS 預存程序，將新記錄新增至 [員工] 資料表。 下一個輪詢執行只會傳回單一記錄。 此週期會持續下去，直到您停用接收輪詢 SQL Server 的連接埠。  
  
## <a name="configuring-a-polling-query-with-the-sql-adapter-binding-properties"></a>使用 SQL 配接器繫結屬性中設定輪詢查詢  
 下表摘要說明[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結屬性，您用來設定配接器接收資料變更訊息。 您必須在設定接收埠中的指定這些繫結屬性[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
> [!NOTE]
>  您也可以指定這些繫結屬性，產生的結構描述時**輪詢**作業，即使它不是強制性。 如果您這樣做時，連接埠繫結檔案[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生的中繼資料產生的組件也包含您指定的繫結屬性的值。 您可以稍後匯入此繫結檔案中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 WCF 自訂或 WCF-SQL 與繫結屬性已設定接收埠。 如需建立使用該繫結檔案的連接埠的詳細資訊，請參閱 <<c0> [ 設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。  
  
|         繫結屬性         |                                                                                                                                                                                                                                         描述                                                                                                                                                                                                                                          |
|----------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     **InboundOperationType**     |                                                                                                                                                                             指定是否要執行**輪詢**， **TypedPolling**，或**通知**輸入作業。 預設值是**輪詢**。                                                                                                                                                                              |
| **PolledDataAvailableStatement** |                                                                                       指定配接器執行，以判斷是否有任何資料可供輪詢 SQL 陳述式。 SQL 陳述式必須傳回的結果集資料列和資料行所組成。 如果可用的資料列，為指定的 SQL 陳述式僅**PollingStatement**屬性繫結將會執行。                                                                                       |
|   **PollingIntervalInSeconds**   |                         指定間隔 （秒），此時[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]執行陳述式指定**PolledDataAvailableStatement**繫結屬性。 預設值是 30 秒。 輪詢間隔會決定後續輪詢間隔的時間間隔。 如果指定的間隔內執行的陳述式，則配接器會等候剩餘的時間間隔中。                          |
|       **PollingStatement**       | 指定輪詢 SQL Server 資料庫資料表的 SQL 陳述式。 您可以指定簡單的 SELECT 陳述式或輪詢陳述式的預存程序。 預設值是 null。 您必須指定的值**PollingStatement**啟用輪詢。 輪詢陳述式在沒有可供輪詢，取決於使用的資料時，才會執行**PolledDataAvailableStatement**繫結屬性。 您可以指定任意數目的 SQL 陳述式以分號分隔。 |
|      **PollWhileDataFound**      |                            指定是否[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]忽略的輪詢間隔，並持續執行 SQL 陳述式指定**PolledDataAvailableStatement**繫結屬性，如果資料可在所輪詢的資料表。 如果沒有資料可在資料表中，配接器會還原為執行 SQL 陳述式，在指定的輪詢間隔。 預設值是**false**。                             |
  
 如需這些屬性的更完整說明，請參閱[了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。 如需完整的說明，如何使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]輪詢 SQL Server，可深入閱讀。  
  
## <a name="how-to-receive-data-change-messages-from-the-sql-server-database"></a>如何從 SQL Server 資料庫中接收資料變更訊息  
 執行 SQL Server 資料庫使用運算[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[開發使用 SQL 配接器的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)。 若要設定要接收資料變更訊息的介面卡，這些工作如下：  
  
1. 建立 BizTalk 專案，然後再產生結構描述**輪詢**作業。 您可以選擇性地指定值**PolledDataAvailableStatement**並**PollingStatement**繫結屬性。  
  
2. 從 SQL Server 資料庫接收訊息的 BizTalk 專案中建立訊息。  
  
3. 建立協調流程接收的 SQL Server 資料庫中的訊息，並將它們儲存到資料夾。  
  
4. 建置和部署 BizTalk 專案。  
  
5. 設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
   > [!IMPORTANT]
   >  輸入的輪詢案例一律必須設定單向的 WCF 自訂或 WCF SQL 接收埠。 雙向 WCF 自訂] 或 [WCF-SQL 接收埠不支援的輸入作業。  
  
6. 啟動 BizTalk 應用程式。  
  
   本主題提供執行這些工作的指示。  
  
## <a name="generating-schema"></a>產生結構描述  
 您必須產生的結構描述**輪詢**作業。 請參閱[擷取使用 SQL 配接器的 Visual Studio 中的 SQL Server 作業的中繼資料](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)如需有關如何產生結構描述。 產生結構描述時，請執行下列工作。 如果您不想指定在設計階段的繫結屬性，請略過第一個步驟。  
  
1.  指定的值**PolledDataAvailableStatement**並**PollingStatement**時產生結構描述繫結屬性。 如需有關這個繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
     如需有關如何指定繫結屬性的指示，請參閱 <<c0> [ 設定 SQL 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md)。  
  
2.  選取合約類型作為**服務 （輸入作業）**。  
  
3.  產生結構描述**輪詢**作業。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您稍早產生的結構描述會描述協調流程中的訊息所需的 「 類型 」。 訊息通常是一個變數，要為其類型會定義對應的結構。 一旦產生結構描述時，您必須訊息從 BizTalk 專案的協調流程檢視以將它的連結。  
  
 本主題中，您必須建立一則訊息來接收 SQL Server 資料庫中的訊息。  
  
 執行下列步驟來建立訊息，並將它們連結至結構描述。  
  
#### <a name="to-create-messages-and-link-to-schema"></a>若要建立訊息，並連結至結構描述  
  
1.  BizTalk 專案中新增協調流程。 從 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下**新項目**。 輸入 BizTalk 協調流程的名稱，然後按一下**新增**。  
  
2.  如果它尚未開啟，請開啟 BizTalk 專案中，[協調流程檢視] 視窗。 按一下 **檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。  
  
3.  在 **協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。  
  
4.  以滑鼠右鍵按一下新建立的訊息，然後按**屬性 視窗**。  
  
5.  在 [**屬性**] 窗格**Message_1**，執行下列動作：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|型別**接收**。|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*PollingQuery.Polling*，其中*PollingQuery*是 BizTalk 專案的名稱。 *輪詢*是針對產生的結構描述**輪詢**作業。|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]接收以輪詢為基礎的資料變更訊息從 SQL Server 資料庫。 在此協調流程中，配接器接收的 select 陳述式指定的回應**PollingStatement**繫結屬性。 SELECT 陳述式的回應會儲存至檔案位置。 用於輪詢 SQL Server 資料庫的一般協調流程會包含：  
  
- 接收和傳送圖形，從 SQL Server 接收訊息，並分別將傳送至檔案連接埠。  
  
- 單向接收埠以接收來自 SQL Server 的訊息。  
  
  > [!IMPORTANT]
  >  輸入的輪詢案例，您必須一律設定為單向接收埠。 雙向接收埠不支援的輸入作業。  
  
- 單向傳送埠以將輪詢回應從 SQL Server 資料庫傳送到資料夾。  
  
  範例協調流程如下所示。  
  
  ![用於輪詢 SQL Server 資料庫的協調流程](../../adapters-and-accelerators/adapter-sql/media/5cf65d53-d70d-444d-82f7-2561efcd9ee4.gif "5cf65d53-d70d-444d-82f7-2561efcd9ee4")  
  
### <a name="adding-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息 圖形中指定下列屬性。 剛剛提到的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveMessage|Receive|-設定**名稱**到*ReceiveMessage*<br /><br /> -設定**啟用**到 *，則為 True*|  
|SaveMessage|Send|輪詢間隔後，執行配接器再次**PolledDataAvailableStatement**。*|  
  
### <a name="adding-ports"></a>新增連接埠  
 請確定您針對每個邏輯連接埠中指定下列屬性。 協調流程中所示，連接埠資料行中所列的名稱會是連接埠的名稱。  
  
|通訊埠|屬性|  
|----------|----------------|  
|SQLReceivePort|-設定**識別碼**到*SQLReceivePort*<br /><br /> -設定**型別**到*SQLReceivePortType*<br /><br /> -設定**通訊模式**到*單向*<br /><br /> -設定**通訊方向**到*接收*|  
|SaveMessagePort|-設定**識別碼**到*SaveMessagePort*<br /><br /> -設定**型別**到*SaveMessagePortType*<br /><br /> -設定**通訊模式**到*單向*<br /><br /> -設定**通訊方向**到*傳送*|  
  
### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>為動作圖形指定訊息，並連接到連接埠  
 下表指定的屬性和屬性來指定動作圖形的訊息，以及連結至連接埠的訊息，您應該設定的值。 先前所述的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveMessage|若要插入多筆記錄，您可以執行 more_activity_data.sql 指令碼提供範例。*<br /><br /> -設定**作業**到*SQLReceivePort.Polling.Request*|  
|SaveMessage|若要插入多筆記錄，您可以執行 more_activity_data.sql 指令碼提供範例。*<br /><br /> 如此一來，配接器執行輪詢陳述式，並再次接收配接器用戶端的輪詢訊息。*|  
  
 您指定這些屬性之後，連線的訊息 圖形和連接埠和協調流程已完成。  
  
 您現在必須建置 BizTalk 方案，並將其部署至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 建置和執行協調流程](../../core/building-and-running-orchestrations.md)。 
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在下**協調流程**在 BizTalk Server 管理主控台 窗格。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 如需逐步解說，請參閱 <<c0> [ 逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。  
  
 設定應用程式包含：  
  
- 選取應用程式主機。  
  
- 對應您在您在 BizTalk Server 管理主控台中的實體連接埠的協調流程中建立的連接埠。 此協調流程中，您必須：  
  
  - 硬碟和對應的檔案連接埠，其中的 BizTalk 協調流程會從卸除訊息的 SQL Server 資料庫上定義的位置。 這些訊息會以您指定接收埠的輪詢陳述式的回應。  
  
  - 不過，因為現在具有狀態為 0，則需要不有任何記錄，所以配接器會取得空的回應，如下列所示。 此連接埠會輪詢 SQL Server 資料庫，以您指定連接埠輪詢陳述式。 如需有關如何建立連接埠的資訊，請參閱 <<c0> [ 手動設定 SQL 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)。 請確定指定接收埠的下列繫結屬性。  
  
    > [!IMPORTANT]
    >  您不需要執行此步驟中，如果您指定在設計階段的繫結屬性。 在此情況下，您可以建立 wcf-custom 或 WCF SQL 接收埠中，設定必要的繫結屬性，藉由匯入所建立的繫結檔[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 如需詳細資訊，請參閱[設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。  
  
    |繫結屬性|ReplTest1|  
    |----------------------|-----------|  
    |**InboundOperationType**|請確定您將此設**輪詢**。|  
    |**PolledDataAvailableStatement**|請確定您指定的 SQL 陳述式。 本主題中，請指定：<br /><br /> `SELECT COUNT(*) FROM Employee`|  
    |**PollingStatement**|請確定您指定輪詢陳述式。 本主題中，請指定：<br /><br /> `SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000`|  
  
     如需不同的繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
    > [!NOTE]
    >  我們建議您執行使用的輸入的操作時設定的交易隔離等級和交易等待時間[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 您可以執行加上服務行為設定 Wcf-custom 或 WCF-SQL 時接收埠。 如需有關如何新增服務行為的指示，請參閱[設定交易隔離等級和交易等待時間，使用 SQL](../../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md)。  
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 SQL Server 資料庫中接收訊息的 BizTalk 應用程式。 如需有關啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。  
  
 在這個階段，請確定：  
  
-   Wcf-custom 或 WCF-SQL 單向接收連接埠，就會使用指定的陳述式的 SQL Server 資料庫來輪詢**PollingStatement**繫結屬性，正在執行。  
  
-   FILE 傳送埠，會從 SQL Server 中接收的訊息，正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，下列的一組動作進行，相同的順序：  
  
- 執行配接器**PolledDataAvailableStatement** employee 資料表，並判斷資料表是否有記錄進行輪詢。  
  
- 配接器執行輪詢陳述式。 輪詢陳述式是由 SELECT 陳述式和預存程序所組成，因為配接器會執行所有陳述式一個接著一個。  
  
  - 配接器會先執行 SELECT 陳述式會傳回 Employee 資料表中的所有記錄。  
  
  - 然後執行 MOVE_EMP_DATA 預存程序從 Employee 資料表的所有資料移動至 EmployeeHistory 資料表配接器。 這個預存程序不會傳回任何值。  
  
  - 配接器接著就執行 ADD_EMP_DETAILS 預存程序，將 [員工] 資料表中的一筆記錄。 這個預存程序傳回的員工識別碼插入之資料錄。  
  
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
  
- 配接器在執行時**PollDataAvailableStatement**同樣地，它會尋找一筆記錄插入 ADD_EMP_DETAILS 的預存程序。 配接器接著會執行所有三個陳述式所指定的**PollingStatement**繫結屬性。 這次會從 SQL Server 回應會包含 SELECT 陳述式的只有一項記錄，並且一筆記錄供 ADD_EMP_DETAILS 預存程序。 所有後續輪詢會傳回類似的回應。  
  
> [!NOTE]
>  [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]將繼續輪詢，直到您明確停用接收埠從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。 一旦您產生繫結檔案時，您可以匯入的組態設定檔案，，讓您不需要建立傳送埠和接收相同的協調流程的連接埠。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用配接器繫結](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md)。
  
## <a name="see-also"></a>另請參閱  
 [使用 SQL 配接器與 BizTalk Server 輪詢 SQL Server](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-biztalk-server.md)