---
title: 執行複合作業上使用 BizTalk Server 的 SQL Server |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 86fd2aa1-20c7-4b58-9f35-83ba0c959cf1
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62605fef85727311b2a2396463c2b43b690e86e2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004327"
---
# <a name="run-composite-operations-on-sql-server-using-biztalk-server"></a>執行 SQL Server 上使用 BizTalk Server 的複合作業
[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可讓配接器用戶端執行複合作業上的 SQL Server 資料庫。 複合作業可包括：  
  
- 插入、 更新和刪除作業。 選取的作業不支援複合作業的一部分。  
  
- 當做作業執行的預存程序。  
  
  單一複合作業可以有任意數目的這些作業，以任何順序。 比方說，您可以有兩個 Insert 作業後面是刪除作業，以及最後的預存程序執行。 此外，您可以有不同的資料庫資料表或檢視為目標的不同作業。 如需配接器如何支援複合作業的詳細資訊，請參閱[使用 SQL 配接器的 SQL Server 中執行複合作業](../../adapters-and-accelerators/adapter-sql/run-composite-operations-in-sql-server-using-the-sql-adapter.md)。 複合作業的 SOAP 訊息結構的相關資訊，請參閱[複合作業的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md)。  
  
> [!NOTE]
>  如果您正在執行具有使用者定義類型的資料行的資料表上的作業，請確定您參考[資料表和檢視與使用 SQL 配接器的使用者定義型別上的作業](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md)開始開發您的應用程式之前。  
  
## <a name="how-to-perform-composite-operations-on-sql-server"></a>如何執行 SQL Server 上的複合作業  
 使用 SQL Server 上執行運算[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及中所述的程序性工作[開發使用 SQL 配接器的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)。 若要執行複合作業上的 SQL Server 資料庫，這些工作如下：  
  
1. 建立 BizTalk 專案，並產生您想要叫用的所有作業的結構描述。  
  
2. 以手動方式建立結構描述檔案，其中包含您在上一個步驟中產生的所有結構描述的參考。  
  
3. 建立傳送和接收訊息，從 SQL Server 資料庫的 BizTalk 專案中的訊息。 這些訊息必須符合您在上一個步驟中建立的要求和回應結構描述。  
  
4. 建立協調流程叫用複合作業上的 SQL Server 資料庫。  
  
5. 建置和部署 BizTalk 專案。  
  
6. 設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
7. 啟動 BizTalk 應用程式。  
  
   本主題提供有關如何執行這些工作的指示。  
  
## <a name="sample-based-on-this-topic"></a>根據本主題的範例  
 ，CompositeOperations，根據本主題提供了範例[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱 < [SQL 配接器的範例](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md)。  
  
## <a name="generating-schema"></a>產生結構描述  
 本主題中，示範如何執行複合作業，下列工作將會執行指定的順序：  
  
- [員工] 資料表中插入記錄。  
  
- 藉由叫用 GET_LAST_EMP_DATA 預存程序中擷取最後一個插入的記錄的所有資料的行。  
  
- 從 [員工] 資料表中刪除記錄。  
  
  執行指令碼提供範例來建立員工資料表。 如需有關範例的詳細資訊，請參閱 <<c0> [ 結構描述範例](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md)。  
  
  您必須建立 BizTalk 專案，並使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]來產生這些作業的結構描述。 請參閱[擷取使用 SQL 配接器的 Visual Studio 中的 SQL Server 作業的中繼資料](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)如需有關如何產生結構描述。  
  
## <a name="creating-a-composite-schema-definition"></a>建立複合的結構描述定義  
 您現在必須建立複合的結構描述參考您針對個別作業所建立之結構描述。 執行下列步驟來建立複合的結構描述定義。  
  
#### <a name="to-add-a-composite-schema-definition"></a>若要新增複合結構描述定義  
  
1. 將結構描述檔案新增至 BizTalk 專案。 以滑鼠右鍵按一下專案名稱，指向**新增**，然後按一下**新項目**。 在 [**加入新項目**] 對話方塊中，從**分類**方塊中，按一下**結構描述檔案**。 從**範本**方塊中，按一下**結構描述**。 指定結構描述檔案的名稱，然後按一下**確定**。  
  
    此範例中，結構描述檔案名稱指定為`CompositeSchema.xsd`。  
  
2. 將參考加入至您想要執行之不同作業產生的結構描述。 在此範例中，不同的作業產生的結構描述是：  
  
   - TableOperation.dbo.Employee.xsd，Insert 和 Delete 作業。  
  
   - Procedure.dbo.xsd，如 GET_LAST_EMP_DATA 預存程序。  
  
     若要新增的參考：  
  
   1.  以滑鼠右鍵按一下根目錄**\<結構描述\>** 節點中 CompositeSchema.xsd，然後按一下**屬性**。  
  
   2.  在 **屬性**方塊中，按一下省略符號按鈕 **（...）** 對抗**匯入**屬性。  
  
        ![匯入結構描述定義](../../adapters-and-accelerators/adapter-oracle-database/media/d084d0f0-60b5-4ae8-9e80-7ed2c9e3ecca.gif "d084d0f0-60b5-4ae8-9e80-7ed2c9e3ecca")  
  
   3.  在 **匯入** 對話方塊中，從**匯入新結構描述為**清單中，選取**XSD 匯入**，然後按一下 **新增**。  
  
   4.  在  **BizTalk 型別選擇器**對話方塊方塊中，展開 BizTalk 專案名稱節點，展開**結構描述**，然後選取您要匯入的結構描述。 此範例中，選取 [< BizTalk_project_name >]。TableOperation_dbo_Employee。 按一下 [確定] 。  
  
        重複此步驟，匯入 < BizTalk_project_name >。Procedure_dbo 太。  
  
   5.  在 [**匯入**] 對話方塊中，按一下**確定**。  
  
3. 加入根結構描述節點中的兩個子節點。 一個子節點對應至要求結構描述，用於執行複合作業。 另一個子節點對應至回應結構描述。 對應至要求結構描述的節點可以有任意名稱。 對應至回應結構描述的節點必須呼叫 < request_schema_node > 回應。 針對此範例中，我們會呼叫要求結構描述節點**要求**。 因此，回應結構描述節點稱為**要求回應**。  
  
   > [!NOTE]
   >  根據預設，**根**節點也會加入至新的結構描述檔案。 您可以重新命名**根**節點，以**要求**。 若要重新命名節點，以滑鼠右鍵按一下節點名稱，然後按一下**重新命名**。  
  
    若要新增下的一個節點**\<結構描述\>** 節點：  
  
   1.  以滑鼠右鍵按一下**\<結構描述\>** 節點，指向**插入結構描述節點**，然後按一下**子記錄**。  
  
   2.  重新命名新節點**要求回應**。  
  
4. 新增子節點底下**要求**對應至複合作業的一部分，您將會執行每個作業的要求結構描述的節點。 此範例中，您必須新增對應於下列子節點：  
  
   -   插入和刪除員工資料表上的作業。  
  
   -   GET_LAST_EMP_DATA 預存程序。  
  
   > [!IMPORTANT]
   >  您必須將節點新增您要在其中執行作業的順序相同。 例如，如果您想要插入一筆記錄，執行預存程序，然後再刪除記錄，您必須先新增插入作業的節點，後面接著節點預存程序，和最後一個節點的刪除作業。  
  
    若要將子節點，即可**要求**節點：  
  
   1.  以滑鼠右鍵按一下**要求**節點，指向**插入結構描述節點**，然後按一下**子記錄**。  
  
        ![插入子節點的結構描述](../../adapters-and-accelerators/adapter-oracle-database/media/58992131-13a6-45c3-9513-5c0995091fae.gif "58992131-13a6-45c3-9513-5c0995091fae")  
  
   2.  重新命名的記錄以對應至您為複合作業的一部分執行的作業的要求結構描述。 例如，重新命名的節點"Insert"。  
  
   3.  地圖**插入**EMPLOYEE 資料表的 Insert 作業的要求結構描述的節點。 若要這樣做，請以滑鼠右鍵按一下**插入**節點，然後按一下**屬性**。 在 [**屬性**] 方塊中，從**資料結構型別**清單中，選取**Insert （參考）**。  
  
        ![將子節點對應至要求結構描述](../../adapters-and-accelerators/adapter-sql/media/5ace18be-0fe8-44c6-bd2f-cb19035494b5.gif "5ace18be-0fe8-44c6-bd2f-cb19035494b5")  
  
   4.  重複這些步驟來加入 GET_LAST_EMP_DATA 預存程序和刪除作業的要求結構描述的節點。 指定節點名稱，然後將它們對應到對應的結構描述，如下列表格中所述。  
  
       |節點名稱|對應至結構描述|  
       |---------------|----------------------|  
       |GET_LAST_EMP_DATA|GET_LAST_EMP_DATA （參考）|  
       |DELETE|刪除 （參考）|  
  
5. 新增子節點底下**要求回應**對應至複合作業的一部分，您將會執行每個作業的回應結構描述的節點。 此範例中，您必須新增對應於下列子節點：  
  
   -   插入和刪除員工資料表上的作業。  
  
   -   GET_LAST_EMP_DATA 預存程序。  
  
   > [!IMPORTANT]
   >  您必須新增子節點底下的子節點順序相同**要求**節點。  
  
    若要將子節點，即可**要求回應**節點：  
  
   1.  以滑鼠右鍵按一下**要求回應**節點，指向**插入結構描述節點**，然後按一下**子記錄**。  
  
   2.  重新命名的記錄以對應至您為複合作業的一部分執行的作業的回應結構描述。 例如，重新命名 「 InsertResponse"的節點。  
  
   3.  地圖**InsertResponse** EMPLOYEE 資料表的 Insert 作業的回應結構描述的節點。 若要這樣做，請以滑鼠右鍵按一下**InsertResponse**節點，然後按一下**屬性**。 在 [**屬性**] 方塊中，從**資料結構型別**清單中，選取**InsertResponse （參考）**。  
  
   4.  重複這些步驟來加入 GET_LAST_EMP_DATA 預存程序和刪除作業的回應結構描述的節點。 指定節點名稱，然後將它們對應到對應的結構描述，如下列表格中所述。  
  
       |節點名稱|對應至結構描述|  
       |---------------|----------------------|  
       |GET_LAST_EMP_DATAResponse|GET_LAST_EMP_DATAResponse （參考）|  
       |DeleteResponse|DeleteResponse （參考）|  
  
6. 儲存**CompositeSchema.xsd**檔案。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您在最後一個步驟中建立的複合結構描述會描述協調流程中的訊息所需的 「 類型 」。 訊息通常是一個變數，要為其類型會定義對應的結構。 現在，您必須建立協調流程的訊息，並將它們連結至您在上一個步驟中建立的結構描述。  
  
#### <a name="to-create-messages-and-link-to-schema"></a>若要建立訊息，並連結至結構描述  
  
1.  BizTalk 專案中新增協調流程。 從 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下**新項目**。 輸入 BizTalk 協調流程的名稱，然後按一下**新增**。  
  
2.  如果它尚未開啟，請開啟 BizTalk 專案，[協調流程檢視] 視窗。 若要這樣做，請按一下**檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。  
  
3.  在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。  
  
4.  以滑鼠右鍵按一下新建立的訊息，然後按**屬性 視窗**。  
  
5.  在 [**屬性**] 窗格**Message_1**，執行下列動作：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|輸入 `Request`|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*CompositeOp.CompositeSchema.Request*CompositeOp 所在的 BizTalk 專案的名稱。 CompositeSchema 是手動建立複合作業的結構描述。|  
  
6.  重複步驟 2 來建立新的訊息。 在 **屬性**窗格中的新訊息，執行下列動作：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|輸入 `Response`|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*CompositeOp.CompositeSchema.RequestResponse*。|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]執行 SQL Server 上的複合作業。 在此協調流程中，卸除在要求訊息定義的接收位置。 要求訊息必須符合您稍早建立的複合結構描述。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會取用這個訊息，並將它傳遞到 SQL Server。 從 SQL Server 的回應會儲存到另一個位置。 您必須包含傳送和接收圖形，將訊息傳送至 SQL Server，並接收回應，分別。 用於執行複合作業的基本協調流程如下所示：  
  
 ![用於執行複合操作的協調流程](../../adapters-and-accelerators/adapter-oracle-database/media/4a1ecae7-8bf2-4c8a-a413-34d6a402cbfb.gif "4a1ecae7-8bf2-4c8a-a413-34d6a402cbfb")  
  
### <a name="adding-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息 圖形中指定下列屬性。 剛剛提到的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveMessage|Receive|-設定**名稱**到*ReceiveMessage*<br />-設定**啟用**到 *，則為 True*|  
|SendMessage|Send|-設定**名稱**到*SendMessage*|  
|ReceiveResponse|Receive|-設定**名稱**到*ReceiveResponse*<br />-設定**啟用**到*False*|  
|SendResponse|Send|-設定**名稱**到*SendResponse*|  
  
### <a name="adding-ports"></a>新增連接埠  
 請確定您針對每個邏輯連接埠中指定下列屬性。 協調流程中所示，連接埠資料行中所列的名稱會是連接埠的名稱。  
  
|通訊埠|屬性|  
|----------|----------------|  
|MessageIn|-設定**識別碼**到*MessageIn*<br />-設定**型別**到*MessageInType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*接收*|  
|LOBPort|-設定**識別碼**到*LOBPort*<br />-設定**型別**到*LOBPortType*<br />-設定**通訊模式**到*要求-回應*<br />-設定**通訊方向**到*傳送接收*|  
|ResponseOut|-設定**識別碼**到*ResponseOut*<br />-設定**型別**到*ResponseOutType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*傳送*|  
  
### <a name="specify-messages-for-action-shapes-and-connect-them-to-ports"></a>為動作圖形指定訊息，並將其連接至連接埠  
 下表指定的屬性和屬性來指定動作圖形的訊息，以及連結至連接埠的訊息，您應該設定的值。 先前所述的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveMessage|-設定**訊息**到*要求*<br />-設定**作業**到*MessageIn.CompositeOp.Request*|  
|SendMessage|-設定**訊息**到*要求*<br />-設定**作業**到*LOBPort.CompositeOp.Request*|  
|ReceiveResponse|-設定**訊息**到*回應*<br />-設定**作業**到*LOBPort.CompositeOp.Response*|  
|SendResponse|-設定**訊息**到*回應*<br />-設定**作業**到*ResponseOut.CompositeOp.Request*|  
  
 您指定這些屬性之後，連線的訊息 圖形和連接埠和協調流程已完成。  
  
 您現在必須建置 BizTalk 方案，並將其部署至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 建置和執行協調流程](../../core/building-and-running-orchestrations.md)。
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在 [協調流程] 窗格底下[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 您必須使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定應用程式。 如需逐步解說，請參閱 <<c0> [ 逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。
  
 設定應用程式包含：  
  
- 選取應用程式主機。  
  
- 對應至實體連接埠在協調流程中建立的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 此協調流程中，您必須：  
  
  - 定義位置上的硬碟和對應的檔案連接埠，您將會卸除要求訊息。 BizTalk 協調流程將會取用的要求訊息，並將它傳送到 SQL Server 資料庫。  
  
  - 定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含從 SQL Server 資料庫回應的回應訊息。  
  
  - 定義實體 Wcf-custom 或 WCF SQL 傳送埠將訊息傳送至 SQL Server 資料庫。 因為作業是在單一交易中，執行複合作業的一部分，以確定**UseAmbientTransaction**繫結屬性設定為 **，則為 True**。  
  
     您也必須在傳送埠中指定的動作。 複合作業的動作是 「**CompositeOperation**"。 如需有關如何建立連接埠的資訊，請參閱 <<c0> [ 手動設定 SQL 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)。 如需如何指定連接埠動作的詳細資訊，請參閱[設定 SQL 配接器的 SOAP 動作](../../adapters-and-accelerators/adapter-sql/configure-the-soap-action-for-the-sql-adapter.md)。
  
    > [!NOTE]
    >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立繫結檔案，其中包含連接埠與那些連接埠設定動作的相關資訊。 您可以將從這個繫結檔案匯入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 （適用於輸出的呼叫） 的傳送埠或接收埠 （適用於輸入的呼叫）。 如需詳細資訊，請參閱 <<c0> [ 設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。 如果您匯入此繫結檔案，在 WCF 自訂] 或 [WCF-SQL 傳送連接埠上的動作會設定為與您在選取的所有作業都有關的動態動作[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生結構描述時。 複合作業中，您必須取代"CompositeOperation 」 的動態動作。  
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 BizTalk 應用程式來執行 SQL Server 資料庫上的複合作業。 如需有關啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。
  
 在這個階段，請確定：  
  
-   FILE 接收埠以接收要求訊息的協調流程正在執行。  
  
-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  
  
-   WCF 自訂] 或 [WCF-SQL 傳送埠將訊息傳送至 SQL Server 資料庫正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，您必須先卸除要求訊息至檔案接收位置。 要求訊息的結構描述必須符合您稍早建立的複合作業的結構描述。 例如，[員工] 資料表中插入記錄、 叫用 GET_LAST_EMP_DATA 預存程序中，並從 [員工] 資料表中刪除記錄的要求訊息是：  
  
```  
<Request xmlns="http://CompositeTest.CompositeSchema">  
  <Insert xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
    <Rows>  
      <Employee xmlns="http://schemas.microsoft.com/Sql/2008/05/Types/Tables/dbo">  
        <Name>John</Name>  
        <Designation>Manager</Designation>  
        <Salary>100000</Salary>  
      </Employee>  
    </Rows>  
  </Insert>  
  <GET_LAST_EMP_DATA xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/dbo" />  
  <Delete xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
    <Rows>  
      <Employee xmlns="http://schemas.microsoft.com/Sql/2008/05/Types/Tables/dbo">  
        <Name>John</Name>  
      </Employee>  
    </Rows>  
  </Delete>  
</Request>  
```  
  
 請參閱[複合作業的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md)如需有關執行 SQL Server 上的複合作業的要求訊息結構描述資料庫 使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
 協調流程取用訊息，並將它傳送到 SQL Server 資料庫。 從 SQL Server 資料庫的回應會儲存在其他定義的協調流程一部分的檔案位置。 例如，從先前的要求訊息的 SQL Server 資料庫的回應是：  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<RequestResponse xmlns="http://CompositeTest.CompositeSchema">  
  <InsertResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
    <InsertResult>  
      <long xmlns="http://schemas.microsoft.com/2003/10/Serialization/Arrays">10080</long>   
    </InsertResult>  
  </InsertResponse>  
  <GET_LAST_EMP_DATAResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/dbo">  
    <GET_LAST_EMP_DATAResult>  
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
              <Employee_ID>10080</Employee_ID>   
              <Name>John</Name>   
              <Designation>Manager</Designation>   
              <Salary>100000.00</Salary>   
              <Last_Modified>AAAAAAAAF40=</Last_Modified>   
            </NewTable>  
          </NewDataSet>  
        </diffgr:diffgram>  
      </DataSet>  
    </GET_LAST_EMP_DATAResult>  
    <ReturnValue>0</ReturnValue>   
  </GET_LAST_EMP_DATAResponse>  
  <DeleteResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
    <DeleteResult>1</DeleteResult>   
  </DeleteResponse>  
</RequestResponse>  
```  
  
 上述的回應包含多個結果集對應不同的作業執行複合作業的一部分。 比方說，`InsertResult`項目包含 10080，這是新加入的資料錄的唯一識別碼。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。 一旦您產生繫結檔案時，您可以匯入的組態設定檔案，，讓您不需要建立項目，例如傳送埠和接收相同的協調流程的連接埠。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用配接器繫結](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md)。
  
## <a name="see-also"></a>另請參閱  
[使用 SQL 配接器開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)