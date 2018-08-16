---
title: 輪詢使用預存程序、 函數或封裝的程序和函式的 Oracle 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6c34843a-d02b-4941-baf6-6bc80b5821ad
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e63bf6b30de29c18a9424306140804a4cf73c16d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010887"
---
# <a name="poll-oracle-database-using-stored-procedures-functions-or-packaged-procedures-and-functions"></a>使用預存程序、 函數或封裝的程序和函式的輪詢 Oracle 資料庫
您可以設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]藉由使用預存程序、 函數或封裝的程序和函式會定期輪詢 Oracle 資料庫接收定期的資料變更訊息。 您可以指定預存程序、 函數或封裝的程序，並做為輪詢 Oracle 資料庫定期執行配接器的輪詢陳述式。  

 若要啟用此功能，您必須指定特定繫結屬性上[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 您也可以藉由設定修改 POLLINGSTMT 作業的目標命名空間**PollingId**中的連線 URI 屬性。 如需詳細資訊，請參閱 <<c0> [ 支援在 Oracle 資料庫接收輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-oracle-database/support-for-receiving-polling-based-data-changed-messages-in-oracle-database.md)並[在 Oracle 資料庫配接器接收以輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md)。 輪詢作業的 SOAP 訊息結構的相關資訊，請參閱[輪詢作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-polling-operations2.md)。  

## <a name="configuring-a-polling-operation-with-oracle-database-adapter-binding-properties"></a>使用繫結屬性建立的 Oracle 資料庫配接器設定的輪詢作業  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]輪詢查詢和任何後續輪詢 PL/SQL 程式碼區塊在交易內執行。 下表摘要說明[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結屬性，您用來設定配接器接收資料變更訊息。 您必須指定這些繫結設定 Wcf-custom 或 Wcf-oracledb 時接收屬性中的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  


|         繫結屬性         |                                                                                                                                                                                                                                                                                                                描述                                                                                                                                                                                                                                                                                                                |
|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     **InboundOperationType**     |                                                                                                                                                                                                                                                               指定是否要執行通知的輪詢輸入作業。 預設值是**輪詢**。                                                                                                                                                                                                                                                                |
| **PolledDataAvailableStatement** |                                                                                                                                                                                              指定配接器執行，以判斷是否有任何資料可供輪詢 SQL 陳述式。 只有當可用的記錄時，預存程序指定**PollingStatement**屬性繫結將會執行。                                                                                                                                                                                              |
|       **PollingInterval**        |              指定間隔 （秒），此時[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]執行陳述式指定**PolledDataAvailableStatement**繫結屬性。 預設值為 500 的秒數。 輪詢間隔會決定後續輪詢間隔的時間間隔。 如果指定的間隔內執行的陳述式，則配接器會睡剩餘的時間間隔中。 預設值是`SELECT 1 FROM DUAL`，這表示配接器，必須繼續輪詢，無論資料表輪詢是否有資料。              |
|       **PollingStatement**       | 指定輪詢陳述式。 若要使用預存程序、 函數或封裝的程序或函式進行輪詢，您必須指定個別作業的整個要求訊息這個繫結屬性中。 要求訊息必須相同，您傳送給配接器，叫用的個別作業，做為輸出的作業。 預設值是 null。<br /><br /> 您必須指定的值**PollingStatement**繫結屬性，來啟用輪詢。 輪詢陳述式在沒有可供輪詢，取決於使用的資料時，才會執行**PolledDataAvailableStatement**繫結屬性。 |
|        **PollingAction**         |                                                                                                                                                                                        指定輪詢作業的動作。 您可以判斷特定的作業，從您為作業使用產生的中繼資料的輪詢動作[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。                                                                                                                                                                                        |
|      **PostPollStatement**       |                                                                                                                                                                                                                                                   指定執行所指定的陳述式之後的陳述式區塊**PollingStatement**屬性繫結會執行。                                                                                                                                                                                                                                                    |
|      **PollWhileDataFound**      |                                                                                                                               指定是否[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會忽略的輪詢間隔，並持續執行輪詢陳述式，如果資料可在所輪詢的資料表。 如果沒有資料可在資料表中，配接器會還原為執行指定的輪詢間隔輪詢陳述式。 預設值為 false。                                                                                                                               |

 如需這些屬性的更完整說明，請參閱[了解 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。 如需完整的說明，如何使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]輪詢 Oracle 資料庫，可深入閱讀。  

## <a name="how-this-topic-demonstrates-polling"></a>本主題將輪詢的示範  
 本主題示範如何使用預存程序之 Oracle 資料庫可以進行輪詢。 建立 BizTalk 專案，並產生您想要使用輪詢 Oracle 資料庫的預存程序的結構描述。 本主題中，我們會使用 GET_ACTIVITYS 預存程序來輪詢 ACCOUNTACTIVITY 資料表。 這個預存程序可與 ACCOUNT_PKG 封裝 SCOTT 結構描述中。 您可以執行 SQL 指令碼隨附的範例，在資料庫中建立這些物件。  

> [!NOTE]
>  中這個 ACCOUNTACTIVITY 資料表，其中資料庫資料表建立執行提供的指令碼範例的主題輪詢的協調流程。 若要輪詢的任何其他表格本主題中所述，您必須執行類似的程序。  

 為了示範輪詢作業，我們執行下列作業：  

-   指定的 SELECT 陳述式**PolledDataAvailableStatement**繫結屬性，以判斷其中資料表輪詢 (ACCOUNTACTIVITY) 有任何資料。 在此範例中，您可以設定為這個繫結屬性：  

    ```  
    SELECT COUNT (*) FROM ACCOUNTACTIVITY  
    ```  

     這可確保當配接器 ACCOUNTACTIVITY 資料表有一些記錄時，才會執行輪詢陳述式。  

-   執行預存程序 GET_ACTIVITYS，藉由提供的要求訊息的一部分**PollingStatement**繫結屬性。 這個預存程序會擷取 ACCOUNTACTIVITY 資料表中的所有資料列，然後就會從配接器的回應訊息。  

-   執行一部分的 PL/SQL 區塊**PostPollStatement**繫結屬性。 此陳述式會從 ACCOUNTACTIVITY 資料表移動所有資料到資料庫中的另一個資料表。 一旦發生這種情況，在下次**PollingStatement**會執行，它不會擷取任何資料，並因此 GET_ACTIVITYS 預存程序會傳回空白的回應訊息。  

-   更多資料新增至 ACCOUNTACTIVITY 資料表，直到您將繼續收到空的回應訊息。 因此，您必須重新擴展 ACCOUNTACTIVITY 資料表與新的記錄。 您可以執行 more_activity_data.sql 指令碼提供範例來這麼做。 執行此指令碼之後下, 一個輪詢作業會擷取新記錄插入至資料表。  

## <a name="how-to-receive-data-change-messages-from-oracle"></a>如何獲得 Oracle 的資料變更訊息  
 使用 Oracle database 上執行運算[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及下列程序性工作中所述[開發與 Oracle 資料庫的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)。 若要設定輪詢使用預存程序的 Oracle 資料庫配接器：  

1. 建立 BizTalk 專案，並產生您想要用於輪詢預存程序的結構描述。  

2. 從 Oracle 資料庫接收訊息的 BizTalk 專案中建立訊息。  

3. 建立協調流程，以從 Oracle 資料庫接收訊息，並將它們儲存到資料夾。  

4. 建置和部署 BizTalk 專案。  

5. 設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  

   > [!IMPORTANT]
   >  輸入的輪詢案例，您必須一律設定為單向接收埠。 雙向接收埠不支援的輸入作業。  

6. 啟動 BizTalk 應用程式。  

   本主題提供執行這些工作的指示。  

## <a name="generating-schema"></a>產生結構描述  
 您必須產生 GET_ACTIVITYS 作業的結構描述。 執行下列工作時產生結構描述使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  

- 選取合約類型作為**服務 （輸入作業）**。  

- 產生結構描述**GET_ACTIVITYS**程序。  

  如需如何產生結構描述的詳細資訊，請參閱[瀏覽、 搜尋及取得 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/browse-search-and-get-metadata-for-oracle-database-operations.md)。  

## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您稍早產生的結構描述會描述協調流程中的訊息所需的 「 類型 」。 訊息通常是一個變數，要為其類型會定義對應的結構。 一旦產生結構描述時，您必須訊息從 BizTalk 專案的協調流程檢視以將它的連結。  

 本主題中，您必須建立一個從 Oracle 接收訊息的訊息。  

 執行下列步驟來建立訊息，並將它們連結至結構描述。  

#### <a name="to-create-messages-and-link-to-schema"></a>若要建立訊息，並連結至結構描述  

1. BizTalk 專案中新增協調流程。 從 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下**新項目**。 輸入 BizTalk 協調流程的名稱，然後按一下**新增**。  

2. 如果它尚未開啟，請開啟 BizTalk 專案中，[協調流程檢視] 視窗。 按一下 **檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。  

3. 在 **協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。  

4. 以滑鼠右鍵按一下新建立的訊息，然後按**屬性 視窗**。  

5. 在 [**屬性**] 窗格**Message_1**，執行下列動作：  

   |使用|以進行此動作|  
   |--------------|----------------|  
   |識別碼|型別**接收**。|  
   |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*Polling.OracleEBSBindingSchema*，其中*輪詢*是 BizTalk 專案的名稱。 *OracleEBSBindingSchema*是針對產生的回應結構描述**GET_ACTIVITYS**預存程序。<br /><br /> **重要事項：** 因為輪詢是單向作業，配接器所產生的結構描述不包含 [回應] 節點中，因此只有一個根節點中沒有結構描述。 如果您使用這類結構描述訊息類型時，您必須識別結構描述所產生的結構描述的檔案名稱。<br /><br /> 例如，如果您建立雙向作業的結構描述，結構描述中的節點檔案名稱`OracleEBSBindingSchema`可能看起來像是 「 要求 」 和 「 回應 」。 如果您想要建立訊息對應至要求結構描述的協調流程中，您可以藉由尋找識別清單中的結構描述`OracleEBSBindingSchema.Request`。 不過，在輪詢作業中，唯一的節點是 「 輪詢 」，因為它並不容易找出您想要對應到，因為未列為單一節點的結構描述的結構描述\<schemafilename\>。\<rootnodename\>。 相反地，這類結構描述會列出依檔案名稱。 在此情況下，識別結構描述的唯一方式是依結構描述檔案名稱，例如 OracleEBSBindingSchema。|  

    [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] GET_ACTIVITYS 的輸入和輸出作業預存程序會產生結構描述。 您必須輸入作業使用的結構描述：  

   - 將協調流程的過程中建立訊息的對應。  

   - 若要擷取的動作，您必須指定**PollingAction**執行階段的繫結屬性。  

     您必須使用輸出作業的結構描述來取得要求訊息的一部分，您必須指定**PollingStatement**繫結屬性。  

## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]從 Oracle 接收以輪詢為基礎的資料變更訊息。 在此協調流程中，配接器接收的回應中執行預存程序，您必須指定要求訊息的一部分**PollingStatement**繫結屬性。 預存程序的回應訊息會儲存至檔案位置。 用於輪詢 Oracle 資料庫的一般協調流程會包含：  

- 接收和傳送圖形，從 Oracle 接收訊息，並分別將傳送至檔案的連接埠。  

- 單向接收埠從 Oracle 資料庫接收訊息。  

  > [!IMPORTANT]
  >  輸入的輪詢案例，您必須一律設定為單向接收埠。 雙向接收埠不支援的輸入作業。  

- 單向傳送埠以傳送輪詢回應從 Oracle 資料庫。  

  範例協調流程如下所示。  

  ![Oracle 輪詢查詢的協調流程](../../adapters-and-accelerators/adapter-oracle-database/media/6eddfe32-bfd0-4bd9-9e2a-fb4a7d0b53e3.gif "6eddfe32-bfd0-4bd9-9e2a-fb4a7d0b53e3")  

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
|因為 ACCOUNTACTIVITY 資料表沒有記錄現在PolledDataAvailableStatement不會傳回正值，因此配接器不會執行指定的陳述式PollingStatement繫結屬性。|如此一來，配接器用戶端不會取得任何輪詢訊息。*<br /><br /> 某些記錄明確插入 ACCOUNTACTIVITY 資料表之前，配接器用戶端不會收到任何其他的輪詢訊息。*<br /><br /> -設定**通訊模式**到*單向*<br /><br /> -設定**通訊方向**到*接收*|  
|SaveMessagePort|-設定**識別碼**到*SaveMessagePort*<br /><br /> -設定**型別**到*SaveMessagePortType*<br /><br /> -設定**通訊模式**到*單向*<br /><br /> -設定**通訊方向**到*傳送*|  

### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>為動作圖形指定訊息，並連接到連接埠  
 下表指定的屬性和屬性來指定動作圖形的訊息，以及連結至連接埠的訊息，您應該設定的值。 先前所述的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。  

|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveMessage|若要插入多筆記錄，您可以執行 more_activity_data.sql 指令碼提供範例。*<br /><br /> 在下一次執行此指令碼之後, **PolledDataAvailableStatement**會執行，它會傳回正值。*|  
|SaveMessage|若要插入多筆記錄，您可以執行 more_activity_data.sql 指令碼提供範例。*<br /><br /> 如此一來，配接器執行輪詢陳述式，並再次接收配接器用戶端的輪詢訊息。*|  

 您指定這些屬性之後，連線的訊息 圖形和連接埠和協調流程已完成。  

 您現在必須建置 BizTalk 方案，並將其部署至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 [將繼續輪詢，直到您明確停用接收埠從](../../core/building-and-running-orchestrations.md)管理主控台。  

## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在下**協調流程**在 BizTalk Server 管理主控台 窗格。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 如需逐步解說，請參閱 <<c0> [ 逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。

 設定應用程式包含：  

- 選取應用程式主機。  

- 對應您在您在 BizTalk Server 管理主控台中的實體連接埠的協調流程中建立的連接埠。 此協調流程中，您必須：  

  - 一旦產生繫結檔案時，您可以匯入的組態設定從檔案，讓您不需要建立傳送埠和接收相同的協調流程的連接埠。 這些訊息會以您指定接收埠的輪詢陳述式的回應。  

  - 定義實體的 Wcf-custom 或 Wcf-oracledb 單向接收埠。 此連接埠會輪詢 Oracle 資料庫。 如需如何建立接收埠，請參閱 <<c0> [ 手動設定 Oracle 資料庫配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md)。 請確定指定接收埠的下列繫結屬性。  


    |         繫結屬性         |                                                                                                                                                                                                                                                                                                                                                       ReplTest1                                                                                                                                                                                                                                                                                                                                                       |
    |----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    |     **InboundOperationType**     |                                                                                                                                                                                                                                                                                                                                             將此設為**輪詢**。                                                                                                                                                                                                                                                                                                                                              |
    | **PolledDataAvailableStatement** |                                                                                                                                                                                                                                        例如，此繫結將屬性設定為：<br /><br /> `SELECT COUNT (*) FROM ACCOUNTACTIVITY`<br /><br /> 這可確保當配接器 ACCOUNTACTIVITY 資料表有一些記錄時，才會執行輪詢陳述式。                                                                                                                                                                                                                                         |
    |        **PollingAction**         |                                                                                                                                                                                                                        從產生 GET_ACTIVITYS 程序的輸入訊息的結構描述中擷取輪詢動作。 此範例中，此繫結將屬性設定為 **<http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/PollingPackage/> ACCOUNT_PKG/GET_ACTIVITYS**。                                                                                                                                                                                                                        |
    |       **PollingStatement**       | 為此繫結屬性，指定要叫用 GET_ACTIVITYS 的要求訊息的預存程序。 您可以取得要求訊息結構描述所產生的輸出作業[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 您必須提供整個 XML 訊息做為輸入，這個繫結屬性。 例如，此繫結將屬性設定為：<br /><br /> `<GET_ACTIVITYS xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACTIVITY">   <INRECS>OPEN ? FOR SELECT * FROM ACCOUNTACTIVITY</INRECS> </GET_ACTIVITYS>`<br /><br /> GET_ACTIVITYS 預存程序會採用輸入的 REF CURSOR，做為參數。 |
    |      **PostPollStatement**       |                                                                                                                                                                                                                                                      指定後輪詢陳述式，將所有資料從 ACCOUNTACTIVITY 資料表移到另一個資料表。 例如，此繫結將屬性設定為：<br /><br /> `BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;`                                                                                                                                                                                                                                                       |

     如需不同的繫結屬性的詳細資訊，請參閱[了解 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。  

    > [!NOTE]
    >  我們建議您執行使用的輸入的操作時設定的交易隔離等級和交易等待時間[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 您可以藉由設定接收埠時新增的服務行為來這麼做。 如需有關如何新增服務行為的指示，請參閱[設定交易隔離等級和交易等待時間](../../adapters-and-accelerators/adapter-oracle-database/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-db.md)。  

## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 BizTalk 應用程式，用於輪詢 Oracle 資料庫。 如需有關啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。  

 在這個階段，請確定：  

-   Wcf-custom 或 Wcf-oracledb 單向接收埠，會輪詢 Oracle 使用指定的預存程序**PollingStatement**繫結屬性，正在執行。  

-   FILE 傳送埠，會從 Oracle 資料庫接收的訊息，正在執行。  

-   BizTalk 協調流程的作業正在執行。  

## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，下列的一組動作進行，相同的順序：  

-   執行配接器**PolledDataAvailableStatement**它會傳回正數的值，指出要執行指定的陳述式的介面卡**PollingStatement**繫結屬性。  

-   配接器執行 GET_ACTIVITYS 預存程序時指定**PollingStatement** ACCOUNTACTIVITY 資料表中的繫結屬性，並傳回所有資料列。 Oracle 資料庫的回應如下所示：  

    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <GET_ACTIVITYS xmlns=" http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/PollingPackage/ACCOUNT_PKG">  
      <OUTRECS>  
        <OUTRECSRecord xmlns=" http://Microsoft.LobServices.OracleDB/2007/03/ReferencedRecordTypes/SCOTT/ACCOUNT_PKG/GET_ACTIVITYS/SCOTT/GET_ACTIVITYS">  
          <TID>1</TID>   
          <ACCOUNT>100001</ACCOUNT>   
          <AMOUNT>500</AMOUNT>   
          <DESCRIPTION />   
          <TRANSDATE>2008-06-21T15:52:19</TRANSDATE>   
          <PROCESSED>n</PROCESSED>   
        </OUTRECSRecord>  
        <OUTRECSRecord xmlns=" http://Microsoft.LobServices.OracleDB/2007/03/ReferencedRecordTypes/SCOTT/ACCOUNT_PKG/GET_ACTIVITYS/SCOTT/GET_ACTIVITYS">  
          ......  
          ......   
        </OUTRECSRecord>  
        ......  
        ......  
      </OUTRECS>  
    </GET_ACTIVITYS>  
    ```  

-   配接器執行後輪詢陳述式，會將所有資料從 ACCOUNTACTIVITY 資料表都移到另一個資料表。  

-   輪詢間隔後，執行配接器再次**PolledDataAvailableStatement**。 因為 ACCOUNTACTIVITY 資料表沒有記錄現在**PolledDataAvailableStatement**不會傳回正值，因此配接器不會執行指定的陳述式**PollingStatement**繫結屬性。 如此一來，配接器用戶端不會取得任何輪詢訊息。  

-   某些記錄明確插入 ACCOUNTACTIVITY 資料表之前，配接器用戶端不會收到任何其他的輪詢訊息。 若要插入多筆記錄，您可以執行 more_activity_data.sql 指令碼提供範例。 在下一次執行此指令碼之後, **PolledDataAvailableStatement**會執行，它會傳回正值。 如此一來，配接器執行輪詢陳述式，並再次接收配接器用戶端的輪詢訊息。  

> [!NOTE]
>  [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]將繼續輪詢，直到您明確停用接收埠從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。 一旦產生繫結檔案時，您可以匯入的組態設定從檔案，讓您不需要建立傳送埠和接收相同的協調流程的連接埠。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用的 Oracle 資料庫配接器繫結](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md)。  

## <a name="see-also"></a>另請參閱  
 [使用 BizTalk Server 輪詢 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/poll-oracle-database-using-biztalk-server.md)