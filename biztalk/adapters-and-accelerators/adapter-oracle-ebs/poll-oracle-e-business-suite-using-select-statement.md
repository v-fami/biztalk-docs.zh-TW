---
title: 使用 SELECT 陳述式的輪詢 Oracle E-business Suite |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81d70b36-8b80-4ab9-b97c-ee861aafbbac
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1eda3c0afb5998485977efddb8a69d47ed4b92a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015417"
---
# <a name="poll-oracle-e-business-suite-using-select-statement"></a>使用 SELECT 陳述式的輪詢 Oracle E-business Suite
您可以設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]接收定期的資料變更訊息，若要連續輪詢介面資料表使用 SELECT 陳述式，介面檢視、 資料表以及 Oracle E-business Suite 中的檢視。 您可以指定 SELECT 陳述式來輪詢 Oracle E-business Suite 會定期執行配接器輪詢陳述式。 您也可以指定後續輪詢 PL/SQL 程式碼區塊，配接器執行後輪詢陳述式。  

 若要啟用輪詢，您必須指定特定繫結屬性，Wcf-custom 或 Wcf-oracleebs 接收埠。  如需配接器如何支援輪詢的詳細資訊，請參閱[支援的輸入呼叫使用輪詢](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md)。 輪詢作業的 SOAP 訊息結構的相關資訊，請參閱[輪詢作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-polling-operations1.md)。  

## <a name="configuring-a-polling-operation-with-oracle-e-business-suite-adapter-binding-properties"></a>使用 Oracle E-business Suite 配接器繫結屬性中設定輪詢作業  
 下表摘要說明[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]繫結屬性，您用來設定配接器接收資料變更訊息。 您必須在設定接收埠中的指定這些繫結屬性[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  


|         繫結屬性         |                                                                                                                                                                                                                            描述                                                                                                                                                                                                                             |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     **InboundOperationType**     |                                                                                                                                                                          指定是否要執行**輪詢**或是**通知**輸入作業。 預設值是**輪詢**。                                                                                                                                                                          |
| **PolledDataAvailableStatement** |                                                                                                             指定配接器執行，以判斷是否有任何資料可供輪詢 SQL 陳述式。 只有當可用的記錄時，SELECT 陳述式您指定的**PollingInput**屬性繫結將會執行。                                                                                                              |
|       **PollingInterval**        | 指定間隔 （秒），此時[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]執行陳述式指定**PolledDataAvailableStatement**繫結屬性。 預設值是 30 秒。 輪詢間隔會決定後續輪詢間隔的時間間隔。 如果指定的間隔內執行的陳述式，則配接器會睡剩餘的時間間隔中。 |
|         **PollingInput**         |                         指定輪詢陳述式。 若要使用的 SELECT 陳述式進行輪詢，您必須指定這個繫結屬性的 SELECT 陳述式。 預設值是 null。<br /><br /> 您必須指定的值**PollingInput**繫結屬性，來啟用輪詢。 輪詢陳述式在沒有可供輪詢，取決於使用的資料時，才會執行**PolledDataAvailableStatement**繫結屬性。                          |
|        **PollingAction**         |                                                                                                    指定輪詢作業的動作。 您可以判斷特定的作業，從您為作業使用產生的中繼資料的輪詢動作[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。                                                                                                     |
|      **PostPollStatement**       |                                                                                                                                                                  指定執行所指定的陳述式之後的陳述式區塊**PollingInput**屬性繫結會執行。                                                                                                                                                                  |
|      **PollWhileDataFound**      |                                    指定是否[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會忽略的輪詢間隔，並持續執行輪詢陳述式，如果資料可在所輪詢的資料表。 如果沒有資料可在資料表中，配接器會還原為執行指定的輪詢間隔輪詢陳述式。 預設值為 false。                                     |

 如需這些屬性的更完整說明，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。 如需完整的說明，如何使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]輪詢 Oracle 資料庫，可深入閱讀。  

## <a name="how-this-topic-demonstrates-polling"></a>本主題將輪詢的示範  
 本主題中，以示範如何[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]接收資料的支援變更使用 SELECT 陳述式的訊息、 建立 BizTalk 專案，並產生結構描述**輪詢**您想要輪詢的資料表作業。 本主題中，我們會產生結構描述**輪詢**作業**MS_SAMPLE_EMPLOYEE**中的介面資料表**應用程式物件程式庫**應用程式。 當您執行提供的範例，在 Oracle E-business Suite 中建立這些物件的 create_apps_artifacts.sql 指令碼時，會建立此資料表。  

 接下來，我們將使用以內容為基礎的路由 (CBR) 中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]若要使用之接收埠會接收來自的輪詢訊息的設定應用程式**MS_SAMPLE_EMPLOYEE**介面資料表，並再將它路由傳送至傳送埠。 在此情況下，我們將建立篩選條件會檢查指定接收位置，並將訊息會路由至傳送埠的傳送埠上。  

 為了示範輪詢作業，我們執行下列作業：  

-   指定的 SELECT 陳述式**PolledDataAvailableStatement**繫結屬性，以判斷其中介面資料表輪詢 (MS_SAMPLE_EMPLOYEE) 有任何資料。 在此範例中，您可以設定為這個繫結屬性：  

    ```  
    SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE  
    ```  

     這可確保當配接器 MS_SAMPLE_EMPLOYEE 介面資料表有一些記錄時，才會執行輪詢陳述式。  

-   指定的 SELECT 陳述式**PollingInput**繫結屬性。 此陳述式擷取 MS_SAMPLE_EMPLOYEE 介面資料表中的所有資料列。 在此範例中，您可以設定為這個繫結屬性：  

    ```  
    SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE  
    ```  

    > [!NOTE]
    >  FOR UPDATE 子句用於 SELECT 陳述式的相關資訊，請參閱[輪詢 Oracle E-business Suite 使用 SELECT 陳述式](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-select-statement.md)。  

-   指定 DELETE 陳述式的一部分**PostPollStatement**繫結屬性。 此陳述式會從 MS_SAMPLE_EMPLOYEE 介面資料表刪除所有資料。 在此範例中，您可以設定為這個繫結屬性：  

    ```  
    DELETE FROM MS_SAMPLE_EMPLOYEE  
    ```  

     一旦發生這種情況，在下一次針對指定的陳述式**PollingInput**會執行，它不會擷取任何資料。  

-   更多資料新增至 MS_SAMPLE_EMPLOYEE 介面資料表之前，不會收到任何輪詢訊息。 因此，您必須重新擴展 MS_SAMPLE_EMPLOYEE 介面資料表與新的記錄。 您可以執行 insert_apps_data.sql 指令碼提供範例來這麼做。 執行此指令碼之後下, 一個輪詢作業會擷取新記錄插入至資料表。  

## <a name="how-to-receive-data-change-messages-from-oracle-e-business-suite"></a>如何從 Oracle E-business Suite 接收資料變更訊息  
 使用 Oracle database 上執行運算[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及下列程序性工作中所述[建立 Oracle E-business Suite 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)。 若要設定配接器輪詢 Oracle E-business Suite 使用 SELECT 陳述式，這些工作如下：  

1. 建立 BizTalk 專案，並產生結構描述**輪詢**您想要輪詢的介面資料表的作業。  

2. 建置和部署 BizTalk 專案。  

3. 設定的 BizTalk 所建立的應用程式接收和傳送埠。 此外，因此，它會檢查在接收埠中，指定的接收位置輪詢訊息會路由傳送至傳送埠，請傳送埠上加入篩選條件。  

   > [!IMPORTANT]
   >  輸入的輪詢案例，您必須一律設定為單向接收埠。 雙向接收埠不支援的輸入作業。  

4. 啟動 BizTalk 應用程式。  

   本主題提供執行這些工作的指示。  

## <a name="sample-based-on-this-topic"></a>根據本主題的範例  
 BizTalk Adapter Pack 也提供基礎的範例，PollingUsingSelectStatement，本主題。 如需詳細資訊，請參閱 <<c0> [ 範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)。  

## <a name="generating-schema"></a>產生結構描述  
 您必須產生的結構描述**輪詢**MS_SAMPLE_EMPLOYEE 介面資料表中的作業**應用程式物件程式庫**應用程式。 執行下列工作時產生結構描述使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  

- 選取合約類型作為**服務 （輸入作業）**。  

- 產生結構描述**輪詢**MS_SAMPLE_EMPLOYEE 介面資料表上的執行作業。 您可以選取作業和介面資料表可能是來自**應用程式為基礎的檢視**節點或**成品-基礎的檢視**節點。  

  如需如何產生結構描述的詳細資訊，請參閱[瀏覽、 搜尋及取得 Oracle E-business Suite 作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)。  

## <a name="building-and-deploying-the-biztalk-project"></a>建置和部署 BizTalk 專案  
 現在，您必須建置 BizTalk 方案，並將它部署到 BizTalk Server。 將方案部署到 BizTalk Server 的相關資訊，請參閱[從 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。

## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 您已部署的 BizTalk 專案之後，應用程式會列在下**應用程式**BizTalk Server 管理主控台中的節點。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 在設定應用程式，您必須建立接收埠和傳送埠的應用程式，並使來自接收埠的所有訊息都路由至傳送埠，然後將篩選新增至傳送埠。  

 設定應用程式包含：  

-   選取應用程式主機。  

-   建立接收和傳送埠。  

### <a name="creating-a-receive-port"></a>建立接收埠  
 您必須建立 Wcf-custom 或 Wcf-oracleebs 單向接收埠，會輪詢 Oracle 使用 SELECT 陳述式指定**PollingInput**繫結屬性。 如需有關如何建立接收埠，請參閱[手動設定實體連接埠繫結來 Oracle E-business 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md)。 在建立接收埠，請確定您指定下列的繫結屬性。  

 **進行輪詢**  

|繫結屬性|ReplTest1|  
|----------------------|-----------|  
|**InboundOperationType**|將此設為**輪詢**。|  
|**PolledDataAvailableStatement**|例如，此繫結將屬性設定為：<br /><br /> `SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE`|  
|**PollingAction**|從產生的結構描述中擷取輪詢動作**輪詢**MS_SAMPLE_EMPLOYEE 介面資料表上的執行作業。 此範例中，此繫結將屬性設定為**InterfaceTables/輪詢/尋找說明/APPS/MS_SAMPLE_EMPLOYEE**。|  
|**PollingInput**|為此繫結屬性，指定 SELECT 陳述式來擷取 MS_SAMPLE_EMPLOYEE 介面資料表中的所有記錄。 例如，此繫結將屬性設定為：<br /><br /> `SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE`|  
|**PostPollStatement**|指定後輪詢陳述式，從 MS_SAMPLE_EMPLOYEE 介面資料表刪除所有資料。 例如，此繫結將屬性設定為：<br /><br /> `DELETE FROM MS_SAMPLE_EMPLOYEE`|  

 **設定應用程式內容**  

 如果您執行於 Oracle E-business Suite 成品的作業，您必須指定要設定應用程式內容的適當繫結屬性的值。 如需有關應用程式內容和設定應用程式內容所需的繫結屬性的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  

 此範例中，指定適當的值，如**oracleUserName**， **oraclePassword**，並**oracleEBSResponsibility**繫結屬性。  

> [!NOTE]
>  我們建議您執行使用的輸入的操作時設定的交易隔離等級和交易等待時間[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 您可以藉由設定接收埠時新增的服務行為來這麼做。 如需有關如何新增服務行為的指示，請參閱[設定交易隔離等級和交易等待時間，使用 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-ebs.md)。  

### <a name="creating-a-send-port"></a>建立傳送埠  
 定義在硬碟上的位置，並建立對應的 FILE 傳送埠其中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]會從 Oracle 卸除訊息。 這些訊息會以您指定接收埠的輪詢陳述式的回應。 如需有關如何建立傳送埠的資訊，請參閱 <<c0> [ 手動設定實體連接埠繫結來 Oracle E-business 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md)。  

 您必須也加入篩選器在傳送埠將訊息路由傳送從接收位置。 若要新增至傳送埠的篩選：  

1.  按兩下 [傳送埠，以開啟**傳送埠屬性**] 對話方塊。  

2.  在 **傳送埠屬性** 對話方塊中，按一下**篩選** 索引標籤。  

3.  使用下列值：  

    -   在 **屬性**清單中，按一下**BTS。ReceivePortName**。  

    -   在 **運算子**清單中，按一下**==**。  

    -   在 **值**欄位中，指定接收埠名稱。  

4.  在 [**傳送埠屬性**] 對話方塊中，按一下**確定**。  

## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動輪詢 Oracle E-business Suite 的 BizTalk 應用程式。 如需有關啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。  

 在這個階段，請確定：  

-   Wcf-custom 或 Wcf-oracleebs 單向接收埠，會輪詢 Oracle 使用 SELECT 陳述式指定**PollingInput**繫結屬性，正在執行。  

-   FILE 傳送埠，會從 Oracle 資料庫接收的訊息，正在執行。  

## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，下列的一組動作進行，相同的順序：  

-   執行配接器**PolledDataAvailableStatement**它會傳回正數的值，指出要執行指定的陳述式的介面卡**PollingInput**繫結屬性。  

-   配接器執行的 SELECT 陳述式**PollingInput** MS_SAMPLE_EMPLOYEE 介面資料表中的繫結屬性，並傳回所有資料列。 Oracle E-business Suite 的回應如下所示：  

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

-   輪詢間隔後，執行配接器再次**PolledDataAvailableStatement**。 因為 MS_SAMPLE_EMPLOYEE 介面資料表中不有任何記錄現在**PolledDataAvailableStatement**不會傳回正值，因此配接器不會執行指定的陳述式**PollingInput**繫結屬性。 如此一來，配接器用戶端不會取得任何輪詢訊息。  

-   某些記錄明確插入 MS_SAMPLE_EMPLOYEE 介面資料表之前，配接器用戶端不會收到任何其他的輪詢訊息。 若要插入多筆記錄，您可以執行 insert_apps_data.sql 指令碼提供範例。 在下一次執行此指令碼之後, **PolledDataAvailableStatement**會執行，它會傳回正值。 如此一來，配接器執行輪詢陳述式，並再次接收配接器用戶端的輪詢訊息。  

> [!NOTE]
>  [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]將繼續輪詢，直到您明確停用接收埠從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。 一旦產生繫結檔案時，您可以匯入的組態設定從檔案，讓您不需要建立傳送埠和接收埠。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用與 Oracle E-business Suite 配接器繫結](../../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md)。  

## <a name="see-also"></a>另請參閱  
 [輪詢 Oracle E-business Suite 使用 BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-biztalk-server.md)