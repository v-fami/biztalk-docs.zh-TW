---
title: "使用預存程序的輪詢 Oracle E-business Suite |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9e89dfe-f33a-436b-94c6-be78e84d5efd
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f52d81f33e57aaa41873e82575cee057c4b858f0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="poll-oracle-e-business-suite-using-stored-procedures"></a>輪詢 Oracle E-business Suite 使用預存程序
您可以設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]來使用預存程序，若要連續輪詢 Oracle 資料庫接收定期的資料變更訊息。 您可以指定預存程序，為配接器執行定期輪詢 Oracle 資料庫的輪詢陳述式。  
  
 若要啟用輪詢，您必須指定 Wcf-custom 或 Wcf-oracleebs 的某些繫結屬性的接收埠。  如需如何配接器支援在輪詢的詳細資訊，請參閱[支援輸入呼叫使用輪詢](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md)。 輪詢作業的 SOAP 訊息結構的相關資訊，請參閱[輪詢作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-polling-operations1.md)。  
  
## <a name="configuring-a-polling-operation-with-oracle-e-business-adapter-binding-properties"></a>使用 Oracle E-business 配接器繫結屬性中設定輪詢作業  
 下表摘要說明[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]繫結，您用來設定配接器來接收資料變更訊息的屬性。 您必須指定這些繫結設定 Wcf-custom 或 Wcf-oracleebs 時接收屬性中的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
|繫結屬性|Description|  
|----------------------|-----------------|  
|**InboundOperationType**|指定您是否要執行**輪詢**或**通知**輸入作業。 預設值是**輪詢**。|  
|**PolledDataAvailableStatement**|指定的 SQL 陳述式來判斷是否可用於輪詢的任何資料執行配接器。 只有當可用的記錄時，預存程序指定為**PollingInput**繫結屬性將會執行。|  
|**PollingInterval**|指定間隔，以秒為單位，此時[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]執行陳述式指定**PolledDataAvailableStatement**繫結屬性。 預設值是 30 秒。 輪詢間隔會決定後續輪詢間隔時間。 如果指定的間隔內執行的陳述式，則配接器進入睡眠狀態的剩餘時間間隔中。|  
|**PollingInput**|指定輪詢陳述式。 若要輪詢使用預存程序，您必須指定這個繫結屬性的整個要求訊息。 要求訊息必須相同，您傳送給配接器叫用預存程序，做為輸出的作業。 預設值是 null。<br /><br /> 您必須指定的值**PollingInput**繫結內容來啟用輪詢。 輪詢陳述式在沒有進行輪詢，取決於可用的資料時，才會執行**PolledDataAvailableStatement**繫結屬性。|  
|**PollingAction**|指定輪詢作業的動作。 您可以判斷您的作業使用產生的中繼資料從特定作業的輪詢動作[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。|  
|**PostPollStatement**|指定執行所指定的陳述式之後的陳述式區塊**PollingInput**執行繫結屬性。|  
|**PollWhileDataFound**|指定是否[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]忽略的輪詢間隔，並持續執行輪詢陳述式，如果輪詢資料表中的可用資料。 如果沒有資料可在資料表中，配接器會還原為執行指定的輪詢間隔輪詢陳述式。 預設值為 false。|  
  
 如需這些屬性的更完整說明，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。 如需完整的說明，如何使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]輪詢 Oracle 資料庫，請閱讀下列各節。  
  
## <a name="how-this-topic-demonstrates-polling"></a>本主題示範輪詢的方式  
 本主題中，以示範如何[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]接收資料的支援變更訊息使用預存程序、 建立 BizTalk 專案和產生想要用於輪詢 Oracle 資料庫的預存程序的結構描述。 本主題中，我們會使用 GET_ACTIVITYS 預存程序來輪詢 ACCOUNTACTIVITY 資料表。 這個預存程序可與 ACCOUNT_PKG 封裝。 您可以執行這些範例資料庫中建立這些物件提供的 SQL 指令碼。  
  
> [!NOTE]
>  此主題輪詢，ACCOUNTACTIVITY 資料表，這基底資料庫建立的資料表執行提供的指令碼範例中的協調流程。 若要輪詢的任何其他資料表，包括介面資料表本主題中所述，您必須執行類似的程序。  
  
 若要示範輪詢作業，我們執行下列作業：  
  
-   指定 SELECT 陳述式**PolledDataAvailableStatement**繫結屬性，以判斷其中資料表輪詢 (ACCOUNTACTIVITY) 有任何資料。 在此範例中，您可以設定為這個繫結屬性：  
  
    ```  
    SELECT COUNT (*) FROM ACCOUNTACTIVITY  
    ```  
  
     這可確保當配接器 ACCOUNTACTIVITY 資料表具有一些記錄時才會執行輪詢陳述式。  
  
-   藉由提供要求訊息的一部分執行的預存程序 GET_ACTIVITYS， **PollingInput**繫結屬性。 這個預存程序會擷取 ACCOUNTACTIVITY 資料表中的所有資料列，您會從配接器收到回應訊息。  
  
-   執行一部分的 PL/SQL 區塊**PostPollStatement**繫結屬性。 這個陳述式會移動所有資料從 ACCOUNTACTIVITY 資料表在資料庫中的另一個資料表。 一旦發生這種情況，在下一次**PollingInput**將會執行，它將會不提取任何資料，因此 GET_ACTIVITYS 預存程序會傳回空白的回應訊息。  
  
-   更多資料加入至 ACCOUNTACTIVITY 資料表，直到您將繼續收到空的回應訊息。 因此，您必須重新擴展 ACCOUNTACTIVITY 資料表與新的記錄。 您可以藉由執行範例所提供的 more_activity_data.sql 指令碼。 執行這個指令碼之後下, 一個輪詢作業將會提取新的記錄插入至資料表。  
  
## <a name="how-to-receive-data-change-messages-from-oracle"></a>如何從 Oracle 接收資料變更訊息  
 使用 Oracle 資料庫上執行操作[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及下列程序性工作中所述[建置組塊，若要建立 Oracle E-business Suite 工作](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)。 若要設定輪詢使用預存程序的 Oracle 資料庫配接器，這些工作包括：  
  
1.  建立 BizTalk 專案，並產生您想要用於輪詢預存程序的結構描述。  
  
2.  從 Oracle 資料庫接收訊息的 BizTalk 專案中建立訊息。  
  
3.  建立協調流程，以從 Oracle 資料庫接收訊息，並將它們儲存到資料夾。  
  
4.  建置和部署 BizTalk 專案。  
  
5.  設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
    > [!IMPORTANT]
    >  輸入的輪詢案例，您必須一律先設定單向接收埠。 雙向接收埠不支援的輸入操作。  
  
6.  啟動 BizTalk 應用程式。  
  
 本主題提供執行這些工作的指示。  
  
## <a name="sample-based-on-this-topic"></a>根據本主題的範例  
 基礎的範例，PollingUsingStoredProc，本主題也會提供與 BizTalk Adapter Pack。 如需詳細資訊，請參閱[範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)。  
  
## <a name="generating-schema"></a>產生結構描述  
 您必須產生 GET_ACTIVITYS 作業的結構描述。 產生結構描述使用時，執行下列工作[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
-   選取合約類型為**服務 （輸入作業）**。  
  
-   產生結構描述的**GET_ACTIVITYS**程序。  
  
 如需如何產生結構描述的詳細資訊，請參閱[瀏覽、 搜尋和 Oracle E-business 作業取得中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您先前產生的結構描述會描述 「 類型 」 所需的協調流程中的訊息。 訊息通常是為其型別由對應的結構描述所定義的變數。 一旦產生結構描述時，您必須訊息連結之協調流程檢視中的 BizTalk 專案。  
  
 本主題中，您必須建立一個從 Oracle 接收訊息的訊息。  
  
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
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*Polling.OracleEBSBindingSchema*，其中*輪詢*是您的 BizTalk 專案的名稱。 *OracleEBSBindingSchema*是針對產生的回應結構描述**GET_ACTIVITYS**預存程序。<br /><br /> **重要事項：**因為輪詢是單向作業，配接器所產生的結構描述不包含回應 節點，因此只有一個根節點結構描述中。 如果您使用這類結構描述的訊息類型時，您必須識別結構描述所產生的結構描述的檔案名稱。<br /><br /> 例如，如果您建立雙向作業的結構描述，結構描述中的節點檔案名稱`OracleEBSBindingSchema`可能看起來像是 「 要求 」 和 「 回應 」。 如果您想要建立訊息對應至要求結構描述在協調流程中，您可以識別結構描述清單中的尋找`OracleEBSBindingSchema.Request`。 不過，在輪詢作業的唯一節點是 「 投票 」，因為它不容易識別您想要對應到單一節點的結構描述不會列為因為結構的描述\<schemafilename\>。\<rootnodename\>。 相反地，這類結構描述會列出依檔名。 在這種情況下，識別結構描述的唯一方法是由結構描述檔名，比方說，OracleEBSBindingSchema。|  
  
     [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]為 GET_ACTIVITYS 的傳入和傳出作業預存程序產生結構描述。 您必須使用結構描述的輸入作業：  
  
    -   將訊息對應建立協調流程的一部分。  
  
    -   若要擷取的動作，您必須指定**PollingAction**在執行階段繫結屬性。  
  
     您必須使用輸出作業的結構描述來取得要求訊息的一部分，您必須指定**PollingInput**繫結屬性。  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]從 Oracle 接收訊息以輪詢為基礎的資料變更。 在此協調流程中，配接器收到回應時所執行的預存程序，您所指定的要求訊息的一部分**PollingInput**繫結屬性。 預存程序的回應訊息會儲存到檔案位置。 用於輪詢 Oracle 資料庫的一般協調流程就會包含：  
  
-   接收和傳送圖形，從 Oracle 接收訊息，並分別將傳送至檔案連接埠。  
  
-   單向接收埠以接收來自 Oracle 資料庫的訊息。  
  
    > [!IMPORTANT]
    >  輸入的輪詢案例，您必須一律先設定單向接收埠。 雙向接收埠不支援的輸入操作。  
  
-   單向傳送埠以傳送輪詢回應從 Oracle 資料庫。  
  
 範例協調流程如下。  
  
 ![Oracle 輪詢查詢的協調流程](../../adapters-and-accelerators/adapter-oracle-database/media/6eddfe32-bfd0-4bd9-9e2a-fb4a7d0b53e3.gif "6eddfe32-bfd0-4bd9-9e2a-fb4a7d0b53e3")  
  
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
|OracleReceivePort|-設定**識別碼**至*OracleReceivePort*<br /><br /> -設定**類型**至*OracleReceivePortType*<br /><br /> -設定**通訊模式**至*單向*<br /><br /> -設定**通訊方向**至*接收*|  
|SaveMessagePort|-設定**識別碼**至*SaveMessagePort*<br /><br /> -設定**類型**至*SaveMessagePortType*<br /><br /> -設定**通訊模式**至*單向*<br /><br /> -設定**通訊方向**至*傳送*|  
  
### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>指定動作圖形訊息並連接至連接埠  
 下表指定屬性和其值，您應該設定來指定動作圖形的訊息，以及連結至連接埠的訊息。 圖形資料行中所列的名稱是 「 訊息 」 圖形的名稱，為顯示在協調流程中先前所述。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveMessage|-設定**訊息**至*接收*<br /><br /> -設定**作業**至*OracleReceivePort.Polling.Request*|  
|SaveMessage|-設定**訊息**至*接收*<br /><br /> -設定**作業**至*SaveMessagePort.Polling.Request*|  
  
 您指定這些屬性之後，連接的訊息 圖形和連接埠，而且您的協調流程已完成。  
  
 您現在必須建置 BizTalk 方案，並部署到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱[建置和執行協調流程](../../core/building-and-running-orchestrations.md)。
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 部署 BizTalk 專案之後，您稍早建立的協調流程會列在**協調流程**BizTalk Server 管理主控台 窗格。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 如需逐步解說，請參閱[逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。
  
 設定應用程式包括：  
  
-   選取應用程式的主機。  
  
-   對應至 BizTalk Server 管理主控台中的實體連接埠在協調流程中建立的連接埠。 此協調流程中，您必須：  
  
    -   定義位置上的硬碟和對應的檔案連接埠，其中 BizTalk 協調流程時，會從 Oracle 捨棄訊息。 這些訊息會在您指定的接收埠對輪詢陳述式。  
  
    -   定義實體的 WCF 自訂或 Wcf-oracleebs 單向接收埠。 此連接埠會輪詢 Oracle 資料庫。 如需有關如何建立接收埠，請參閱[手動設定的實體連接埠的繫結至 Oracle E-business 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md)。 請確定指定接收埠的下列繫結屬性。  
  
        |繫結屬性|值|  
        |----------------------|-----------|  
        |**InboundOperationType**|將此設**輪詢**。|  
        |**PolledDataAvailableStatement**|例如，此繫結將屬性設定為：<br /><br /> `SELECT COUNT (*) FROM ACCOUNTACTIVITY`<br /><br /> 這可確保當配接器 ACCOUNTACTIVITY 資料表具有一些記錄時才會執行輪詢陳述式。|  
        |**PollingAction**|從產生 GET_ACTIVITYS 程序的輸入訊息的結構描述中擷取輪詢動作。 此範例中，此繫結將屬性設定為**PollingPackageApis/應用程式/ACCOUNT_PKG/GET_ACTIVITYS**。|  
        |**PollingInput**|對於此繫結屬性，指定要叫用 GET_ACTIVITYS 的要求訊息的預存程序。 您可以取得要求訊息從結構描述所產生的輸出作業[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 您必須提供整個 XML 訊息做為輸入，此繫結屬性。 例如，此繫結將屬性設定為：<br /><br /> `<GET_ACTIVITYS xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/PackageApis/APPS/ACCOUNT_PKG">   <INRECS>OPEN ? FOR SELECT * FROM ACCOUNTACTIVITY</INRECS> </GET_ACTIVITYS>`<br /><br /> GET_ACTIVITYS 預存程序會接受輸入的 REF CURSOR，做為參數。|  
        |**PostPollStatement**|指定要從 ACCOUNTACTIVITY 資料表的所有資料都移到另一個資料表後輪詢陳述式。 例如，此繫結將屬性設定為：<br /><br /> `BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;`|  
  
         如需不同的繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  
  
        > [!IMPORTANT]
        >  如果您正在輪詢介面資料表，您必須藉由指定必要的繫結內容設定的應用程式內容。 如需設定應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
        > [!NOTE]
        >  我們建議您執行使用的輸入的操作時設定的交易隔離等級和異動逾時[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 您可以藉由新增服務行為設定 WCF 自訂時，或 Wcf-oracleebs 接收埠。 如需如何新增服務行為的指示，請參閱[設定交易隔離等級和交易逾時與 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-ebs.md)。  
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 BizTalk 應用程式用於輪詢 Oracle 資料庫。 如需啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。
  
 在這個階段，請確定：  
  
-   Wcf-custom 或 Wcf-oracleebs 單向接收埠，會輪詢 Oracle 使用指定的預存程序**PollingInput**繫結屬性，正在執行。  
  
-   檔案傳送埠，從 Oracle 資料庫接收訊息，正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，執行下列一進行，以相同順序：  
  
-   執行配接器**PolledDataAvailableStatement**傳回正值，指出要執行指定的陳述式的介面卡的**PollingInput**繫結屬性。  
  
-   配接器執行 GET_ACTIVITYS 預存程序時指定**PollingInput** ACCOUNTACTIVITY 資料表中的繫結屬性，會傳回所有資料列。 從 Oracle 資料庫回應如下所示：  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <GET_ACTIVITYS xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/PollingPackageApis/APPS/ACCOUNT_PKG">  
      <OUTRECS>  
        <OUTRECSRecord xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/ReferencedRecordTypes/APPS/ACCOUNT_PKG/GET_ACTIVITYS/APPS/GET_ACTIVITYS">  
          <TID>1</TID>   
          <ACCOUNT>100001</ACCOUNT>   
          <AMOUNT>500</AMOUNT>   
          <DESCRIPTION />   
          <TRANSDATE>2008-06-21T15:52:19</TRANSDATE>   
          <PROCESSED>n</PROCESSED>   
        </OUTRECSRecord>  
        <OUTRECSRecord xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/ReferencedRecordTypes/APPS/ACCOUNT_PKG/GET_ACTIVITYS/APPS/GET_ACTIVITYS">  
          ......  
          ......   
        </OUTRECSRecord>  
        ......  
        ......  
      </OUTRECS>  
    </GET_ACTIVITYS>  
    ```  
  
-   配接器執行後輪詢陳述式，將所有資料從 ACCOUNTACTIVITY 資料表移到另一個資料表。  
  
-   輪詢間隔後，配接器一次執行**PolledDataAvailableStatement**。 因為 ACCOUNTACTIVITY 資料表現在，不有任何記錄**PolledDataAvailableStatement**不會傳回正數值且因此配接器不會執行指定的陳述式**PollingInput**繫結屬性。 如此一來，配接器用戶端不會取得任何輪詢訊息。  
  
-   之前某些記錄明確插入 ACCOUNTACTIVITY 資料表配接器用戶端不會收到任何其他的輪詢訊息。 若要插入多個記錄，您可以執行範例所提供的 more_activity_data.sql 指令碼。 在下一次執行此指令碼之後, **PolledDataAvailableStatement**是它執行，則傳回正值。 如此一來，配接器執行輪詢陳述式，並再次接收配接器用戶端的輪詢訊息。  
  
> [!NOTE]
>  [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]將繼續輪詢直到您明確地停用接收埠從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。 一旦產生繫結檔案時，您可以匯入的組態設定從檔案，因此您不需要建立傳送埠和接收相同的協調流程連接埠。 如需繫結檔案的詳細資訊，請參閱[重複使用的 SQL 配接器繫結](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md)。  
  
## <a name="see-also"></a>請參閱  
 [使用 BizTalk Server 輪詢 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-biztalk-server.md)