---
title: 從使用 BizTalk Server 的 SQL 以累加方式查詢通知接收 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a6972e01-80be-47be-986a-c2e4e0fb0cd1
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e278b4e25db6c62127d2aac4ee8d29c3c422e463
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007759"
---
# <a name="receive-query-notifications-incrementally-from-sql-using-biztalk-server"></a>以累加方式查詢通知接收使用 BizTalk Server 的 SQL
> [!IMPORTANT]
>  為了簡潔起見，本主題僅說明如何以累加方式接收通知。 在商務案例中，協調流程必須在理想情況下會納入邏輯來擷取收到的通知訊息的類型，然後再執行任何後續的作業。 本主題中所述的協調流程換句話說，必須採用協調流程中所述[處理通知訊息，以完成特定工作中使用 BizTalk Server 的 SQL](../../adapters-and-accelerators/adapter-sql/process-notification-messages-to-complete-specific-tasks-in-sql-using-biztalk.md)。  
  
 本主題示範如何設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]接收從 SQL Server 資料庫的累加式的查詢通知訊息。 為了示範累加通知，請考慮資料表，員工，且 [狀態] 資料行。 此資料表插入新記錄時，[狀態] 欄的值設為 0。 您可以設定配接器接收累加的通知，執行下列動作：  
  
- 註冊使用 SQL 陳述式會擷取具有 [狀態] 欄位為 0 的所有記錄的通知。 則可以藉由指定的 SQL 陳述式**NotificationStatement**繫結屬性。  
  
- 對於已接收的通知訊息的資料列，更新 [狀態] 欄為 1。  
  
  本主題示範如何建立 BizTalk 協調流程和設定 BizTalk 應用程式來達到此目的。  
  
## <a name="configuring-notifications-with-the-sql-adapter-binding-properties"></a>使用 SQL 配接器繫結屬性中設定通知  
 下表摘要說明[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結屬性，您用來設定 從 SQL Server 中接收通知。 您必須在設定接收埠中的指定這些繫結屬性[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
> [!NOTE]
>  您也可以指定這些繫結屬性，產生的結構描述時**通知**作業，即使它不是強制性。 如果您這樣做時，連接埠繫結檔案[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生的中繼資料產生的組件也包含您指定的繫結屬性的值。 您可以稍後匯入此繫結檔案中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 WCF 自訂或 WCF-SQL 與繫結屬性已設定接收埠。 如需建立使用該繫結檔案的連接埠的詳細資訊，請參閱 <<c0> [ 設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。  
  
|繫結屬性|描述|  
|----------------------|-----------------|  
|**InboundOperationType**|指定輸入您想要執行的作業。 若要接收通知訊息，將此設**通知**。|  
|**NotificationStatement**|指定的 SQL 陳述式 (SELECT 或 EXEC\<預存程序\>) 用來註冊查詢通知。 在結果集為指定的 SQL 陳述式變更時，才配接器從 SQL Server 取得通知訊息。|  
|**NotifyOnListenerStart**|指定是否配接器傳送通知給配接器用戶端啟動接聽程式時。|  
  
 如需這些屬性的更完整說明，請參閱[了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。 如需完整的說明，如何使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]若要從 SQL Server 中接收通知，可深入閱讀。  
  
## <a name="how-this-topic-demonstrates-receiving-notification-messages"></a>本主題示範接收通知訊息  
 若要示範如何[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]支援從 SQL Server 中接收通知訊息，本主題將示範如何設定配接器接收的 Employee 資料表的變更通知。 假設員工資料表有資料行 Employee_ID、 名稱和狀態。 每當新增新進員工時，[狀態] 欄的值設為 0。  
  
 為了示範如何接收通知，執行下列作業：  
  
-   產生結構描述**通知**（輸入作業），和**選取**（輸出作業） 在 [員工] 資料表。  
  
-   建立具有下列的協調流程：  
  
    -   接收位置來接收通知訊息。 您可以藉由指定 SELECT 陳述式設定通知：  
  
        ```  
        SELECT Employee_ID, Name FROM dbo.Employee WHERE Status=0  
        ```  
  
        > [!NOTE]
        >  具體來說，您必須指定資料行名稱，在此所示的陳述式中的 SELECT 陳述式。 此外，您一律必須指定資料表名稱，以及結構描述名稱。 例如， `dbo.Employee`。  
  
    -   傳送埠，以更新的通知已傳送的資料列。 您這樣做，將值設定為 1 的 [狀態] 欄中。 您可以選取作業的一部分傳送至配接器的下列訊息。  
  
        ```  
        <Select xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
          <Columns>Employee_ID,Name,Status</Columns>  
          <Query>where Status=0;UPDATE Employee SET Status=1 WHERE Status=0</Query>  
        </Select>  
        ```  
  
         在此訊息中，做為一部分`<Query>`元素中，指定更新的狀態資料行 UPDATE 陳述式。 請注意接收通知訊息，以便處理的資料列更新之後，必須執行此作業。 若要執行立即等候取得通知回應，然後再手動卸除要求訊息來更新資料列的負擔，您將會產生更新協調流程本身內的資料列的要求訊息。 您可以使用來進行這**建構訊息**協調流程內的圖形。  
  
## <a name="how-to-receive-notification-messages-from-the-sql-server-database"></a>如何從 SQL Server 資料庫中接收通知訊息  
 執行 SQL Server 資料庫使用運算[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[開發使用 SQL 配接器的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)。 若要設定要接收通知訊息的介面卡，這些工作如下：  
  
1. 建立 BizTalk 專案，然後再產生結構描述**通知**（輸入作業） 和**選取**（輸出作業） 在 [員工] 資料表。 您可以選擇性地指定值**InboundOperationType**並**NotificationStatement**繫結屬性。  
  
2. 從 SQL Server 資料庫中接收通知的 BizTalk 專案中建立訊息。  
  
3. 在 SQL Server 資料庫上執行選取的資訊，並接收回應訊息的 BizTalk 專案中建立訊息。  
  
4. 建立協調流程，會執行下列作業：  
  
   -   從 SQL Server 中接收通知訊息。  
  
   -   建立選取及更新的資料列，收到通知訊息。  
  
   -   將此訊息傳送到 SQL Server 更新的資料列，並接收回應。  
  
5. 建置和部署 BizTalk 專案。  
  
6. 設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
   > [!NOTE]
   >  輸入的作業，例如接收通知訊息，您必須只設定單向的 WCF 自訂或 WCF SQL 接收埠。 雙向 WCF 自訂] 或 [WCF-SQL 接收埠不支援的輸入作業。  
  
7. 啟動 BizTalk 應用程式。  
  
   本主題提供執行這些工作的指示。  
  
## <a name="sample-based-on-this-topic"></a>根據本主題的範例  
 ，IncrementalNotification，根據本主題提供了範例[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱 < [SQL 配接器的範例](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md)。  
  
## <a name="generating-schema"></a>產生結構描述  
 您必須產生的結構描述**通知**作業並**選取**員工資料表上的執行作業。 請參閱[取得 Visual Studio 中使用 SQL 配接器中的 SQL Server 作業的中繼資料](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)如需有關如何產生結構描述。 產生結構描述時，請執行下列工作。 如果您不想在設計階段指定的繫結屬性，請略過第一個步驟。  
  
1.  指定的值**InboundOperationType**並**NotificationStatement**時產生結構描述繫結屬性。 如需有關這個繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。 如需有關如何指定繫結屬性的指示，請參閱 <<c0> [ 設定 SQL 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md)。  
  
2.  選取合約類型作為**服務 （輸入作業）**。  
  
3.  產生結構描述**通知**作業。  
  
4.  選取合約類型作為**用戶端 （傳出作業）**。  
  
5.  產生結構描述**選取 **上的作業**員工**資料表。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您稍早產生的結構描述會描述協調流程中的訊息所需的 「 類型 」。 訊息通常是一個變數，要為其類型會定義對應的結構。 一旦產生結構描述時，您必須訊息從 BizTalk 專案的協調流程檢視以將它的連結。  
  
 本主題中，您必須建立三個訊息，一個用於接收通知，從 SQL Server 資料庫，以執行所選取的作業和一個用來接收選取作業的回應。  
  
 執行下列步驟來建立訊息，並將它們連結至結構描述。  
  
#### <a name="to-create-messages-and-link-to-schema"></a>若要建立訊息，並連結至結構描述  
  
1.  BizTalk 專案中新增協調流程。 從 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下**新項目**。 輸入 BizTalk 協調流程的名稱，然後按一下**新增**。  
  
2.  如果它尚未開啟，請開啟 BizTalk 專案中，[協調流程檢視] 視窗。 按一下 **檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。  
  
3.  在 **協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。  
  
4.  以滑鼠右鍵按一下新建立的訊息，然後按**屬性 視窗**。  
  
5.  在 [**屬性**] 窗格**Message_1**，執行下列動作：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|輸入 `NotifyReceive`。|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*SQLNotify.Notification*，其中*SQLNotify*是 BizTalk 專案的名稱。 *通知*是針對產生的結構描述**通知**作業。|  
  
6.  重複步驟 3 以建立兩個新的訊息。 在 **屬性**窗格中的新訊息，執行下列動作：  
  
    |若要設定識別項|若要設定訊息類型|  
    |-----------------------|-------------------------|  
    |Select|*SQLNotify.TableOperation_dbo_Employee.Select*，其中*TableOperation_dbo_Employee*是針對產生的結構描述**選取**作業|  
    |SelectResponse|*SQLNotify.TableOperation_dbo_Employee.SelectResponse*|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]for SQL Server 資料庫中接收通知訊息，然後更新 收到通知的資料列。 在此協調流程中，配接器會接收依據指定的 SELECT 陳述式的通知訊息**NotificationStatement**繫結屬性。 檔案位置就會收到通知訊息。 一旦收到回應時，協調流程會建構的訊息，將用來更新資料列，收到通知。 此訊息的回應也就會收到相同的檔案位置。  
  
 因此，您的協調流程必須包含下列各項：  
  
- 單向接收埠以接收通知訊息。  
  
- 雙向傳送埠以傳送訊息以更新資料列，並接收相同的回應。  
  
- A**建構訊息**來建構訊息，以執行更新作業，在協調流程中的圖形。  
  
- FILE 傳送埠以儲存更新作業的回應。  
  
- 接收和傳送圖形。  
  
  範例協調流程如下所示。  
  
  ![用於接收 SQL Server 通知的協調流程](../../adapters-and-accelerators/adapter-sql/media/f13ad3b8-8161-42e5-a521-424bbf549ad5.gif "f13ad3b8-8161-42e5-a521-424bbf549ad5")  
  
### <a name="adding-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息 圖形中指定下列屬性。 剛剛提到的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveNotification|Receive|-設定**名稱**到*ReceiveNotification*<br /><br /> -設定**啟用**到 *，則為 True*|  
|SaveNotification|Send|-設定**名稱**到*SaveNotification*|  
|SendSelectMessage|Send|-設定**名稱**到*SendSelectMessage*|  
|ReceiveSelectResponse|Receive|-設定**名稱**到*ReceiveSelectResponse*|  
|SaveSelectResponse|Send|-設定**名稱**到*SaveSelectResponse*|  
  
### <a name="adding-construct-message-shape"></a>新增 建構訊息圖形  
 您可以使用**建構訊息**圖形，以產生在作業中執行選取的作業要求訊息。 若要這樣做，您必須加入**建構的訊息**圖形，並在其中**訊息指派**圖形至協調流程。 此範例中，如**訊息指派**圖形叫用所產生的訊息，傳送到 SQL Server 來執行選取作業的程式碼。 **訊息指派**圖形也會將訊息傳送到 SQL Server 的動作。  
  
 針對 「 建構訊息 」 圖形中，設定**建構的訊息**屬性設**選取**。  
  
 若要產生回應的程式碼可以是相同的 Visual Studio 方案，為您的 BizTalk 專案的一部分。 產生回應訊息的範例程式碼看起來像這樣。  
  
```  
namespace SampleMessageCreator  
{  
    public class SampleMessageCreator  
    {  
        private static XmlDocument Message;  
        private static string XmlFileLocation;  
        private static string ResponseDoc;  
        public static XmlDocument XMLMessageCreator()  
        {  
            XmlFileLocation = "C:\\TestLocation\\CreateMessage";  
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
  
 上述程式碼摘錄中能夠產生要求訊息，您必須 （適用於 [員工] 資料表的 Select 作業） 的 XML 要求訊息中所指定的位置`XmlFileLocation`變數。  
  
> [!NOTE]
>  建置專案之後，就會建立 SampleMessageCreator.dll 專案目錄中。 您必須將此 DLL 加入全域組件快取 (GAC)。 此外，您必須新增 SampleMessageCreator.dll 做為 BizTalk 專案中的參考。  
  
 加入下列運算式來叫用此程式碼**訊息指派**圖形，並設定訊息的動作。 若要新增運算式，請按兩下**訊息指派**圖形以開啟 運算式編輯器。  
  
```  
Select = SampleMessageCreator.SampleMessageCreator.XMLMessageCreator();  
Select(WCF.Action) = "TableOp/Select/dbo/Employee";  
```  
  
### <a name="adding-ports"></a>新增連接埠  
 請確定您針對每個邏輯連接埠中指定下列屬性。 協調流程中所示，連接埠資料行中所列的名稱會是連接埠的名稱。  
  
|通訊埠|屬性|  
|----------|----------------|  
|SQLNotifyPort|-設定**識別碼**到*SQLNotifyPort*<br /><br /> -設定**型別**到*SQLNotifyPortType*<br /><br /> -設定**通訊模式**到*單向*<br /><br /> -設定**通訊方向**到*接收*|  
|SaveMessagePort|-設定**識別碼**到*SaveMessagePort*<br /><br /> -設定**型別**到*SaveMessagePortType*<br /><br /> -設定**通訊模式**到*單向*<br /><br /> -設定**通訊方向**到*傳送*<br /><br /> -建立作業*通知*。 這項作業用於通知訊息。<br /><br /> -建立作業*選取*。 此作業可用於選取的回應訊息。|  
|SQLOutboundPort|-設定**識別碼**到*SQLOutboundPort*<br /><br /> -設定**型別**到*SQLOutboundPortType*<br /><br /> -設定**通訊模式**到*要求-回應*<br /><br /> -設定**通訊方向**到*傳送接收*|  
  
### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>為動作圖形指定訊息，並連接到連接埠  
 下表指定的屬性和屬性來指定動作圖形的訊息，以及連結至連接埠的訊息，您應該設定的值。 先前所述的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveNotification|-設定**訊息**到*NotifyReceive*<br /><br /> -設定**作業**到*SQLNotifyPort.Notify.Request*|  
|SaveNotification|-設定**訊息**到*NotifyReceive*<br /><br /> -設定**作業**到*SaveMessagePort.Notify.Request*|  
|SendSelectMessage|-設定**訊息**到*選取*<br /><br /> -設定**作業**到*SQLOutboundPort.Select.Request*|  
|ReceiveSelectResponse|此訊息通知記錄已更新 Employee 資料表中。*<br /><br /> 請注意，值**項目是 「 更新 」。*|  
|SaveSelectResponse|此訊息通知記錄已更新 Employee 資料表中。*<br /><br /> 第二個通知之後，配接器會執行 Select 陳述式。*|  
  
 您指定這些屬性之後，連線的訊息 圖形和連接埠和協調流程已完成。  
  
 您現在必須建置 BizTalk 方案，並將其部署至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 建置和執行協調流程](../../core/building-and-running-orchestrations.md)。
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在下**協調流程**在 BizTalk Server 管理主控台 窗格。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 如需逐步解說，請參閱 <<c0> [ 逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。
  
 設定應用程式包含：  
  
- 選取應用程式主機。  
  
- 對應您在您在 BizTalk Server 管理主控台中的實體連接埠的協調流程中建立的連接埠。 此協調流程中，您必須：  
  
  - 不過，因為現在具有狀態為 0，則需要不有任何記錄，所以配接器會取得空的回應，如下列所示。 如需有關繫結檔案的詳細資訊，請參閱 <<c0>  重複使用的 SQL 配接器繫結。 如需有關如何建立連接埠的資訊，請參閱 <<c0> [ 手動設定 SQL 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)。 請確定指定接收埠的下列繫結屬性。  
  
    > [!IMPORTANT]
    >  您不需要執行此步驟中，如果您在設計階段指定的繫結屬性。 在此情況下，您可以建立 wcf-custom 或 WCF SQL 接收埠中，設定必要的繫結屬性，藉由匯入所建立的繫結檔[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 如需詳細資訊，請參閱[設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。  
  
    |繫結屬性|ReplTest1|  
    |----------------------|-----------|  
    |**InboundOperationType**|將此設為**通知**。|  
    |**NotificationStatement**|將此設為：<br /><br /> `SELECT Employee_ID, Name FROM dbo.Employee WHERE Status=0`<br /><br /> **注意：** 您必須特別指定的資料行名稱的陳述式中，這個 SELECT 陳述式中所示。 此外，您一律必須指定資料表名稱，以及結構描述名稱。 例如， `dbo.Employee`。|  
    |**NotifyOnListenerStart**|將此設為 **，則為 True**。|  
  
     如需不同的繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
    > [!NOTE]
    >  我們建議您執行使用的輸入的操作時設定的交易隔離等級和交易等待時間[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 您可以執行加上服務行為設定 Wcf-custom 或 WCF-SQL 時接收埠。 如需有關如何新增服務行為的指示，請參閱[設定交易隔離等級和交易等待時間，使用 SQL](../../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md)。  
  
  - 定義實體 Wcf-custom 或 WCF SQL 傳送埠將訊息傳送至 SQL Server 資料庫。 您也必須在傳送埠中指定的動作。  
  
  - 硬碟和對應的檔案連接埠，其中的 BizTalk 協調流程會從卸除訊息的 SQL Server 資料庫上定義的位置。 這些會收到來自 SQL Server 的通知訊息和 select 的訊息，而且您透過 WCF 自訂或 WCF-SQL 執行更新作業的傳送埠。  
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 BizTalk 應用程式從 SQL Server 資料庫中接收通知訊息，並用來執行後續的 Select 和 Update 作業。 如需有關啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。
  
 在這個階段，請確定：  
  
-   Wcf-custom 或 WCF-SQL 單向接收埠，以從 SQL Server 資料庫執行時接收通知訊息。  
  
-   選取要執行的 WCF 自訂] 或 [WCF-SQL 傳送連接埠和員工資料表上的更新作業正在執行。  
  
-   FILE 傳送埠，會從 SQL Server 中接收的訊息，正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 若要執行這項作業，您必須將記錄插入員工資料表。 讓我們假設您插入具有下列詳細資料的記錄：  
  
```  
Name = John Smith  
Designation = Manager  
Salary = 100000  
```  
  
 此外，請確定選取要執行的 XML 訊息，並更新作業將會位於 C:\TestLocation\MessageIn。 XML 檔案應該如下所示：  
  
```  
<Select xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
  <Columns>Employee_ID,Name,Status</Columns>  
  <Query>where Status=0;UPDATE Employee SET Status=1 WHERE Status=0</Query>  
</Select>  
```  
  
 一旦插入記錄時，下列的一組動作進行相同的順序：  
  
-   配接器接收通知訊息，如下所示：  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">  
      <Info>Insert</Info>   
      <Source>Data</Source>   
      <Type>Change</Type>   
    </Notification>  
    ```  
  
     此訊息會告知 Employee 資料表中已插入一筆記錄。 請注意，值`<Info>`項目是 「 插入 」。  
  
-   配接器執行選取的作業。 因為選取的 XML 作業也包括 Update 陳述式，也會執行 Update 陳述式。 SQL Server 的下一個回應是 Select 陳述式。  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <SelectResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
      <SelectResult>  
        <Employee xmlns="http://schemas.microsoft.com/Sql/2008/05/Types/Tables/dbo">  
          <Employee_ID>10006</Employee_ID>   
          <Name>John</Name>   
          <Status>0</Status>  
        </Employee>  
      </SelectResult>  
    </SelectResponse>  
    ```  
  
     此回應會顯示一筆記錄插入員工資料表，以及該記錄的狀態是 0。  
  
-   Select 陳述式的一部分，也會執行 Update 陳述式，以及新記錄的狀態資料行變更為 1。 這會再次觸發另一個通知，從 SQL Server 和配接器接收對應的通知訊息，類似下列：  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">  
      <Info>Update</Info>   
      <Source>Data</Source>   
      <Type>Change</Type>   
    </Notification>  
    ```  
  
     此訊息通知記錄已更新 Employee 資料表中。 請注意，值`<Info>`項目是 「 更新 」。  
  
-   第二個通知之後，配接器會執行 Select 陳述式。 不過，因為現在具有狀態為 0，則需要不有任何記錄，所以配接器會取得空的回應，如下列所示。  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <SelectResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
      <SelectResult />   
    </SelectResponse>  
    ```  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。 一旦您產生繫結檔案時，您可以匯入的組態設定檔案，，讓您不需要建立傳送埠和接收相同的協調流程的連接埠。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用的 SQL 配接器繫結](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md)。
  
## <a name="see-also"></a>另請參閱  
 [接收使用 BizTalk Server 的 SQL 查詢通知](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md)