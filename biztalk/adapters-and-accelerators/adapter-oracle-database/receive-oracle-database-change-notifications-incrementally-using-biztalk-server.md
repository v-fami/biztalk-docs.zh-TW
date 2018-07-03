---
title: 接收以累加方式使用 BizTalk Server 的 Oracle 資料庫變更通知 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17cef39f-a1aa-4f46-993f-620008f3890d
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61e8fbbe2644098baf963d258d3e95b94e20e8b8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012087"
---
# <a name="receive-oracle-database-change-notifications-incrementally-using-biztalk-server"></a>接收以累加方式使用 BizTalk Server 的 Oracle 資料庫變更通知
> [!IMPORTANT]
>  為了簡潔起見，本主題僅說明如何以累加方式接收通知。 在商務案例中，協調流程必須在理想情況下會納入邏輯來擷取收到的通知訊息的類型，然後再執行任何後續的作業。 本主題中所述的協調流程換句話說，必須採用協調流程中所述[程序來完成特定工作，使用 BizTalk Server 的 Oracle 資料庫中的通知訊息](../../adapters-and-accelerators/adapter-oracle-database/process-notification-messages-to-run-specific-tasks-in-oracle-db-using-biztalk.md)。  
  
 本主題示範如何設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]從 Oracle 接收累加式的查詢通知訊息。 為了示範累加通知，我們假設資料表，ACCOUNTACTIVITY，具有 「 處理 」 資料行。 此資料表插入新記錄時，「 處理 」 資料行的值設為 ' n '。 您可以設定配接器接收累加的通知，執行下列動作：  
  
- 註冊通知使用的 SELECT 陳述式會擷取所有記錄具有 「 處理 」 資料行做為 ' n '。 則可以藉由指定 SELECT 陳述式，如**NotificationStatement**繫結屬性。  
  
- 對於已通知的資料列，更新為 'y' 的 「 處理 」 資料行。  
  
  本主題示範如何建立 BizTalk 協調流程和設定 BizTalk 應用程式來達到此目的。  
  
## <a name="configuring-notifications-with-the-oracle-database-adapter-binding-properties"></a>使用 Oracle 資料庫配接器繫結屬性中設定通知  
 下表摘要說明[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結屬性，您用來設定從 Oracle 資料庫接收通知。 您必須在設定接收埠中的指定這些繫結屬性[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
> [!NOTE]
>  您也可以指定這些繫結屬性，產生的結構描述時**通知**作業，即使它不是強制性。 如果您這樣做時，連接埠繫結檔案[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生的中繼資料產生的組件也包含您指定的繫結屬性的值。 您可以稍後匯入此繫結檔案中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 WCF 自訂或 Wcf-oracledb 與繫結屬性已設定接收埠。 如需建立接收埠使用的繫結檔案的詳細資訊，請參閱 <<c0> [ 設定為使用 Oracle 資料庫的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md)。  
  
|繫結屬性|描述|  
|----------------------|-----------------|  
|**InboundOperationType**|指定輸入您想要執行的作業。 若要接收通知訊息，將此設**通知**。|  
|**NotificationPort**|指定 ODP.NET 必須開啟以接聽從 Oracle 資料庫的資料庫變更通知的連接埠號碼。|  
|**NotificationStatement**|指定用來註冊查詢通知的 SELECT 陳述式。 配接器在結果集，指定 SELECT 陳述式變更時，才取得通知訊息。|  
|**NotifyOnListenerStart**|指定是否配接器傳送通知給配接器用戶端啟動接聽程式時。|  
  
 如需這些屬性的更完整說明，請參閱[使用 BizTalk Adapter for Oracle 資料庫繫結屬性](https://msdn.microsoft.com/library/dd788467.aspx)。 如需完整的說明，如何使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]若要從 Oracle 資料庫接收通知，可深入閱讀。  
  
## <a name="how-this-topic-demonstrates-receiving-notification-messages"></a>本主題示範接收通知訊息  
 本主題中，以示範如何[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援從 Oracle 資料庫接收累加資料庫變更通知訊息，我們會設定配接器接收 ACCOUNTACTIVTY 資料表所做變更的通知。 讓我們假設 ACCOUNTACTIVITY 資料表有資料行"TID 」、 「 帳戶 」 和 「 處理 」。 每當新增新的記錄時，「 處理 」 資料行的值設為 ' n '。 因此，若要取得累加通知您必須為 BizTalk 協調流程的一部分執行下列工作：  
  
- 取得通知，其中是 「 處理 」 的所有記錄的 ' n '。 您可以指定做為通知的陳述式的 SELECT 陳述式來執行這項操作。  
  
- 某些記錄收到通知之後，請為 'y' 中設定 「 處理 」。 您可以執行預存程序，PROCESS_RECORDS，更新 「 處理 」 的資料行來執行這項操作。  
  
  為了示範接收累加的通知，我們執行下列作業：  
  
- 產生結構描述**通知**（輸入作業），以及**PROCESS_RECORDS** （輸出作業） ACCOUNTACTIVITY 資料表上。  
  
- 建立具有下列的協調流程：  
  
  -   接收位置來接收通知訊息。 您可以藉由指定 SELECT 陳述式設定通知：  
  
      ```  
      SELECT TID,ACCOUNT,PROCESSED FROM SCOTT.ACCOUNTACTIVITY WHERE PROCESSED = ‘n’  
      ```  
  
      > [!NOTE]
      >  您必須指定資料表名稱，以及結構描述名稱。 例如， `SCOTT.ACCOUNTACTIVITY`。  
  
  -   傳送埠，以更新的通知已傳送的資料列。 您將執行 PROCESS_RECORDS 預存程序，在此連接埠設為 'y' 收到通知的記錄的 「 處理 」 資料行的值。  
  
       請注意接收通知訊息，以便處理的資料列更新之後，必須執行此作業。 若要執行立即等候取得通知回應，然後再手動卸除執行 PROCESS_RECORDS 程序的要求訊息的額外負荷，您將會產生 PROCESS_RECORDS 程序協調流程本身內的要求訊息。 您可以使用來進行這**建構訊息**協調流程內的圖形。  
  
## <a name="how-to-receive-notification-messages-from-the-oracle-database"></a>如何從 Oracle 資料庫接收通知訊息  
 執行上 Oracle 資料庫使用的作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[開發與 Oracle 資料庫的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)。 若要設定要接收通知訊息的介面卡，這些工作如下：  
  
1. 建立 BizTalk 專案，然後再產生結構描述**通知**（輸入作業） 和**PROCESS_RECORDS** ACCOUNTACTIVITY 資料表上的程序 （輸出作業）。 您可以選擇性地指定值**InboundOperationType**， **NotificationPort**，並**NotificationStatement**繫結屬性。  
  
2. 從 Oracle 資料庫接收通知的 BizTalk 專案中建立訊息。  
  
3. 在執行 PROCESS_RECORDS 預存程序，並接收回應訊息的 BizTalk 專案中的訊息。  
  
4. 建立協調流程，會執行下列作業：  
  
   -   從 Oracle 資料庫接收通知訊息。  
  
   -   建立要執行 PROCESS_RECORDS 程序的訊息。  
  
   -   將此訊息傳送到 Oracle 資料庫，以選取和更新記錄並接收回應。  
  
5. 建置和部署 BizTalk 專案。  
  
6. 設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
   > [!NOTE]
   >  輸入的作業，例如接收通知訊息，您必須只設定單向的 WCF 自訂或 Wcf-oracledb 接收埠。 雙向接收埠不支援的輸入作業。  
  
7. 啟動 BizTalk 應用程式。  
  
   本主題提供執行這些工作的指示。  
  
## <a name="generating-schema"></a>產生結構描述  
 您必須產生的結構描述**通知**作業並**PROCESS_RECORDS**程序。 請參閱[擷取 Oracle 作業，在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)如需有關如何產生結構描述。 產生結構描述時，請執行下列工作。 如果您不想指定在設計階段的繫結屬性，請略過第一個步驟。  
  
1.  指定的值**InboundOperationType**， **NotificationPort**，並**NotificationStatement**時產生結構描述繫結屬性。 如需有關這個繫結屬性的詳細資訊，請參閱[使用 BizTalk Adapter for Oracle 資料庫繫結屬性](https://msdn.microsoft.com/library/dd788467.aspx)。 如需有關如何指定繫結屬性的指示，請參閱 <<c0> [ 指定的繫結屬性](https://msdn.microsoft.com/library/dd788420.aspx)。  
  
2.  選取合約類型作為**服務 （輸入作業）**。  
  
3.  產生結構描述**通知**作業。  
  
4.  選取合約類型作為**用戶端 （傳出作業）**。  
  
5.  產生結構描述**PROCESS_RECORDS**程序。 此程序，會位於**ACCOUNT_PKG**封裝。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您稍早產生的結構描述會描述協調流程中的訊息所需的 「 類型 」。 訊息通常是一個變數，要為其類型會定義對應的結構。 一旦產生結構描述時，您必須訊息從 BizTalk 專案的協調流程檢視以將它的連結。  
  
 本主題中，您必須建立三個訊息，一個用於接收從 Oracle 資料庫，一個執行 PROCESS_RECORDS 程序，一個用於接收程序回應的通知。  
  
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
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*OracleNotifyIncremental.OracleDBBinding.Notification*，其中*OracleNotifyIncremental*的名稱您的 BizTalk 專案。 *OracleDBBinding*是針對產生的結構描述**通知**作業。|  
  
6.  重複步驟 3 以建立兩個新的訊息。 在 **屬性**窗格中的新訊息，執行下列動作：  
  
    |若要設定識別項|若要設定訊息類型|  
    |-----------------------|-------------------------|  
    |程序|*OracleNotifyIncremental.OracleDBBinding1.PROCESS_RECORDS*，其中*OracleDBBinding1*是針對產生的結構描述**PROCESS_RECORDS**程序。|  
    |ProcedureResponse|*OracleNotifyIncremental.OracleDBBinding1.PROCESS_RECORDSResponse*|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]用於從 Oracle 資料庫接收通知訊息，然後更新 收到通知的資料列。 在此協調流程中，配接器會接收依據指定的 SELECT 陳述式的通知訊息**NotificationStatement**繫結屬性。 檔案位置就會收到通知訊息。 一旦收到回應時，協調流程會建構要叫用的 PROCESS_RECORDS 程序，更新的資料列，收到通知訊息。 此訊息的回應也就會收到相同的檔案位置。  
  
 因此，您的協調流程必須包含下列各項：  
  
- 單向的 「 WCF 自訂 」 或 「 Wcf-oracledb 接收埠來接收通知訊息。  
  
- 雙向的 「 WCF 自訂 」 或 「 Wcf-oracledb 傳送埠將訊息傳送至執行 PROCESS_RECORDS 程序。  
  
- A**建構訊息**圖形來建構執行 PROCESS_RECORDS 程序，在協調流程中的訊息。  
  
- 檔案傳送埠以儲存通知訊息和 PROCESS_RECORDS 程序的回應。  
  
- 接收和傳送圖形。  
  
  範例協調流程如下所示。  
  
  ![若要從 Oracle 接收通知的協調流程](../../adapters-and-accelerators/adapter-oracle-database/media/cef49414-490a-4bd5-a32d-b3f4cde5950a.gif "cef49414-490a-4bd5-a32d-b3f4cde5950a")  
  
### <a name="adding-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息 圖形中指定下列屬性。 剛剛提到的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveNotification|Receive|-設定**名稱**到*ReceiveNotification*<br /><br /> -設定**啟用**到 *，則為 True*|  
|SaveNotification|Send|-設定**名稱**到*SaveNotification*|  
|SendProcMessage|Send|-設定**名稱**到*SendProcMessage*|  
|ReceiveProcResponse|Receive|-設定**名稱**到*ReceiveProcResponse*|  
|SaveProcResponse|Send|-設定**名稱**到*SaveProcResponse*|  
  
### <a name="adding-construct-message-shape"></a>新增 建構訊息圖形  
 您可以使用**建構訊息**產生要求訊息的協調流程內執行 PROCESS_RECORDS 程序的圖形。 若要這樣做，您必須加入**建構的訊息**圖形，並在其中**訊息指派**圖形至協調流程。 此範例中，如**訊息指派**圖形叫用會產生訊息傳送到 Oracle 資料庫執行此程序的程式碼。 **訊息指派**圖形也會將訊息傳送到 Oracle 資料庫的動作。  
  
 針對 「 建構訊息 」 圖形中，設定**建構的訊息**屬性設**程序**。  
  
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
            XmlFileLocation = "C:\\TestLocation\\MessageIn";  
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
  
 上述程式碼摘錄中能夠產生要求訊息，您必須 （適用於 PROCESS_RECORDS 程序） XML 要求訊息中指定的位置`XmlFileLocation`變數。  
  
> [!NOTE]
>  建置專案之後，就會建立 MessageCreator.dll 專案目錄中。 您必須將此 DLL 加入全域組件快取 (GAC)。 此外，您必須新增 MessageCreator.dll 做為 BizTalk 專案中的參考。  
  
 加入下列運算式來叫用此程式碼**訊息指派**圖形，並設定訊息的動作。 若要新增運算式，請按兩下**訊息指派**圖形以開啟 運算式編輯器。  
  
```  
Procedure = SampleMessageCreator.SampleMessageCreator.XMLMessageCreator();  
Procedure(WCF.Action) = "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/PROCESS_RECORDS";  
```  
  
### <a name="adding-ports"></a>新增連接埠  
 請確定您針對每個邏輯連接埠中指定下列屬性。 協調流程中所示，連接埠資料行中所列的名稱會是連接埠的名稱。  
  
|通訊埠|屬性|  
|----------|----------------|  
|OracleNotifyPort|-設定**識別碼**到*OracleNotifyPort*<br /><br /> -設定**型別**到*OracleNotifyPortType*<br /><br /> -設定**通訊模式**到*單向*<br /><br /> -設定**通訊方向**到*接收*|  
|SaveMessagePort|-設定**識別碼**到*SaveMessagePort*<br /><br /> -設定**型別**到*SaveMessagePortType*<br /><br /> -設定**通訊模式**到*單向*<br /><br /> -設定**通訊方向**到*傳送*<br /><br /> -建立作業*通知*。 這項作業用於通知訊息。<br /><br /> -建立作業*程序*。 此作業可用於選取的回應訊息。|  
|OracleOutboundPort|-設定**識別碼**到*OracleOutboundPort*<br /><br /> -設定**型別**到*OracleOutboundPortType*<br /><br /> -設定**通訊模式**到*要求-回應*<br /><br /> -設定**通訊方向**到*傳送接收*|  
  
### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>為動作圖形指定訊息，並連接到連接埠  
 下表指定的屬性和屬性來指定動作圖形的訊息，以及連結至連接埠的訊息，您應該設定的值。 先前所述的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveNotification|-設定**訊息**到*NotifyReceive*<br /><br /> -設定**作業**到*OracleNotifyPort.Notify.Request*|  
|SaveNotification|-設定**訊息**到*NotifyReceive*<br /><br /> -設定**作業**到*SaveMessagePort.Notify.Request*|  
|SendProcMessage|-設定**訊息**到*程序*<br /><br /> -設定**作業**到*OracleOutboundPort.Procedure.Request*|  
|ReceiveProcResponse|-設定**訊息**到*ProcedureResponse*<br /><br /> -設定**作業**到*OracleOutboundPort.Procedure.Response*|  
|SaveProcResponse|-設定**訊息**到*ProedureResponse*<br /><br /> -設定**作業**到*SaveMessagePort.Procedure.Request*|  
  
 您指定這些屬性之後，連線的訊息 圖形和連接埠和協調流程已完成。  
  
 您現在必須建置 BizTalk 方案，並將其部署至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 建置和執行協調流程](../../core/building-and-running-orchestrations.md)。  
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在下**協調流程** 窗格中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 您必須使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定應用程式。 如需逐步解說，請參閱 <<c0> [ 逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。
  
 設定應用程式包含：  
  
- 選取應用程式主機。  
  
- 對應至實體連接埠在協調流程中建立的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 此協調流程中，您必須：  
  
  - 定義實體的 Wcf-custom 或 Wcf-oracledb 單向接收埠。 此連接埠會接聽來自 Oracle 資料庫的通知。 如需如何建立接收埠，請參閱 <<c0> [ 手動設定 Oracle 資料庫配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md)。 請確定指定接收埠的下列繫結屬性。  
  
    > [!IMPORTANT]
    >  您不需要執行此步驟中，如果您指定在設計階段的繫結屬性。 在這種情況下，您可以建立接收埠，設定必要的繫結屬性，藉由匯入所建立的繫結檔[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 如需詳細資訊，請參閱[設定為使用 Oracle 資料庫的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md)。  
  
    |繫結屬性|ReplTest1|  
    |----------------------|-----------|  
    |**InboundOperationType**|將此設為**通知**。|  
    |**NotificationPort**|指定 ODP.NET 必須開啟以接聽從 Oracle 資料庫的資料庫變更通知的連接埠號碼。 設定為相同的連接埠號碼，您必須已加入的 Windows 防火牆例外清單。 如需如何將 Windows 防火牆例外清單中的連接埠的指示，請參閱 < [ http://go.microsoft.com/fwlink/?LinkID=196959 ](http://go.microsoft.com/fwlink/?LinkID=196959)。<br /><br /> **重要事項：** 如果您設定為預設值-1，您必須完全停用 Windows 防火牆，以接收通知訊息。|  
    |**NotificationStatement**|將此設為：<br /><br /> `SELECT TID,ACCOUNT,PROCESSED FROM SCOTT.ACCOUNTACTIVITY WHERE PROCESSED = ‘n’`<br /><br /> **注意：** 您必須指定資料表名稱，以及結構描述名稱。 例如， `SCOTT.ACCOUNTACTIVITY`。|  
    |**NotifyOnListenerStart**|將此設為 **，則為 True**。|  
  
     如需不同的繫結屬性的詳細資訊，請參閱[使用 BizTalk Adapter for Oracle 資料庫繫結屬性](https://msdn.microsoft.com/library/dd788467.aspx)。  
  
    > [!NOTE]
    >  我們建議您執行使用的輸入的操作時設定的交易隔離等級和交易等待時間[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 您可以執行加上服務行為設定 Wcf-custom 或 Wcf-oracledb 時接收埠。 如需有關如何新增服務行為的指示，請參閱[設定交易隔離等級和交易等待時間](../../adapters-and-accelerators/adapter-oracle-database/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-db.md)。  
  
  - 定義實體 Wcf-custom 或 Wcf-oracledb 傳送埠將訊息傳送至 Oracle 資料庫來執行 PROCESS_REOCRDS 程序。 您也必須在傳送埠中指定的動作。  
  
  - 硬碟和對應的檔案連接埠，BizTalk 協調流程會放置的位置將訊息從 Oracle 資料庫上定義的位置。 這些是從 Oracle 資料庫接收的通知訊息和訊息執行透過 Wcf-custom PROCESS_RECORDS 程序或 Wcf-oracledb 傳送埠。  
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 BizTalk 應用程式來接收通知訊息，從 Oracle 資料庫及執行 PROCESS_RECORDS 程序。 如需有關啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。  
  
 在這個階段，請確定：  
  
-   Wcf-custom 或 Wcf-oracledb 單向接收埠，以從 Oracle 資料庫執行時接收通知訊息。  
  
-   WCF 自訂] 或 [Wcf-oracledb 傳送埠執行 PROCESS_RECORDS 程序正在執行。  
  
-   FILE 傳送埠，會從 Oracle 資料庫接收的訊息，正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 假設 ACCOUNTACTIVITY 資料表已經有一些記錄。 此外，請確定要執行 PROCESS_RECORDS 程序的 XML 訊息將會位於 C:\TestLocation\MessageIn。 XML 檔案應該如下所示：  
  
```  
<PROCESS_RECORDS xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG"/>  
```  
  
 一旦啟動 BizTalk 協調流程之後，下列的一組動作進行相同的順序：  
  
-   配接器接收通知訊息，如下所示：  
  
    ```  
    \<?xml version="1.0" encoding="utf-8" ?\>   
    <Notification xmlns="http://Microsoft.LobServices.OracleDB/2007/03/Notification/">  
      <Info>ListenerStarted</Info>   
      <Source>OracleDBBinding</Source>   
      <Type>Startup</Type>   
    </Notification>  
    ```  
  
     此訊息會通知已啟動 接收埠來接收通知訊息。 請注意，值`<Info>`項目是 「 ListnerStarted"。  
  
-   配接器執行 PROCESS_RECORDS 程序。 從 Oracle 資料庫的下一個回應是程序。  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <PROCESS_RECORDSResponse xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG">  
      <TABLE_DATA>  
        <xs:schema id="NewDataSet" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
          <xs:element msdata:IsDataSet="true" name="NewDataSet">  
            <xs:complexType>  
              <xs:sequence>  
                <xs:element minOccurs="0" maxOccurs="unbounded" name="NewTable">  
                  <xs:complexType>  
                    <xs:sequence>  
                      <xs:element minOccurs="0" name="TID" type="xs:decimal" />   
                      <xs:element minOccurs="0" name="ACCOUNT" type="xs:decimal" />   
                      <xs:element minOccurs="0" name="PROCESSED" type="xs:string" />   
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
            <TID>1</TID>   
            <ACCOUNT>100001</ACCOUNT>   
            <PROCESSED>n</PROCESSED>   
          </NewTable>  
          <NewTable>  
            ......  
            ......  
          </NewTable>  
          ......  
          ......  
        </NewDataSet>  
        </diffgr:diffgram>  
      </TABLE_DATA>  
    </PROCESS_RECORDSResponse>  
    ```  
  
     這是回應 PROCESS_RECORDS 程序的一部分執行的 SELECT 陳述式。  
  
-   PROCESS_RECORDS 程序也會更新為 'y' 設定已處理的資料列。 因此，配接器接收的更新作業的另一個通知。  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Notification xmlns="http://Microsoft.LobServices.OracleDB/2007/03/Notification/">  
      <Details>  
        <NotificationDetails>  
          <ResourceName>SCOTT.ACCOUNTACTIVITY</ResourceName>   
          <Info>32</Info>   
          <QueryId>0</QueryId>   
        </NotificationDetails>  
      </Details>  
      <Info>Update</Info>   
      <ResourceNames>  
        <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/Arrays">SCOTT.ACCOUNTACTIVITY</string>   
      </ResourceNames>  
      <Source>Data</Source>   
      <Type>Change</Type>   
    </Notification>  
    ```  
  
     請注意，`Info`元素包含"Update"。  
  
-   第二個通知之後，配接器一次執行 PROCESS_RECORDS 程序。 不過，現在因為沒有的記錄之已處理的資料行設定為 ' n '，此程序會傳回類似下列的空白回應。  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <PROCESS_RECORDSResponse xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG">  
      <TABLE_DATA>  
        <xs:schema id="NewDataSet" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
          <xs:element msdata:IsDataSet="true" name="NewDataSet">  
            <xs:complexType>  
              <xs:sequence>  
                <xs:element minOccurs="0" maxOccurs="unbounded" name="NewTable">  
                  <xs:complexType>  
                    <xs:sequence>  
                      <xs:element minOccurs="0" name="TID" type="xs:decimal" />   
                      <xs:element minOccurs="0" name="ACCOUNT" type="xs:decimal" />   
                      <xs:element minOccurs="0" name="PROCESSED" type="xs:string" />   
                    </xs:sequence>  
                  </xs:complexType>  
                </xs:element>  
              </xs:sequence>  
            </xs:complexType>  
          </xs:element>  
        </xs:schema>  
        <diffgr:diffgram xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
          <NewDataSet xmlns="" />   
        </diffgr:diffgram>  
      </TABLE_DATA>  
    </PROCESS_RECORDSResponse>  
    ```  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。 一旦您產生繫結檔案時，您可以匯入的組態設定檔案，，讓您不需要建立傳送埠和接收相同的協調流程的連接埠。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用的 Oracle 資料庫配接器繫結](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk Server 接收的 Oracle 資料庫變更通知](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-using-biztalk-server.md)