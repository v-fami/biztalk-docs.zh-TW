---
title: 處理通知訊息，以便完成特定工作在 SQL 中使用 BizTalk Server |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8538cb89-1cca-45ad-b6f4-041e117963ff
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36d3c923593fe9a9402a14012e93fccb274ecdb6
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25967340"
---
# <a name="process-notification-messages-to-complete-specific-tasks-in-sql-using-biztalk-server"></a>處理通知訊息，以便完成特定工作中使用 BizTalk Server 的 SQL
您可以使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]接收通知的 SQL Server 資料庫資料表的變更。 不過，配接器只會傳送一些記錄已插入、 更新或刪除特定資料庫資料表中的通知。 用戶端應用程式本身必須處理這些記錄的任何後續處理。 本主題顯示如何處理從 SQL Server 資料庫接收通知的種類為基礎的資料表中的記錄以案例為基礎的描述。  
  
## <a name="scenarios-for-performing-subsequent-actions-after-receiving-notification"></a>執行後續的動作，在收到通知的案例  
 以下是幾個案例中，配接器用戶端必須執行某些通知後工作。  
  
-   **案例 1**。 假設配接器用戶端必須執行特定工作，根據您從 SQL Server 所接收的通知類型的地方。 例如，用戶端應用程式必須更新"A"資料表中的記錄，如果要在資料表"B"中插入記錄。 同樣地，用戶端應用程式必須記錄如果刪除資料表"A"從"B"資料表刪除記錄。  
  
     在此案例中，我們收到的通知訊息從配接器用戶端必須擷取決定通知是否為 insert 或 delete 作業的通知類型。 一旦為 reflection 的通知類型，配接器用戶端必須執行插入或更新的相關資料表的後續動作。  
  
-   **案例 2**。 假設接收到的資料表所做變更的通知訊息的接收位置會中斷。 接收位置已關閉，而某些記錄會加入至資料表。 不過，這些記錄配接器用戶端沒有收到任何通知。 備份 接收位置時，配接器用戶端會傳送通知的特定訊息，然後向下接收位置時，已插入資料庫資料表中的所有記錄必須都尋找用戶端應用程式。  
  
     在此案例中，我們收到的通知訊息從配接器用戶端必須擷取之通知是資料庫資料表的變更或接收位置開始的相關資訊。 如果通知的接收位置開始，配接器用戶端必須實作邏輯以處理可能會有已插入、 更新或刪除接收位置時關閉記錄。  
  
> [!NOTE]
>  這些是一些範例案例，進一步了解如何使用 「 通知 」 功能中的所列[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 不過，一組基本的擷取收到的通知類型所需的工作將會在所有案例類似。 本主題說明如何擷取通知訊息的通知類型。  
  
## <a name="how-this-topic-demonstrates-receiving-notification-messages-and-extracting-notification-type"></a>本主題示範接收通知訊息和擷取通知類型  
 本主題中，以示範如何處理通知訊息，以執行後續工作，我們假設基本配接器用戶端使用的 BizTalk 應用程式來接收員工資料表所做變更的通知訊息的位置。 在收到通知之後，用戶端篩選的收到的通知類型，並執行後續動作。 若要示範非常基本的案例，讓我們考慮，配接器用戶端會將通知訊息複製到不同的資料夾，根據收到的通知類型。 因此：  
  
-   如果 Insert 或 Update 作業的通知訊息，配接器用戶端會將訊息複製 C:\TestLocation\UpsertNotification 資料夾。  
  
-   如果通知訊息的任何其他作業，例如刪除，配接器用戶端會將訊息複製到 C:\TestLocation\OtherNotificaiton 資料夾。  
  
 若要達到這做為 BizTalk 應用程式的一部分，協調流程必須包含下列各項：  
  
-   單向接收埠以接收通知訊息。  
  
-   「 運算式 」 圖形，其中包含 xpath 查詢來擷取收到的通知訊息的類型資訊。  
  
-   在協調流程中包含決策區塊 「 決定 」 圖形。 在此決策區塊中，應用程式決定要執行的後續作業基礎收到的通知訊息。  
  
-   兩個單向傳送埠，最後接收通知訊息。  
  
## <a name="configuring-notifications-with-the-sql-adapter-binding-properties"></a>使用 SQL 配接器繫結屬性中設定通知  
 下表摘要說明[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結，您用來設定 SQL Server 從接收通知的屬性。 您必須同時設定接收埠中的指定這些繫結屬性[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
> [!NOTE]
>  您可以選擇指定這些繫結內容產生的結構描述時**通知**作業，即使它不是強制性。 如果您這樣做，連接埠繫結檔，[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生的中繼資料產生的組件也包含您指定的繫結屬性的值。 您可以稍後匯入此繫結檔案[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台建立 wcf-custom 或 WCF SQL 接收埠以繫結已設定的屬性。 如需有關如何建立使用該繫結檔案的連接埠的詳細資訊，請參閱[設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。  
  
|繫結屬性|Description|  
|----------------------|-----------------|  
|**InboundOperationType**|指定輸入您想要執行的作業。 若要接收通知訊息，將此設**通知**。|  
|**NotificationStatement**|指定的 SQL 陳述式 (SELECT 或 EXEC\<預存程序\>) 用來註冊查詢通知。 在結果集為指定的 SQL 陳述式變更時，才配接器從 SQL Server 取得通知訊息。|  
|**NotifyOnListenerStart**|指定是否配接器傳送通知給配接器用戶端啟動接聽程式時。|  
  
 如需這些屬性的更完整說明，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。 如需完整的說明，如何使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]進一步要從 SQL Server 中接收通知，閱讀。  
  
## <a name="how-to-receive-notification-messages-from-the-sql-server-database"></a>如何從 SQL Server 資料庫中接收通知訊息  
 使用 SQL Server 資料庫上執行操作[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及程序中所述的工作[開發 BizTalk 應用程式與 SQL 配接器的建置組塊](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)。 若要設定要接收通知訊息的介面卡，這些工作包括：  
  
1.  建立 BizTalk 專案，然後再產生結構描述的**通知**輸入作業。 您可以選擇性地指定值**InboundOperationType**和**NotificationStatement**繫結屬性。  
  
2.  從 SQL Server 資料庫中接收通知的 BizTalk 專案中建立訊息。  
  
3.  上一節中所述，建立協調流程。  
  
4.  建置和部署 BizTalk 專案。  
  
5.  設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
    > [!NOTE]
    >  輸入的作業，像是接收通知訊息，您必須只設定單向的 WCF 自訂或 WCF SQL 接收埠。 雙向 Wcf-custom 或 WCF SQL 接收埠的輸入作業不支援。  
  
6.  啟動 BizTalk 應用程式。  
  
 本主題提供執行這些工作的指示。  
  
## <a name="generating-schema"></a>產生結構描述  
 您必須產生的結構描述**通知**輸入作業。 請參閱[擷取中繼資料，使用 SQL 配接器的 Visual Studio 中的 SQL Server 作業的](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)如需有關如何產生結構描述。 產生結構描述時，請執行下列工作。 如果您不要指定繫結屬性在設計階段，請略過第一個步驟。  
  
1.  指定的值**InboundOperationType**和**NotificationStatement**時產生結構描述繫結屬性。 如需此繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。 如需有關如何指定繫結屬性的指示，請參閱[設定 SQL 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md)。  
  
2.  選取合約類型為**服務 （輸入操作）**。  
  
3.  產生結構描述的**通知**作業。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您先前產生的結構描述會描述 「 類型 」 所需的協調流程中的訊息。 訊息通常是為其型別由對應的結構描述所定義的變數。 一旦產生結構描述時，您必須訊息連結之協調流程檢視中的 BizTalk 專案。  
  
 本主題中，您必須建立一個要從 SQL Server 資料庫接收通知訊息。  
  
 執行下列步驟來建立訊息，並將它們連結至結構描述。  
  
#### <a name="to-create-messages-and-link-to-schema"></a>建立訊息，以及連結至結構描述  
  
1.  BizTalk 專案中新增協調流程。 從 方案總管 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下 **新項目**。 輸入 BizTalk 協調流程的名稱，然後按一下**新增**。  
  
2.  如果它尚未開啟，請開啟 BizTalk 專案中，[協調流程檢視] 視窗。 按一下**檢視**，指向 **其他視窗**，然後按一下 **協調流程檢視**。  
  
3.  在**協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。  
  
4.  以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。  
  
5.  在**屬性**窗格**Message_1**，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|輸入 `NotifyReceive`。|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*Process_Notification.Notification*，其中*Process_Notification*是您的 BizTalk 專案的名稱。 *通知*是針對產生的結構描述**通知**作業。|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]接收通知訊息從 SQL Server 資料庫，然後執行根據收到的通知類型的工作。 在此協調流程中，配接器接收通知訊息，根據指定的 SELECT 陳述式**NotificationStatement**繫結屬性。 「 運算式 」 圖形中指定的 xpath 查詢則會擷取類型的通知放入變數中，假設**notificationtype 而**。 「 決定 」 圖形在此變數會使用值來決定的收到的通知類型，並採用適當"path"以執行後續的作業。 如前一節所述，協調流程將執行下列作業根據接收通知訊息類型。  
  
-   如果 Insert 或 Update 作業的通知訊息，配接器用戶端會將訊息複製 C:\TestLocation\UpsertNotification 資料夾。  
  
-   如果通知訊息的任何其他作業，例如刪除，配接器用戶端會將訊息複製到 C:\TestLocation\OtherNotificaiton 資料夾。  
  
 因此，您的協調流程必須包含下列各項：  
  
-   單向接收埠以接收通知訊息。  
  
-   「 運算式 」 圖形，其中包含 xpath 查詢來擷取的收到的通知類型。  
  
-   在協調流程中包含決策區塊 「 決定 」 圖形。 在此決策區塊中，應用程式決定要執行的後續作業基礎收到的通知訊息。  
  
-   兩個單向傳送埠，最後接收通知訊息。  
  
-   接收圖形。  
  
 範例協調流程如下。  
  
 ![協調流程執行 post & #45，通知工作會](../../adapters-and-accelerators/adapter-sql/media/20f62716-603d-4293-84f7-8c8f6d82ccd0.gif "20f62716-603d-4293-84f7-8c8f6d82ccd0")  
  
### <a name="adding-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息圖形指定下列屬性。 圖形資料行中所列的名稱是訊息 圖形的名稱，為顯示在剛才提及的協調流程中。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveNotification|Receive|-設定**名稱**至*ReceiveNotification*<br /><br /> -設定**啟動**至 *，則為 True*|  
  
### <a name="adding-an-expression-shape"></a>新增 「 運算式 」 圖形  
 協調流程中包括 「 運算式 」 圖形的用途是將 xpath 查詢來擷取收到的通知訊息的類型。 在之前建立 xpath 查詢，讓我們看看通知訊息的格式。 典型的通知訊息如下所示：  
  
```  
<Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">  
  <Info>Insert</Info>   
  <Source>Data</Source>   
  <Type>Change</Type>   
</Notification>  
```  
  
 您看到的通知類型的相關資訊可內`<info>`標記，在父系`<Notification>`標記。 因此，在此運算式圖形，您必須：  
  
-   建立包含內值的變數，`<Info>`標記，並將其類型設為 System.String。 如需有關如何建立變數的詳細資訊，請參閱[在協調流程中使用變數](../../core/using-variables-in-orchestrations.md)。
  
     本主題中，命名為變數**notificationtype 而**。  
  
-   建立 xpath 查詢來擷取的值從\<資訊\>標記。 Xpath 查詢會如下所示：  
  
    ```  
    NotificationType = xpath(NotifyReceive,"string(/*[local-name()='Notification']/*[local-name()='Info']/text())");  
    ```  
  
     在此 xpath 查詢， **NotifyReceive**是您建立來接收通知訊息的訊息。 內摘錄`string`函式表示的查詢必須解壓縮內的值`<Info>`標記，這又是內`<Notification>`標記。 最後，將查詢所擷取的值指派給**NotificaitonType**變數。  
  
### <a name="adding-a-decide-shape"></a>新增 「 決定 」 圖形  
 新增 「 決定 」 圖形的目的是要在協調流程以決定要執行的後續作業基礎接收通知訊息類型中包含決策區塊。 根據的值所決定**notificationtype 而**變數。 本主題中，協調流程會根據接收通知訊息類型決定。 因此，「 規則 」 圖形中的條件的指定方式如下：  
  
```  
NotificationType.Equals("Insert") | NotificationType.Equals("Update")  
```  
  
 此條件所示，如果值**NotificaitonType**變數是 Insert 或 Update，協調流程會執行一組工作。 如果值**notificationtype 而**變數可以是任何其他項目，協調流程會執行其他的工作集。  
  
 如之前章節中所述，示範以簡單的方法，協調流程會將訊息複製到不同的資料夾，根據通知訊息類型。 因此，規則內和 Else 區塊，您必須新增傳送圖形，將訊息傳送至不同的通訊埠。 本主題中，命名為 「 傳送 」 圖形中的規則區塊**SendUpsertNotification**和在 Else 區塊中的 「 傳送 」 圖形**SendOtherNotification**。  
  
### <a name="adding-ports"></a>新增連接埠  
 您必須加入下列的邏輯連接埠至協調流程：  
  
-   單向接收埠以接收通知訊息從 SQL Server。  
  
-   單向傳送埠來傳送的 Insert 和 Update 作業的通知訊息給特定的資料夾。  
  
-   單向傳送埠來傳送通知訊息的任何其他作業特定的資料夾。  
  
 請確定您針對每個邏輯連接埠指定下列屬性。 連接埠資料行中所列的名稱是連接埠的名稱，為顯示協調流程中。  
  
|通訊埠|屬性|  
|----------|----------------|  
|SQLNotifyPort|-設定**識別碼**至*SQLNotifyPort*<br /><br /> -設定**類型**至*SQLNotifyPortType*<br /><br /> -設定**通訊模式**至*單向*<br /><br /> -設定**通訊方向**至*接收*|  
|NotificationUpsertPort|-設定**識別碼**至*NotificationUpsertPort*<br /><br /> -設定**類型**至*NotificationUpsertPortType*<br /><br /> -設定**通訊模式**至*單向*<br /><br /> -設定**通訊方向**至*傳送*|  
|OtherNotificationPort|-設定**識別碼**至*OtherNotificationPort*<br /><br /> -設定**類型**至*OtherNotificationPortType*<br /><br /> -設定**通訊模式**至*單向*<br /><br /> -設定**通訊方向**至*傳送*|  
  
### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>指定動作圖形訊息並連接至連接埠  
 下表指定屬性和其值，您應該設定來指定動作圖形的訊息，以及連結至連接埠的訊息。 圖形資料行中所列的名稱是 「 訊息 」 圖形的名稱，為顯示在協調流程中先前所述。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveNotification|-設定**訊息**至*NotifyReceive*<br /><br /> -設定**作業**至*SQLNotifyPort.Notify.Request*|  
|SendUpsertNotification|-設定**訊息**至*NotifyReceive*<br /><br /> -設定**作業**至*NotificationUpsertPort.Upsert.Request*|  
|SendOtherNotification|-設定**訊息**至*選取*<br /><br /> -設定**作業**至*OtherNotificationPort.Other.Request*|  
  
 您指定這些屬性之後，連接的訊息 圖形和連接埠，而且您的協調流程已完成。  
  
 您現在必須建置 BizTalk 方案，並部署到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱[建置和執行協調流程](../../core/building-and-running-orchestrations.md)。
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 部署 BizTalk 專案之後，您稍早建立的協調流程會列在**協調流程**BizTalk Server 管理主控台 窗格。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 如需逐步解說，請參閱[逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。  
  
 設定應用程式包括：  
  
-   選取應用程式的主機。  
  
-   對應至 BizTalk Server 管理主控台中的實體連接埠在協調流程中建立的連接埠。 此協調流程中，您必須：  
  
    -   定義實體的 WCF 自訂或 WCF-SQL 單向接收埠。 此連接埠會接聽來自 SQL Server 資料庫的通知。 如需如何建立連接埠相關資訊，請參閱[手動設定 SQL 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)。 請確定指定接收埠的下列繫結屬性。  
  
        > [!IMPORTANT]
        >  您不需要執行這個步驟，如果您指定在設計階段的繫結屬性。 在此情況下，您可以建立 wcf-custom 或 WCF SQL 接收埠，設定必要的繫結屬性，藉由匯入所建立之繫結檔案[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 如需詳細資訊，請參閱[設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。  
  
        |繫結屬性|值|  
        |----------------------|-----------|  
        |**InboundOperationType**|將此設**通知**。|  
        |**NotificationStatement**|將此值設定為：<br /><br /> `SELECT Employee_ID, Name FROM dbo.Employee WHERE Status=0`<br /><br /> **注意：** 您必須明確指定資料行名稱的陳述式中這個 SELECT 陳述式中所示。 此外，您永遠必須指定資料表名稱，以及結構描述名稱。 例如， `dbo.Employee`。|  
        |**NotifyOnListenerStart**|將此設**True**。|  
  
         如需不同的繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
        > [!NOTE]
        >  我們建議您執行使用的輸入的操作時設定的交易隔離等級和異動逾時[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 您可以執行新增服務行為設定 Wcf-custom 或 WCF-SQL 時接收埠。 如需如何新增服務行為的指示，請參閱[設定交易隔離等級和交易逾時，使用 SQL](../../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md)。  
  
    -   定義位置上的硬碟和對應的檔案連接埠，其中 BizTalk 協調流程會從卸除的通知訊息之 SQL Server 資料庫的 Insert 和 Update 作業。 設定此連接埠來卸除資料夾 C:\TestLocation\UpsertNotification 的通知訊息。  
  
    -   定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程會放置的位置，通知訊息從 SQL Server 資料庫，而所有其他作業。 設定此連接埠來卸除資料夾 C:\TestLocation\OtherNotification 的通知訊息。  
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 BizTalk 應用程式接收通知訊息從 SQL Server 資料庫以及執行後續的 Select 和 Update 作業。 如需啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。
  
 在這個階段，請確定：  
  
-   Wcf-custom 或 WCF-SQL 單向接收埠，會從 SQL Server 資料庫執行時接收通知訊息。  
  
-   兩個的檔案傳送埠，從 SQL Server 接收訊息，正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 啟動 BizTalk 協調流程之後，下列的動作集合就會發生：  
  
-   因為**NotifyOnListenerStart**繫結屬性設定為**True**，您會收到下列訊息：  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">  
      <Info>ListenerStarted</Info>   
      <Source>SqlBinding</Source>   
      <Type>Startup</Type>   
    </Notification>  
    ```  
  
     請注意，中的值`<Info>`標記為 「 ListnerStarted"。 因此，會收到此訊息 C:\TestLocation\OtherNotification 資料夾中。  
  
-   Employee 資料表中插入記錄。 您會收到通知訊息，如下列所示：  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">  
      <Info>Insert</Info>   
      <Source>Data</Source>   
      <Type>Change</Type>   
    </Notification>  
    ```  
  
     請注意，中的值`<Info>`標記為 「 插入 」。 因此，會收到此訊息 C:\TestLocation\UpsertNotification 資料夾中。  
  
-   更新 Employee 資料表中的記錄。 您會收到通知訊息，如下列所示：  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">  
      <Info>Update</Info>   
      <Source>Data</Source>   
      <Type>Change</Type>   
    </Notification>  
    ```  
  
     請注意，中的值`<Info>`標記為 「 更新 」。 因此，會收到此訊息 C:\TestLocation\UpsertNotification 資料夾中。  
  
-   從 Employee 資料表刪除記錄。 您會收到通知訊息，如下列所示：  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">  
      <Info>Delete</Info>   
      <Source>Data</Source>   
      <Type>Change</Type>   
    </Notification>  
    ```  
  
     請注意，中的值`<Info>`標記為 「 刪除 」。 因此，會收到此訊息 C:\TestLocation\OtherNotification 資料夾中。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。 一旦產生繫結檔案時，可以組態設定匯入檔案，使您不需要建立傳送埠和接收相同的協調流程連接埠。 如需繫結檔案的詳細資訊，請參閱[重複使用配接器繫結](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md)。
  
## <a name="performing-complex-operations-after-receiving-notification-messages"></a>執行複雜的作業之後接收通知訊息  
 為了簡化和更佳了解，本主題中的協調流程會將訊息複製到不同的資料夾，根據通知類型。 不過，在真實世界案例中，您可能想要執行更複雜的作業。 您可以執行類似的程序，如本主題和組建，以執行您希望的作業所提供。 例如，您可以變更另一個資料表中插入記錄，如果您收到 Employee 資料表的插入作業的通知訊息的協調流程。 在這種情況下，您可以進行適當的變更，「 決定 」 圖形內。  
  
 其中一個這類情況中會詳細說明在[教學課程 2： 員工-訂單程序使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/tutorial-2-employee-purchase-order-process-using-the-sql-adapter.md)。  
  
## <a name="see-also"></a>請參閱  
 [接收使用 BizTalk Server 的 SQL 查詢通知](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md)