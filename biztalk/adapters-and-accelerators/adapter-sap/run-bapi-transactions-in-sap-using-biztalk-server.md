---
title: "執行 SAP 使用 BizTalk Server 中的 BAPI 交易 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75ff5cf7-5e98-4d74-a13f-4de65c215d41
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79cfa3f1b799c4a96cdad7f4c9b89b4b594dc4d8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="run-bapi-transactions-in-sap-using-biztalk-server"></a>執行 SAP 使用 BizTalk Server 中的 BAPI 交易
[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]可讓配接器用戶端使用 SAP 系統上執行的交易[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 建立之前的交易協調流程，您必須先了解基本的案例將在其中執行的交易。 在一般交易案例中，多個作業 （例如，叫用 BAPI） 的要求訊息傳送至 SAP 系統。 這將被稱為 「 作業訊息 」。 協調流程必須從要求訊息中擷取每個作業訊息，並傳送至 SAP 系統的個別作業訊息。 協調流程傳送一個接著一個使用相同的連接。 協調流程會使用透過 BizTalk 對應的 XML 轉換中擷取個別的訊息中的 「 作業訊息 」。  
  
 作業會執行之後，協調流程必須認可或中止交易，藉由分別 BAPI_TRANSACTION_COMMIT 或 BAPI_TRANSACTION_ROLLBACK，傳送訊息。 這些會稱為 「 交易訊息 >。  
  
## <a name="how-does-the-adapter-enable-transactions-through-biztalk-server"></a>配接器如何啟用交易透過 BizTalk Server？  
 若要啟用 SAP 系統使用的交易[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]、 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]:  
  
-   提供開啟、 關閉、 重複使用和中止的訊息內容屬性。  
  
-   使用 BAPI_TRANSACTION_COMMIT 和 BAPI_TRANSACTION_ROLLBACK 認可或中止作業。 這些公開的 SAP 系統。  
  
 下表列出使用 BAPI_TRANSACTION_COMMIT 或 BAPI_TRANSACTION_ROLLBACK 具有屬性的一些指導方針：  
  
|訊息|OPEN|重複使用|CLOSE|中止|  
|-------------|----------|-----------|-----------|-----------|  
|第一則訊息 （作業訊息）|是|否|否|否|  
|後續的訊息 （作業訊息）|否|是|否|否|  
|BAPI_TRANSACTION_COMMIT （交易訊息）|否|否|是|否|  
|BAPI_TRANSACTION_ROLLBACK （交易訊息）|否|否|是|是|  
  
 在資料表中，「 是 」 表示要用於訊息的訊息內容屬性。 同樣地，「 否 」 表示不以用於訊息的訊息內容屬性。  
  
 摘要資料表：  
  
-   第一個訊息必須一律為作業訊息，而且必須只會使用開放式屬性。  
  
-   重複使用屬性時，必須使用後續的作業訊息。  
  
-   對應於 BAPI_TRANSACTION_COMMIT 認可交易的交易訊息必須使用關閉的屬性。  
  
-   交易訊息對應至 BAPI_TRANSACTION_ROLLBACK 中止交易，可以使用關閉或中止屬性。 如果使用中止，理想的情況下訊息必須是協調流程的例外狀況區塊中。  
  
## <a name="key-considerations-related-to-transactions-using-biztalk-server"></a>使用 BizTalk Server 交易相關的重要考量  
  
-   如果協調流程中有多個傳送埠，配接器會自動區隔每個連接埠所接收訊息的交易。 也就是說，交易無法跨越連接埠。  
  
-   在 SAP 的交易中的訊息不支援訊息重試次數。 因此，使用者應該設定為零的訊息重試的嘗試。  
  
-   配接器可能會產生非預期的結果標記為 [否] 上, 表中的組合。 您應該使用組合標示為 [是]。  
  
-   訊息傳送至配接器沒有訊息內容屬性會正常執行，而繫結至目前的交易內容。  
  
-   BAPI_TRANSACTION_COMMIT 或 BAPI_TRANSACTION_ROLLBACK 理想的情況下應該是在協調流程中目前的交易內容中的最後一個訊息。  
  
 下列各節提供有關如何在使用 SAP 執行交易指示[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
## <a name="how-to-perform-a-transaction-on-an-sap-system"></a>如何在 SAP 系統上執行交易？  
 執行 SAP 系統使用的作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[建立的 SAP 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)。 若要執行 SAP 系統上的交易，這些工作包括：  
  
1.  建立 BizTalk 專案，並為您要執行交易的 RFC 產生結構描述。 此外，您必須 BAPI_TRANSACTION_COMMIT 和 BAPI_TRANSACTION_ROLLBACK Rfc 來產生結構描述。  
  
2.  建立傳送和從 SAP 系統接收訊息的 BizTalk 專案中的訊息。  
  
3.  建立協調流程會從要求訊息中擷取個別 < 作業訊息 >，並將它傳送給 SAP 系統。 根據要求訊息，協調流程也會決定是否要認可或回復交易。  
  
4.  建置和部署 BizTalk 專案。  
  
5.  設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
6.  啟動 BizTalk 應用程式。  
  
 本主題提供執行這些工作的指示。  
  
## <a name="sample-based-on-this-topic"></a>根據本主題的範例  
 基礎的範例，SAPTransaction，本主題隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱[適用於 SAP 配接器範例](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md)。  
  
## <a name="generating-schema"></a>產生結構描述  
 若要示範如何在 SAP 系統上執行的交易，您需要下列的結構描述：  
  
-   「 作業訊息 」 的 SAP 系統上執行作業。 傳送至配接器的要求訊息必須符合此結構描述。 這可以是任何使用者特有的結構描述包含任意數目的運算節點。 在本主題中，會使用結構描述 MultipleOrders.xsd。 結構描述也可當做交易範例的一部分隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]範例。 如需詳細資訊，請參閱[結構描述範例](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md)。  
  
-   執行 SAP 系統，例如，叫用 RFC 上的作業。 要執行作業的要求訊息必須符合此結構描述。 此結構描述必須利用產生[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。 本主題中，會叫用 BAPI_SALESORDER_CREATEFROMDAT2 RFC。 如需 RFC 的產生結構描述資訊，請參閱[瀏覽、 搜尋和 get 中繼資料中 SAP RFC 作業的](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md)。  
  
-   正在中止或認可交易。 此結構描述必須符合要求認可或中止交易。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] BAPI_TRANSACTION_COMMIT 和 BAPI_TRANSACTION_ROLLBACK RFC 為認可和復原作業分別使用。 您必須使用這些 rfc 來產生結構描述[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
> [!NOTE]
>  您必須確定所有必要的結構描述會加入至 BizTalk 專案。  
  
> [!IMPORTANT]
>  您必須加入參考 BizTalk 屬性結構描述以取得[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]到 BizTalk 專案。 結構描述檔案， *Microsoft.Adapters.SAP.BiztalkPropertySchema.dll*，會安裝[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝程式，通常是在\<安裝磁碟機\>: \Program Files\Microsoft BizTalk Adapter Pack\bin。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您先前產生的結構描述會描述 「 類型 」 所需的協調流程中的訊息。 訊息通常是為其型別由對應的結構描述所定義的變數。 您必須連結產生的結構描述您在第一個步驟中的訊息從 BizTalk 專案的 [協調流程檢視] 視窗。  
  
 建立之前的訊息，您必須決定要求訊息 （屬於 MultipleOrders.xsd 類型） 具有的 「 作業 」 節點的數目。 例如，假設要求訊息具有兩個作業訊息來叫用 BAPI_SALESORDER_CREATEFROMDAT2 RFC。 因此，您必須建立一個會產生這個 RFC 的結構描述的要求-回應訊息組。  
  
 您必須在 BizTalk 專案中建立下列兩則訊息。  
  
-   訊息，SendtoAdapter，將會傳送至協調流程的要求訊息。 此訊息必須對應至輸入訊息，也就是 MultipleOrders.xsd 的結構描述。  
  
-   作業的訊息，BAPIMessage，第一個傳送到 SAP 系統。 您也必須建立回應訊息，BAPIResponse，第一項作業的回應。 要求和回應訊息必須對應至產生的 BAPI_SALESORDER_CREATEFROMDAT2 RFC 的結構描述。  
  
-   訊息，BAPICommitMessage，認可作業。 您也必須建立回應訊息，BAPICommitResponse，對應的回應訊息。 要求和回應訊息必須對應到 BAPI_TRANSACTION_COMMIT RFC 的結構描述。  
  
-   訊息，BAPIRollbackMessage，復原作業。 您也必須建立回應訊息，BAPIRollbackResponse，對應的回應訊息。 要求和回應訊息必須對應到 BAPI_TRANSACTION_ROLLBACK RFC 的結構描述。  
  
 執行下列步驟來建立訊息，並將其連結至結構描述。  
  
#### <a name="to-create-messages-and-link-to-schema"></a>建立訊息，以及連結至結構描述  
  
1.  如果不是已開啟，請開啟協調流程檢視 BizTalk 專案。 按一下**檢視**，指向 **其他視窗**，然後按一下**協調流程檢視**。  
  
2.  在**協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。  
  
3.  以滑鼠右鍵按一下新建立的訊息，然後再選取**屬性 視窗**。  
  
4.  在**屬性**窗格**Message_1**，執行下列動作。  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|型別**SendToAdapter**。|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*SAPTransaction.MultipleOrders*，其中*SAPTransaction*是您的 BizTalk 專案的名稱。 *MultipleOrders*是要求訊息的結構描述。|  
  
5.  重複上述步驟，建立六個的多個訊息。 在**屬性**窗格，以新的訊息，執行下列動作。  
  
    |若要設定識別項|若要設定訊息類型|  
    |-----------------------|-------------------------|  
    |BAPIMessage|*SAPTransaction.SAPBindingSchema.BAPI_SALESORDER_CREATEFROMDAT2*|  
    |BAPIResponse|*SAPTransaction.SAPBindingSchema.BAPI_SALESORDER_CREATEFROMDAT2Response*|  
    |BAPICommitMessage|*SAPTransaction.SAPBindingSchema.BAPI_TRANSACTION_COMMIT*|  
    |BAPICommitResponse|*SAPTransaction.SAPBindingSchema.BAPI_TRANSACTION_COMMITResponse*|  
    |BAPIRollbackMessage|*SAPTransaction.SAPBindingSchema.BAPI_TRANSACTION_ROLLBACK*|  
    |BAPIRollbackResponse|*SAPTransaction.SAPBindingSchema.BAPI_TRANSACTION_ROLLBACKResponse*|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]來執行 SAP 系統中的交易。 在此協調流程中，卸除要求訊息已定義的接收位置。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]取用訊息，並將它傳遞至 SAP 系統。 從 SAP 系統的回應會儲存到另一個位置。  
  
 若要建立協調流程時的另一個考量是：  
  
-   將要求訊息的結構描述對應的 BAPI_SALESORDER_CREATEFROMDAT2 RFC。  
  
-   對應於 BAPI_TRANSACTION_COMMIT 和 BAPI_TRANSACTION_ROLLBACK RFC 的要求訊息的結構描述。  
  
 您可以使用 XML 轉換透過 BizTalk 對應來對應結構描述。 若要達成此目的，包含轉換 」 圖形在協調流程中。  
  
 最後，根據要求訊息是否已認可或中止交易的資訊，協調流程必須決定適當的訊息傳送到 SAP 系統。 若要達成此目的，包含 「 決定 」 圖形在協調流程中。  
  
 如需協調流程中包含的不同圖形的詳細資訊，請參閱**協調流程設計師 UI** [!INCLUDE[ui-guidance-developers-reference](../../includes/ui-guidance-developers-reference.md)]。
  
 SAP 交易範例協調流程如下。  
  
 ![在 SAP 執行交易的協調流程](../../adapters-and-accelerators/adapter-sap/media/727f82e9-51a9-4a94-9d0a-d05c17904bde.gif "727f82e9-51a9-4a94-9d0a-d05c17904bde")  
  
### <a name="adding-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息圖形指定下列屬性。 圖形資料行中所列的名稱是 「 訊息 」 圖形的名稱，為顯示上述的協調流程中。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveInputXML|Receive|-設定**名稱**至*ReceiveInputXML*<br /><br /> -設定**啟動**至*，則為 True*|  
|SendToLOB|Send|-設定**名稱**至*SendToLOB*|  
|ReceiveResponse|Receive|-設定**名稱**至*ReceiveResponse*<br /><br /> -設定**啟動**至*False*|  
|SendResponse|Send|-設定**名稱**至*SendResponse*|  
  
 因為要求訊息具有兩個 insert 訊息，您必須建立另一組的傳送和接收圖形，將訊息傳送至 SAP，並接收回應。 不過，因為 insert 訊息可能會認可或回復，必須建立第二個一組圖形決策區塊內。 您必須建立一組適用於認可圖形和圖形回復的另一組。  
  
> [!NOTE]
>  您可以藉由從 BizTalk 協調流程 [工具箱] 拖放 「 決定 」 圖形加入決策區塊。  
  
#### <a name="message-shapes-for-commit"></a>認可訊息圖形  
 下表列出適用於 「 認可路徑 」 的協調流程圖形。 在這裡，您不需要建立要求訊息的接收訊息。 從先前的 「 訊息 」 圖形會傳遞給要求訊息。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|SendBAPICommit|Send|-設定**名稱**至*SendBAPICommit*|  
|ReceiveCommitResponse|Receive|-設定**名稱**至*ReceiveCommitResponse*<br /><br /> -設定**啟動**至*False*|  
|SendResponse2|Send|-設定**名稱**至*SendResponse2*|  
  
#### <a name="message-shapes-for-abort"></a>中止訊息圖形  
 下表列出適用於 「 復原路徑 」 的協調流程圖形。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|SendBAPIRollback|Send|-設定**名稱**至*SendBAPIRollback*|  
|ReceiveRollbackResponse|Receive|-設定**名稱**至*ReceiveRollbackResponse*<br /><br /> -設定**啟動**至*False*|  
|SendResponse3|Send|-設定**名稱**至*SendResponse3*|  
  
### <a name="setting-the-rule-expression"></a>設定規則運算式  
 包含認可的訊息 圖形，並中止作業決策區塊內加入 「 決定 」 圖形。 若要指定的條件的協調流程會做出決定，您必須指定在 「 規則 」 圖形的運算式基礎所在的交易為被認可或回復。 例如，您必須指定 「 規則 」 圖形的下列運算式：  
  
```  
SendToAdapter.isCommit == true  
```  
  
 其中，SendToAdapter 是您建立的要求訊息的結構描述的訊息。 因此，在要求訊息時，如果`isCommit`標記設定為**True**，協調流程會採用 「 認可 」 路由。 否則，協調流程會將 「 復原 」 路由。  
  
 為了讓您能夠指定此條件運算式編輯器 中，您必須升級`isCommit`要求訊息傳送至配接器的訊息結構描述中的屬性。 本主題中，若要使用之輸入結構描述是 MultipleOrders.xsd。 您必須升級`isCommit`這個結構描述中的屬性。 如需升級屬性的詳細資訊，請參閱[升級屬性](../../core/promoting-properties.md)。
  
### <a name="adding-construct-message-shapes"></a>新增建構訊息圖形  
 如同先前討論，要求訊息傳送至配接器包含兩個 insert 訊息，然後認可或中止訊息。 您必須新增建構訊息 」 圖形，並轉換圖形來擷取個別作業的訊息傳送至 SAP 系統內的。 您也必須加入訊息指派 」 圖形來設定訊息內容屬性，啟用交易。  
  
#### <a name="the-first-construct-message-shape"></a>第一個建構訊息圖形  
 假設第一個 「 建構訊息 」 圖形稱為 「 ReceiveXML。 」 此圖形中，指定建構訊息 屬性為"BAPIMessage"。 按兩下以開啟 轉換 圖形**轉換組態** 對話方塊。 在對話方塊中：  
  
-   選擇建立新的對應。  
  
-   從左窗格中，選取**來源**來回**變數名稱**下拉式清單中選取*SendToAdapter*。  
  
-   從左窗格中，選取**目的地**來回**變數名稱**下拉式清單中選取*BAPIMessage*。  
  
-   按一下**確定**啟動 「 對應工具 」。 將要求訊息的結構描述對應至 BAPI_SALESORDER_CREATEFROMDAT2 的結構描述。 您可以使用**索引**運算質來建立來源與目的結構描述之間的對應。 **索引**運算質可讓您選取一系列的記錄中的特定記錄的資訊。  
  
     下圖顯示使用對應的結構描述**索引**運算質。  
  
     ![使用 Index 運算質對應的結構描述](../../adapters-and-accelerators/adapter-sap/media/d0ade577-ea74-4be3-a724-4ba19397d8d3.gif "d0ade577-ea74-4be3-a724-4ba19397d8d3")  
  
     如需有關使用**轉換組態**對話方塊中，請參閱**轉換組態對話方塊裡** [!INCLUDE[ui-guidance-developers-reference](../../includes/ui-guidance-developers-reference.md)]。
  
     如需有關如何使用索引運算質的詳細資訊，請參閱[索引運算質](../../core/index-functoid.md)。
       
     對應結構描述之後，您可以測試使用對應檔的屬性頁的對應。 如需詳細資訊，請參閱**<Map File>屬性頁對話方塊中，測試對應** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../../includes/ui-guidance-developers-reference.md)]。
  
 在 [訊息指派] 圖形中，指定訊息內容屬性，啟動交易。 例如，可能是第一個訊息的訊息內容屬性：  
  
```  
BAPIMessage(Microsoft.Adapters.SAP.BiztalkPropertySchema.ConnectionState) = "OPEN";  
```  
  
#### <a name="the-commit-construct-message-shape"></a>認可建構訊息圖形  
 假設建構訊息 」 圖形的認可作業稱為 「 CommitMessage。 」 此圖形中，指定建構訊息 屬性為"BAPICommitMessage"。 按兩下以開啟 轉換 圖形**轉換組態** 對話方塊。 在對話方塊中：  
  
-   選擇建立新的對應。  
  
-   從左窗格中，選取**來源**來回**變數名稱**下拉式清單中選取*SendToAdapter*。  
  
-   從左窗格中，選取**目的地**來回**變數名稱**下拉式清單中選取*BAPICommitMessage*。  
  
-   按一下 [確定] 以啟動 「 對應工具 」。 將要求訊息的結構描述對應至 BAPI_TRANSACTION_COMMIT 的結構描述。 因為 BAPI_TRANSACTION_COMMIT 節點不包含記錄的階層架構，您不需要包含針對此對應索引運算質。  
  
 在 [訊息指派] 圖形中，指定要認可的交易的訊息內容屬性。 例如，可能是第一個訊息的訊息內容屬性：  
  
```  
BAPICommitMessage(Microsoft.Adapters.SAP.BiztalkPropertySchema.ConnectionState) = "CLOSE";  
```  
  
#### <a name="the-rollback-construct-message-shape"></a>復原建構訊息圖形  
 假設建構訊息 」 圖形的回復作業稱為 「 RollbackMessage。 」 此圖形中，指定建構訊息 屬性為"BAPIRollbackMessage"。 按兩下以開啟 轉換 圖形**轉換組態** 對話方塊。 在對話方塊中：  
  
-   選擇建立新的對應。  
  
-   從左窗格中，選取**來源**來回**變數名稱**下拉式清單中選取*SendToAdapter*。  
  
-   從左窗格中，選取**目的地**來回**變數名稱**下拉式清單中選取*BAPIRollbackMessage*。  
  
-   按一下 [確定] 以啟動 「 對應工具 」。 將要求訊息的結構描述對應至 BAPI_TRANSACTION_ROLLBACK 的結構描述。 因為 BAPI_TRANSACTION_ROLLBACK 節點不包含記錄的階層架構，您不需要包含針對此對應索引運算質。  
  
 在訊息指派圖形中，指定訊息內容屬性，以復原交易。 例如，可能是第一個訊息的訊息內容屬性：  
  
```  
BAPIRollbackMessage(Microsoft.Adapters.SAP.BiztalkPropertySchema.ConnectionState) = "ABORT";  
```  
  
> [!IMPORTANT]
>  在一般情況下，對應至 BAPI_TRANSACTION_ROLLBACK 中止內容屬性的訊息必須使用例外狀況區塊中。  
  
### <a name="adding-ports"></a>新增連接埠  
 請確定您針對每個邏輯連接埠指定下列屬性。 所列的名稱*連接埠*資料行是連接埠的名稱，顯示在 協調流程中。  
  
 此協調流程，會建立三個連接埠。 第一個連接埠會從指定的資料夾挑選要求訊息。 第二個連接埠將訊息傳送至 SAP 系統，並接收回應。 第三個連接埠會將儲存至另一個資料夾的回應。 因此：  
  
-   第一個連接埠只會接收單一結構描述，也就是 MultipleOrders.xsd 的訊息。  
  
-   第二個連接埠傳送並接收 BAPI_SALESORDER_CREATEFROMDAT2 RFC 的結構描述的訊息。 此外，相同的連接埠將用於認可或回復交易。 因此，此連接埠也會收到訊息的結構描述 BAPI_TRANSACTION_COMMIT 和 BAPI_TRANSACTION_ROLLBACK Rfc。 若要啟用此功能，此連接埠，每一個都對應至特定訊息的結構描述中建立三個不同的作業。  
  
-   類似於第二個連接埠，此連接埠還會收到三個不同的結構描述的訊息。 因此，就必須建立三個不同的作業，在此連接埠。  
  
|通訊埠|屬性|  
|----------|----------------|  
|FileIn|-設定**識別碼**至*FileIn*<br /><br /> -設定**類型**至*FileInType*<br /><br /> -設定**通訊模式**至*單向*<br /><br /> -設定**通訊方向**至*接收*|  
|LOBPort|-設定**識別碼**至*LOBPort*<br /><br /> -設定**類型**至*LOBPortType*<br /><br /> -設定**通訊模式**至*要求-回應*<br /><br /> -設定**通訊方向**至*傳送接收*<br /><br /> 建立作業*BAPIMessage*。<br /><br /> 建立作業*CommitMessage*。 這項作業將用來傳送認可訊息。<br /><br /> 建立作業*RollbackMessage*。 這項作業將用來復原訊息傳送。|  
|SaveResponse|-設定**識別碼**至*SaveResponse*<br /><br /> -設定**類型**至*SaveResponseType*<br /><br /> -設定**通訊模式**至*單向*<br /><br /> -設定**通訊方向**至*傳送*。<br /><br /> 建立作業*BAPIMessage*。<br /><br /> 建立作業*CommitMessage*。 這項作業將用來儲存認可訊息的回應。<br /><br /> 建立作業*RollbackMessage*。 這項作業將用來儲存復原訊息的回應。|  
  
## <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>指定動作圖形訊息並連接至連接埠  
 下表指定屬性和其值設為指定的動作圖形，並將它們連結至連接埠的訊息。 所列的名稱*圖形*資料行名稱就是訊息圖形顯示在上述的協調流程中。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveInputXML|-設定**訊息**至*SendToAdapter*<br /><br /> -設定**作業**至*FileIn.Transaction.Request*|  
|SendToLOB|-設定**訊息**至*BAPIMessage*<br /><br /> -設定**作業**至*LOBPort.BAPIMessage.Request*|  
|ReceiveResponse|-設定**訊息**至*BAPIResponse*<br /><br /> -設定**作業**至*LOBPort.BAPIMessage.Response*|  
|SendResponse|-設定**訊息**至*BAPIResponse*<br /><br /> -設定**作業**至*SaveResponse.BAPIMessage.Request*|  
|SendBAPICommit|-設定**訊息**至*BAPICommitMessage*<br /><br /> -設定**作業**至*LOBPort.CommitMessage.Request*|  
|ReceiveCommitResponse|-設定**訊息**至*BAPICommitResponse*<br /><br /> -設定**作業**至*LOBPort.CommitMessage.Response*|  
|SendResponse2|-設定**訊息**至*BAPICommitResponse*<br /><br /> -設定**作業**至*SaveResponse.CommitMessage.Request*|  
|SendBAPIRollback|-設定**訊息**至*BAPIRollbackMessage*<br /><br /> -設定**作業**至*LOBPort.RollbackMessage.Request*|  
|ReceiveRollbackResponse|-設定**訊息**至*BAPIRollbackResponse*<br /><br /> -設定**作業**至*LOBPort.RollbackMessage.Response*|  
|SendResponse3|-設定**訊息**至*BAPIRollbackResponse*<br /><br /> -設定**作業**至*SaveResponse.RollbackMessage.Request*|  
  
 您指定這些屬性之後，連接的訊息 圖形和連接埠，而且您的協調流程已完成。  
  
## <a name="handling-exceptions"></a>處理例外狀況  
 在複雜的協調流程來執行 BAPI 交易類似，務必您追蹤的協調流程的狀態，報告錯誤發生時，以便您可以在發生時解決的問題。 BizTalk 協調流程會提供工具來處理錯誤，來維護狀態的協調流程，並修正問題發生時透過交易、 補償和例外狀況處理。  
  
 做為交易和例外狀況處理的架構，協調流程設計師 」 提供**範圍**圖形。 範圍可以包含交易類型、補償和任何數目的例外狀況處理常式。 範圍可以包含一個或多個區塊。 它有內文，並可以選擇性地有任意數目的例外狀況處理區塊附加到它。 如果 BAPI 交易是整個協調流程 （請參閱先前圖） 可以包含在範圍中。  
  
 若要攔截例外狀況，您必須新增**Catch 例外狀況**區塊至協調流程。 **攔截例外狀況**區塊會附加至結尾**範圍**協調流程設計師中的圖形。 在 BAPI 交易的情況下，您必須將 「 中止 」 常式到**Catch 例外狀況**封鎖，亦即，您必須加入下列 「 中止 」 常式：  
  
-   包含的轉換 （從輸入訊息中擷取的要求訊息） 和 （若要設定內容屬性） 「 訊息指派 」 圖形建構訊息圖形  
  
-   傳送和接收圖形。  
  
 SAP 交易範例[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)](SAPTransaction) 隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]示範太處理的例外狀況。 如需有關範例的詳細資訊，請參閱[適用於 SAP 配接器範例](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md)。  
  
 如需如何處理例外狀況的詳細資訊，在一般情況下，使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[使用交易和處理例外狀況](../../core/using-transactions-and-handling-exceptions.md)。
  
## <a name="add-the-biztalk-property-schema-to-biztalk"></a>BizTalk 屬性結構描述新增至 BizTalk  
 您可以在 BizTalk 專案中，加入 BizTalk 屬性結構描述的組件參考[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 您必須加入相同的組件當做 BizTalk 應用程式，也就是應用程式將會部署 BizTalk 專案中的資源。 結構描述檔案， *Microsoft.Adapters.SAP.BiztalkPropertySchema.dll*，會安裝[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]通常在安裝\<安裝磁碟機\>: \Program Files\Microsoft BizTalk 配接器Pack\bin。 沒有這個資源，您將無法部署專案。  
  
#### <a name="to-add-an-assembly-as-a-resource-in-biztalk"></a>若要加入做為資源在 BizTalk 組件  
  
1.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk 群組**，依序展開**應用程式**，，然後您要新增 BizTalk 組件的應用程式。  
  
3.  以滑鼠右鍵按一下**資源**，指向 **新增**，然後按一下  **BizTalk 組件**。  
  
4.  在**加入資源**對話方塊中，按一下 **新增**、 瀏覽至包含 BizTalk 組件檔案的資料夾中，選取 BizTalk 組件檔案，然後按一下**開啟**。  
  
5.  在**選項**，指定安裝至 GAC，BizTalk 組件的選項，然後按一下**確定**。  
  
 您必須現在可以建置 BizTalk 方案，然後再將它部署至 BizTalk Server。 如需詳細資訊，請參閱[建置和執行協調流程](../../core/building-and-running-orchestrations.md)。
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 部署 BizTalk 專案之後，您稍早建立的協調流程會列在**協調流程**BizTalk Server 管理主控台 窗格。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 如需有關如何設定應用程式的詳細資訊，請參閱[如何設定應用程式](../../core/how-to-configure-an-application.md)。
  
 設定應用程式包括：  
  
-   選取應用程式的主機。  
  
-   對應至 BizTalk Server 管理主控台中的實體連接埠在協調流程中建立的連接埠。 此協調流程中，您必須：  
  
    -   定義位置上的硬碟和對應的檔案連接埠，您將在此置放要求訊息。 BizTalk 協調流程會使用要求訊息，並將它傳送至 SAP 系統。  
  
    -   定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含 SAP 系統從回應的回應訊息。  
  
    -   定義將訊息傳送至 SAP 系統實體 Wcf-custom 或 WCF SAP 傳送埠。 如需如何建立連接埠相關資訊，請參閱[以手動方式設定 SAP 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md)。 因為傳送連接埠傳送和接收符合一個以上的結構描述的訊息，並執行兩個作業，您必須設定這兩個作業的動態動作。 如需動作的詳細資訊，請參閱[設定 SAP 系統的 SOAP 動作](../../adapters-and-accelerators/adapter-sap/configure-the-soap-action-for-the-sap-system.md)。 請確定您遵守時建立 WCF 自訂下列重要的考量或 WCF SAP 傳送連接埠來執行交易。  
  
        |設定下列項目|此值|  
        |-----------------------|-------------------|  
        |動作|傳送埠傳送和接收多個作業的訊息。 因此，每一項作業必須設定傳送埠上的動作。<br /><br /> `<BtsActionMapping>   <Operation Name="BAPIMessage" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/BAPI_SALESORDER_CREATEFROMDAT2" />   <Operation Name="CommitMessage" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/BAPI_TRANSACTION_COMMIT" />   <Operation Name="RollbackMessage" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/BAPI_TRANSACTION_ROLLBACK" /> </BtsActionMapping>`|  
        |EnableBizTalkCompatibilityMode|將此繫結屬性設定為**True**。|  
        |EnableConnectionPooling|將此繫結屬性設定為**False**之前執行任何交易。 在其中設定配接器和 BizTalk 之間的通道意外終止時的情況下，對應的連接會加入連接集區。 當另一個通道會開啟，而且新的通道會挑選相同的連接物件時，在舊的連接物件上未認可的交易也會認可時透過新的通道，在交易被認可。 若要避免這個問題，連接集區必須停用時執行交易。|  
  
        > [!NOTE]
        >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠的設定動作的相關資訊的繫結檔案。 您可以從 BizTalk Server 管理主控台來建立 （適用於傳出呼叫） 的傳送埠或接收埠 （適用於進行傳入呼叫時），以匯入此繫結檔案。 如需詳細資訊，請參閱[設定實體連接埠繫結使用連接埠繫結檔案至 SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md)。
  
        > [!IMPORTANT]
        >  您可以在 WCF 自訂設定備份傳輸或 WCF SAP 傳送埠，可讓您將訊息傳送至另一個 SAP 系統，如果主要傳輸無法正常運作。 不過，對於執行 SAP 系統，WCF 基礎交易[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不支援指定指向另一個 SAP 伺服器的備份傳輸。  
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 BizTalk 應用程式執行交易的 SAP 系統。 如需啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)，[如何啟動應用程式](../../core/how-to-start-and-stop-a-biztalk-application.md)。
  
 在這個階段，請確定：  
  
-   FILE 接收埠以接收要求訊息的協調流程執行。  
  
-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  
  
-   Wcf-custom 或 WCF SAP 傳送埠將訊息傳送至 SAP 系統正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，您必須在預先定義的位置中卸除協調流程的要求訊息。 要求訊息必須符合特定結構描述，比方說，MultipleOrders.xsd 結構描述。 比方說，若要建立 SAP 系統中的銷售訂單要求訊息，然後以認可作業：  
  
```  
<ns0:Orders xmlns:ns0="http://BAPISend.MultipleOrders">  
  <Order>  
      <ORDER_HEADER_IN>  
        <DOC_TYPE>TA</DOC_TYPE>  
        <SALES_ORG>1000</SALES_ORG>  
        <DISTR_CHAN>10</DISTR_CHAN>  
        <DIVISION>00</DIVISION>  
        <SALES_OFF>1000</SALES_OFF>  
        <REQ_DATE_H>20060901</REQ_DATE_H>  
        <PURCH_DATE>20060901</PURCH_DATE>  
        <PURCH_NO_C>Cust A</PURCH_NO_C>  
        <CURRENCY>EUR</CURRENCY>  
      </ORDER_HEADER_IN>  
      <ORDER_ITEMS_IN>  
          <MATERIAL>P-109</MATERIAL>  
          <PLANT>1000</PLANT>  
          <TARGET_QU>ST</TARGET_QU>  
      </ORDER_ITEMS_IN>  
      <ORDER_PARTNERS>  
          <PARTN_ROLE>AG</PARTN_ROLE>  
          <PARTN_NUMB>0000000257</PARTN_NUMB>  
      </ORDER_PARTNERS>  
    <RETURN></RETURN>  
  </Order>  
  <isCommit>true</isCommit>  
  <BAPI_TRANSACTION_COMMIT>  
  </BAPI_TRANSACTION_COMMIT>  
</ns0:Orders>  
```  
  
 協調流程取用訊息，並將它傳送至 SAP 系統。 從 SAP 系統的回應會儲存在其他的協調流程中定義的檔案位置。 針對上述的要求訊息，您會取得兩個回應訊息，另一個用於叫用 BAPI_SALESORDER_CREATEFROMDAT2 RFC 和另一個則用於使用 BAPI_TRANSACTION_COMMIT 的認可作業。  
  
 BAPI_SALESORDER_CREATEFROMDAT2 的回應是：  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<BAPI_SALESORDER_CREATEFROMDAT2Response xmlns="http://Microsoft.LobServices.Sap/2007/03/Rfc/">  
  <SALESDOCUMENT />   
  <ORDER_ITEMS_IN>  
    <BAPISDITM xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
      <ITM_NUMBER>0</ITM_NUMBER>   
      <HG_LV_ITEM>0</HG_LV_ITEM>   
      <PO_ITM_NO />   
      ......  
    </BAPISDITM>  
  </ORDER_ITEMS_IN>  
  <ORDER_PARTNERS>  
    <BAPIPARNR xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
      <PARTN_ROLE>AG</PARTN_ROLE>   
      <PARTN_NUMB>0000000257</PARTN_NUMB>   
      <ITM_NUMBER>0</ITM_NUMBER>   
      ......   
    </BAPIPARNR>  
  </ORDER_PARTNERS>  
</BAPI_SALESORDER_CREATEFROMDAT2Response>  
```  
  
 BAPI_TRANSACTION_COMMIT 的回應是：  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<BAPI_TRANSACTION_COMMITResponse xmlns="http://Microsoft.LobServices.Sap/2007/03/Rfc/">  
  <RETURN>  
    <TYPE xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/" />   
    <ID xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/" />   
    <NUMBER xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">0</NUMBER>   
    <MESSAGE xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/" />   
    <LOG_NO xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/" />   
    <LOG_MSG_NO xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">0</LOG_MSG_NO>   
    <MESSAGE_V1 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/" />   
    <MESSAGE_V2 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/" />   
    <MESSAGE_V3 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/" />   
    <MESSAGE_V4 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/" />   
    <PARAMETER xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/" />   
    <ROW xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">0</ROW>   
    <FIELD xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/" />   
    <SYSTEM xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/" />   
  </RETURN>  
</BAPI_TRANSACTION_COMMITResponse>  
```  
  
> [!NOTE]
>  如果要求訊息叫用 BAPI_TRANSACTION_ROLLBACK RFC，第二個回應會 BAPI_TRANSACTION_ROLLBACK。  
  
## <a name="possible-exceptions"></a>可能的例外狀況  
 如需例外狀況的資訊可能會遇到的 SAP 系統上執行的交易，使用 BizTalk Server 時，請參閱[例外狀況和錯誤處理與 SAP 配接器](../../adapters-and-accelerators/adapter-sap/exceptions-and-error-handling-with-the-sap-adapter.md)。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。 一旦您產生繫結檔案，可以組態設定匯入檔案中，因此您不需要建立傳送埠和接收埠，針對相同的協調流程。 如需繫結檔案的詳細資訊，請參閱[重複使用的 SAP 配接器繫結](../../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md)。  
  
## <a name="see-also"></a>請參閱  
[開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)