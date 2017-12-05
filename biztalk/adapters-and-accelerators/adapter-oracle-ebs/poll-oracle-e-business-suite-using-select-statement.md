---
title: "使用 SELECT 陳述式輪詢 Oracle E-business Suite |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81d70b36-8b80-4ab9-b97c-ee861aafbbac
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 83e5b40d8176b8e4ba448cadf1676013db8f2706
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="poll-oracle-e-business-suite-using-select-statement"></a>輪詢 Oracle E-business Suite 使用 SELECT 陳述式
您可以設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]接收定期的資料變更訊息，若要連續輪詢介面資料表使用 SELECT 陳述式，介面檢視、 資料表以及 Oracle E-business Suite 中的檢視。 您可以指定 SELECT 陳述式為輪詢 Oracle E-business Suite 會定期執行配接器的輪詢陳述式。 您也可以指定後續輪詢 PL/SQL 程式碼區塊後輪詢陳述式執行配接器。  
  
 若要啟用輪詢，您必須指定 Wcf-custom 或 Wcf-oracleebs 的某些繫結屬性的接收埠。  如需如何配接器支援在輪詢的詳細資訊，請參閱[支援輸入呼叫使用輪詢](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md)。 輪詢作業的 SOAP 訊息結構的相關資訊，請參閱[輪詢作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-polling-operations1.md)。  
  
## <a name="configuring-a-polling-operation-with-oracle-e-business-suite-adapter-binding-properties"></a>使用 Oracle E-business Suite 配接器繫結屬性中設定輪詢作業  
 下表摘要說明[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]繫結屬性，您用來設定配接器接收的資料變更的訊息。 您必須同時設定接收埠中的指定這些繫結屬性[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
|繫結屬性|Description|  
|----------------------|-----------------|  
|**InboundOperationType**|指定您是否要執行**輪詢**或**通知**輸入作業。 預設值是**輪詢**。|  
|**PolledDataAvailableStatement**|指定的 SQL 陳述式來判斷是否可用於輪詢的任何資料執行配接器。 只有當可用的記錄時，SELECT 陳述式您為指定**PollingInput**繫結屬性將會執行。|  
|**PollingInterval**|指定間隔，以秒為單位，此時[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]執行陳述式指定**PolledDataAvailableStatement**繫結屬性。 預設值是 30 秒。 輪詢間隔會決定後續輪詢間隔時間。 如果指定的間隔內執行的陳述式，則配接器進入睡眠狀態的剩餘時間間隔中。|  
|**PollingInput**|指定輪詢陳述式。 若要輪詢使用 SELECT 陳述式，您必須指定這個繫結屬性的 SELECT 陳述式。 預設值是 null。<br /><br /> 您必須指定的值**PollingInput**繫結內容來啟用輪詢。 輪詢陳述式在沒有進行輪詢，取決於可用的資料時，才會執行**PolledDataAvailableStatement**繫結屬性。|  
|**PollingAction**|指定輪詢作業的動作。 您可以判斷您的作業使用產生的中繼資料從特定作業的輪詢動作[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。|  
|**PostPollStatement**|指定執行所指定的陳述式之後的陳述式區塊**PollingInput**執行繫結屬性。|  
|**PollWhileDataFound**|指定是否[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]忽略的輪詢間隔，並持續執行輪詢陳述式，如果輪詢資料表中的可用資料。 如果沒有資料可在資料表中，配接器會還原為執行指定的輪詢間隔輪詢陳述式。 預設值為 false。|  
  
 如需這些屬性的更完整說明，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。 如需完整的說明，如何使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]進一步來輪詢 Oracle 資料庫，請閱讀。  
  
## <a name="how-this-topic-demonstrates-polling"></a>本主題示範輪詢的方式  
 本主題中，以示範如何[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]接收資料的支援變更使用 SELECT 陳述式的訊息、 建立 BizTalk 專案和產生結構描述的**輪詢**您想要輪詢的資料表的作業。 本主題中，我們會產生結構描述的**輪詢**作業**MS_SAMPLE_EMPLOYEE**介面中的資料表**應用程式物件程式庫**應用程式。 當您執行範例建立 Oracle E-business Suite 中的這些物件提供的 create_apps_artifacts.sql 指令碼時，會建立此資料表。  
  
 接下來，我們會使用以內容為基礎的路由 (CBR) 中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]設定應用程式將會接收來自輪詢訊息的接收埠與**MS_SAMPLE_EMPLOYEE**介面資料表，然後將它傳送至傳送埠。 在此情況下，我們將會檢查指定的接收位置，以及訊息路由至傳送埠的傳送埠上建立篩選。  
  
 若要示範輪詢作業，我們執行下列作業：  
  
-   指定 SELECT 陳述式**PolledDataAvailableStatement**繫結屬性，以判斷其中介面資料表輪詢 (MS_SAMPLE_EMPLOYEE) 有任何資料。 在此範例中，您可以設定為這個繫結屬性：  
  
    ```  
    SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE  
    ```  
  
     這可確保當配接器 MS_SAMPLE_EMPLOYEE 介面資料表具有一些記錄時才會執行輪詢陳述式。  
  
-   指定 SELECT 陳述式**PollingInput**繫結屬性。 此陳述式擷取 MS_SAMPLE_EMPLOYEE 介面資料表中的所有資料列。 在此範例中，您可以設定為這個繫結屬性：  
  
    ```  
    SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE  
    ```  
  
    > [!NOTE]
    >  FOR UPDATE 子句用於 SELECT 陳述式的相關資訊，請參閱[輪詢 Oracle E-business Suite 使用 SELECT 陳述式](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-select-statement.md)。  
  
-   指定 DELETE 陳述式的一部分**PostPollStatement**繫結屬性。 這個陳述式會從 MS_SAMPLE_EMPLOYEE 介面資料表刪除所有資料。 在此範例中，您可以設定為這個繫結屬性：  
  
    ```  
    DELETE FROM MS_SAMPLE_EMPLOYEE  
    ```  
  
     一旦發生這種情況，在下一次針對指定的陳述式**PollingInput**將會執行，它將會不提取任何資料。  
  
-   更多資料加入到 MS_SAMPLE_EMPLOYEE 介面資料表之前, 不會收到任何輪詢訊息。 因此，您必須重新擴展 MS_SAMPLE_EMPLOYEE 介面資料表與新的記錄。 您可以藉由執行範例所提供的 insert_apps_data.sql 指令碼。 執行這個指令碼之後下, 一個輪詢作業將會提取新的記錄插入至資料表。  
  
## <a name="how-to-receive-data-change-messages-from-oracle-e-business-suite"></a>如何從 Oracle E-business Suite 接收資料變更訊息  
 使用 Oracle 資料庫上執行操作[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及下列程序性工作中所述[建立 Oracle E-business Suite 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)。 若要設定要輪詢 Oracle E-business Suite 使用 SELECT 陳述式的介面卡，這些工作包括：  
  
1.  建立 BizTalk 專案，並產生結構描述的**輪詢**您想要輪詢的介面資料表的作業。  
  
2.  建置和部署 BizTalk 專案。  
  
3.  設定的 BizTalk 應用程式藉由建立接收和傳送埠。 此外，新增篩選器的傳送埠，讓它會檢查在接收埠中，指定接收位置及輪詢訊息路由至傳送埠。  
  
    > [!IMPORTANT]
    >  輸入的輪詢案例，您必須一律先設定單向接收埠。 雙向接收埠不支援的輸入操作。  
  
4.  啟動 BizTalk 應用程式。  
  
 本主題提供執行這些工作的指示。  
  
## <a name="sample-based-on-this-topic"></a>根據本主題的範例  
 基礎的範例，PollingUsingSelectStatement，本主題也會提供與 BizTalk Adapter Pack。 如需詳細資訊，請參閱[範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)。  
  
## <a name="generating-schema"></a>產生結構描述  
 您必須產生的結構描述**輪詢**MS_SAMPLE_EMPLOYEE 介面資料表中的作業**應用程式物件程式庫**應用程式。 產生結構描述使用時，執行下列工作[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
-   選取合約類型為**服務 （輸入作業）**。  
  
-   產生結構描述的**輪詢**MS_SAMPLE_EMPLOYEE 介面資料表上的作業。 您可以選取的作業以及介面資料表從**應用程式為基礎的檢視**節點或**成品為基礎的檢視**節點。  
  
 如需如何產生結構描述的詳細資訊，請參閱[瀏覽、 搜尋和 Oracle E-business Suite 作業取得中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)。  
  
## <a name="building-and-deploying-the-biztalk-project"></a>建置和部署 BizTalk 專案  
 現在，您必須建置 BizTalk 方案，並將它部署到 BizTalk Server。 將解決方案部署到 BizTalk Server 的相關資訊，請參閱[從到 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 部署 BizTalk 專案之後，應用程式會列在**應用程式**BizTalk Server 管理主控台中的節點。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 設定應用程式的一部分，您必須在應用程式，建立一個接收埠與傳送埠，並使來自接收埠的所有訊息都路由至傳送埠，然後將篩選加入至傳送埠。  
  
 設定應用程式包括：  
  
-   選取應用程式的主機。  
  
-   建立接收和傳送埠。  
  
### <a name="creating-a-receive-port"></a>建立接收埠  
 您必須建立 Wcf-custom 或 Wcf-oracleebs 單向接收埠，會輪詢 Oracle 使用 SELECT 陳述式指定**PollingInput**繫結屬性。 如需有關如何建立接收埠，請參閱[手動設定的實體連接埠的繫結至 Oracle E-business 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md)。 在建立接收埠，確定您指定下列繫結屬性。  
  
 **進行輪詢**  
  
|繫結屬性|值|  
|----------------------|-----------|  
|**InboundOperationType**|將此設**輪詢**。|  
|**PolledDataAvailableStatement**|例如，此繫結將屬性設定為：<br /><br /> `SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE`|  
|**PollingAction**|從產生的結構描述擷取輪詢動作**輪詢**MS_SAMPLE_EMPLOYEE 介面資料表上的作業。 此範例中，此繫結將屬性設定為**InterfaceTables/輪詢/尋找說明/應用程式/MS_SAMPLE_EMPLOYEE**。|  
|**PollingInput**|這個繫結屬性，指定 SELECT 陳述式擷取由 MS_SAMPLE_EMPLOYEE 介面資料表的所有記錄。 例如，此繫結將屬性設定為：<br /><br /> `SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE`|  
|**PostPollStatement**|指定從 MS_SAMPLE_EMPLOYEE 介面資料表刪除所有資料後輪詢陳述式。 例如，此繫結將屬性設定為：<br /><br /> `DELETE FROM MS_SAMPLE_EMPLOYEE`|  
  
 **設定應用程式內容**  
  
 如果您正在執行 Oracle E-business Suite 成品上的作業，您必須指定設定的應用程式內容的適當繫結屬性值。 如需應用程式內容和設定應用程式內容所需的繫結屬性的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
 此範例中，指定適當的值**oracleUserName**， **oraclePassword**，和**oracleEBSResponsibility**繫結屬性。  
  
> [!NOTE]
>  我們建議您執行使用的輸入的操作時設定的交易隔離等級和異動逾時[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 您可以藉由設定接收埠時新增服務行為。 如需如何新增服務行為的指示，請參閱[設定交易隔離等級和交易逾時與 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-ebs.md)。  
  
### <a name="creating-a-send-port"></a>建立傳送埠  
 定義在硬碟上的位置，並建立對應的 FILE 傳送埠其中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]會從 Oracle 卸除訊息。 這些訊息會在您指定的接收埠對輪詢陳述式。 如需如何建立傳送埠相關資訊，請參閱[手動設定的實體連接埠的繫結至 Oracle E-business 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md)。  
  
 您也必須將篩選器的傳送埠上加入路由傳送訊息從接收位置。 若要新增至傳送埠的篩選：  
  
1.  按兩下要開啟的傳送埠**傳送埠屬性** 對話方塊。  
  
2.  在**傳送埠屬性**對話方塊中，按一下 [**篩選**] 索引標籤。  
  
3.  使用下列值：  
  
    -   在**屬性**清單中，按一下**BTS。ReceivePortName**。  
  
    -   在**運算子**清單中，按一下 **==** 。  
  
    -   在**值**欄位中，指定接收埠名稱。  
  
4.  在**傳送埠屬性**對話方塊中，按一下 **確定**。  
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動輪詢 Oracle E-business Suite 的 BizTalk 應用程式。 如需啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。  
  
 在這個階段，請確定：  
  
-   Wcf-custom 或 Wcf-oracleebs 單向接收埠，會輪詢 Oracle 使用 SELECT 陳述式指定**PollingInput**繫結屬性，正在執行。  
  
-   檔案傳送埠，從 Oracle 資料庫接收訊息，正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，執行下列一進行，以相同順序：  
  
-   執行配接器**PolledDataAvailableStatement**傳回正值，指出要執行指定的陳述式的介面卡的**PollingInput**繫結屬性。  
  
-   執行 SELECT 陳述式的配接器**PollingInput** MS_SAMPLE_EMPLOYEE 介面資料表中的繫結屬性，會傳回所有資料列。 從 Oracle E-business Suite 回應如下所示：  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <Poll xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/FND/APPS/MS_SAMPLE_EMPLOYEE">   
      <DATA>   
        <SelectRecord xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/TableViewRecord/APPS/MS_SAMPLE_EMPLOYEE">   
         <EMP_NO>10002</EMP_NO>   
         <NAME>JEFF PRICE</NAME>   
         <DESIGNATION>MANAGER</DESIGNATION>   
         <SALARY>25000</SALARY>   
         <JOIN_DATE>2007-12-15T00:00:00</JOIN_DATE>   
        </SelectRecord>   
        <SelectRecord xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/TableViewRecord/APPS/MS_SAMPLE_EMPLOYEE">   
         <EMP_NO>10003</EMP_NO>   
         <NAME>DON HALL</NAME>   
         <DESIGNATION>ACCOUNTANT</DESIGNATION>   
         <SALARY>12000</SALARY>   
         <JOIN_DATE>2005-10-29T00:00:00</JOIN_DATE>   
        </SelectRecord>   
        …        
        <SelectRecord xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/TableViewRecord/APPS/MS_SAMPLE_EMPLOYEE">   
         …   
        </SelectRecord>   
        …   
      </DATA>   
    </Poll>  
    ```  
  
-   配接器執行後輪詢陳述式，從 MS_SAMPLE_EMPLOYEE 介面資料表中刪除所有資料。  
  
-   輪詢間隔後，配接器一次執行**PolledDataAvailableStatement**。 因為 MS_SAMPLE_EMPLOYEE 介面資料表現在，不有任何記錄**PolledDataAvailableStatement**不會傳回正數值且因此配接器不會執行指定的陳述式**PollingInput**繫結屬性。 如此一來，配接器用戶端不會取得任何輪詢訊息。  
  
-   之前某些記錄明確插入 MS_SAMPLE_EMPLOYEE 介面資料表配接器用戶端不會收到任何其他的輪詢訊息。 若要插入多個記錄，您可以執行範例所提供的 insert_apps_data.sql 指令碼。 在下一次執行此指令碼之後, **PolledDataAvailableStatement**是它執行，則傳回正值。 如此一來，配接器執行輪詢陳述式，並再次接收配接器用戶端的輪詢訊息。  
  
> [!NOTE]
>  [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]將繼續輪詢直到您明確地停用接收埠從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。 一旦產生繫結檔案時，您可以匯入的組態設定從檔案，因此您不需要建立傳送埠和接收埠。 如需繫結檔案的詳細資訊，請參閱[重複使用配接器繫結與 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md)。  
  
## <a name="see-also"></a>請參閱  
 [輪詢 Oracle E-business Suite 使用 BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-biztalk-server.md)