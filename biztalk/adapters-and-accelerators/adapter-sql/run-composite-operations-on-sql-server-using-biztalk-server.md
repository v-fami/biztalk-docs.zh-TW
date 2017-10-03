---
title: "執行複合操作 SQL Server 上使用 BizTalk Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86fd2aa1-20c7-4b58-9f35-83ba0c959cf1
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa84ee4a4c1964db090cc48b7229558c9ee86114
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="run-composite-operations-on-sql-server-using-biztalk-server"></a>執行複合操作 SQL Server 上使用 BizTalk Server
[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可讓配接器用戶端執行複合操作上的 SQL Server 資料庫。 複合作業可包括：  
  
-   插入、 更新和刪除作業。 選取的作業不支援複合作業。  
  
-   當做作業執行的預存程序。  
  
 單一複合作業可以有任意數目的這些作業，以任何順序。 例如，您可以有後面是刪除作業，以及最後的預存程序執行兩項插入作業。 此外，您可以有不同的資料庫資料表或檢視表為目標的不同作業。 如需配接器如何支援複合操作的詳細資訊，請參閱[使用 SQL 配接器的 SQL Server 中執行複合操作](../../adapters-and-accelerators/adapter-sql/run-composite-operations-in-sql-server-using-the-sql-adapter.md)。 複合操作的 SOAP 訊息結構的相關資訊，請參閱[複合操作的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md)。  
  
> [!NOTE]
>  如果您正在執行具有使用者定義類型的資料行的資料表上的作業，請確定您參考[資料表和檢視表使用 SQL 配接器的使用者定義類型的作業](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md)開始開發應用程式之前。  
  
## <a name="how-to-perform-composite-operations-on-sql-server"></a>如何執行 SQL Server 上的複合作業  
 使用 SQL Server 上執行操作[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[開發 BizTalk 應用程式與 SQL 配接器的建置組塊](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)。 若要執行複合操作上的 SQL Server 資料庫，這些工作包括：  
  
1.  建立 BizTalk 專案，並產生您想要叫用的所有作業的結構描述。  
  
2.  手動建立結構描述檔案，其中包含您在上一個步驟中產生的所有結構描述的參考。  
  
3.  建立傳送和接收訊息，從 SQL Server 資料庫的 BizTalk 專案中的訊息。 這些訊息必須符合您在上一個步驟中建立的要求和回應結構描述。  
  
4.  建立協調流程叫用 SQL Server 資料庫的複合作業。  
  
5.  建置和部署 BizTalk 專案。  
  
6.  設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
7.  啟動 BizTalk 應用程式。  
  
 本主題提供有關如何執行這些工作的指示。  
  
## <a name="sample-based-on-this-topic"></a>根據本主題的範例  
 基礎的範例，CompositeOperations，本主題隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱[SQL 配接器範例](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md)。  
  
## <a name="generating-schema"></a>產生結構描述  
 本主題中，以示範如何執行複合操作，下列工作將會執行指定的順序：  
  
-   EMPLOYEE 資料表中插入記錄。  
  
-   叫用 GET_LAST_EMP_DATA 預存程序所擷取最後一個插入的記錄的所有資料的行。  
  
-   從 EMPLOYEE 資料表刪除記錄。  
  
 執行與建立員工資料表範例中提供的指令碼。 如需這些範例的詳細資訊，請參閱[結構描述範例](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md)。  
  
 您必須建立 BizTalk 專案，並使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]來產生這些作業的結構描述。 請參閱[擷取中繼資料，使用 SQL 配接器的 Visual Studio 中的 SQL Server 作業的](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)如需有關如何產生結構描述。  
  
## <a name="creating-a-composite-schema-definition"></a>建立複合的結構描述定義  
 您現在必須建立複合的結構描述參考您針對個別作業所建立之結構描述。 執行下列步驟，以建立複合的結構描述定義。  
  
#### <a name="to-add-a-composite-schema-definition"></a>若要加入複合的結構描述定義  
  
1.  將結構描述檔案加入至 BizTalk 專案。 以滑鼠右鍵按一下專案名稱，指向**新增**，然後按一下 **新項目**。 在**加入新項目**對話方塊中，從**類別**方塊中，按一下**結構描述檔案**。 從**範本**方塊中，按一下**結構描述**。 指定結構描述檔案的名稱，然後按一下**確定**。  
  
     此範例中，結構描述檔案名稱指定為`CompositeSchema.xsd`。  
  
2.  將參考加入至您想要執行的不同作業產生的結構描述。 在此範例中，不同的結構描述產生的作業如下：  
  
    -   TableOperation.dbo.Employee.xsd Insert 和 Delete 作業。  
  
    -   Procedure.dbo.xsd，如 GET_LAST_EMP_DATA 預存程序。  
  
     若要加入的參考：  
  
    1.  以滑鼠右鍵按一下根**\<結構描述 >**中 CompositeSchema.xsd，按一下節點**屬性**。  
  
    2.  在**屬性**方塊中，按一下省略符號按鈕**（...）**針對**匯入**屬性。  
  
         ![匯入結構描述定義](../../adapters-and-accelerators/adapter-oracle-database/media/d084d0f0-60b5-4ae8-9e80-7ed2c9e3ecca.gif "d084d0f0-60b5-4ae8-9e80-7ed2c9e3ecca")  
  
    3.  在**匯入**對話方塊中，從**匯入新結構描述為**清單中，選取**XSD 匯入**，然後按一下 **新增**。  
  
    4.  在**BizTalk 型別選擇器**對話方塊方塊中，展開 BizTalk 專案名稱節點，展開**結構描述**，然後選取您要匯入的結構描述。 此範例中，選取 < BizTalk_project_name >。TableOperation_dbo_Employee。 按一下 **[確定]**。  
  
         重複此步驟，匯入 < BizTalk_project_name >。Procedure_dbo 太。  
  
    5.  在**匯入**對話方塊中，按一下 **確定**。  
  
3.  將兩個子節點加入至根結構描述節點。 一個子節點對應至要求結構描述執行複合作業。 另一個子節點對應至回應結構描述。 對應至要求結構描述的節點可以有任何名稱。 對應至回應結構描述的節點必須呼叫 < request_schema_node > 回應。 針對此範例中，我們會呼叫要求結構描述節點，做為**要求**。 因此，呼叫的回應結構描述節點**RequestResponse**。  
  
    > [!NOTE]
    >  根據預設，**根**節點也會加入至新的結構描述檔案。 您可以重新命名**根**節點**要求**。 若要重新命名的節點，以滑鼠右鍵按一下節點名稱，然後按一下**重新命名**。  
  
     若要加入的節點下**\<結構描述 >**節點：  
  
    1.  以滑鼠右鍵按一下**\<結構描述 >**節點，指向**插入結構描述節點**，然後按一下**子記錄**。  
  
    2.  重新命名新的節點**RequestResponse**。  
  
4.  加入子節點底下**要求**對應到複合作業的一部分，您將執行每個作業的要求結構描述的節點。 對於此範例中，您必須將對應於下列子節點：  
  
    -   插入和刪除員工資料表上的作業。  
  
    -   GET_LAST_EMP_DATA 預存程序。  
  
    > [!IMPORTANT]
    >  您必須將節點加入您要執行作業的順序相同。 例如，如果您想要插入的記錄，然後執行預存程序，然後刪除記錄，您必須先新增的節點代表插入作業，後面接著預存程序中，節點和最後一個刪除作業。  
  
     若要加入至子節點**要求**節點：  
  
    1.  以滑鼠右鍵按一下**要求**節點，指向**插入結構描述節點**，然後按一下 **子記錄**。  
  
         ![插入結構描述的子節點](../../adapters-and-accelerators/adapter-oracle-database/media/58992131-13a6-45c3-9513-5c0995091fae.gif "58992131-13a6-45c3-9513-5c0995091fae")  
  
    2.  重新命名為對應至複合作業的一部分執行的操作的要求結構描述的記錄。 例如，重新命名 「 插入 」 至節點。  
  
    3.  地圖**插入**EMPLOYEE 資料表的 Insert 作業的要求結構描述的節點。 若要這樣做，請以滑鼠右鍵按一下**插入**節點，然後按一下**屬性**。 在**屬性** 方塊中，從**資料結構型別**清單中，選取**插入 （參考）**。  
  
         ![將子節點對應至要求結構描述](../../adapters-and-accelerators/adapter-sql/media/5ace18be-0fe8-44c6-bd2f-cb19035494b5.gif "5ace18be-0fe8-44c6-bd2f-cb19035494b5")  
  
    4.  重複這些步驟來加入 GET_LAST_EMP_DATA 預存程序和刪除作業的要求結構描述的節點。 指定節點名稱，然後將它們對應至對應的結構描述，如下列表格中所述。  
  
        |節點名稱|對應至結構描述|  
        |---------------|----------------------|  
        |GET_LAST_EMP_DATA|GET_LAST_EMP_DATA （參考）|  
        |DELETE|刪除 （參考）|  
  
5.  加入子節點底下**RequestResponse**對應到複合作業的一部分，您將執行每個作業的回應結構描述的節點。 對於此範例中，您必須將對應於下列子節點：  
  
    -   插入和刪除員工資料表上的作業。  
  
    -   GET_LAST_EMP_DATA 預存程序。  
  
    > [!IMPORTANT]
    >  您必須加入子節點下的子節點的順序相同**要求**節點。  
  
     若要加入至子節點**RequestResponse**節點：  
  
    1.  以滑鼠右鍵按一下**RequestResponse**節點，指向**插入結構描述節點**，然後按一下**子記錄**。  
  
    2.  重新命名為對應至複合作業的一部分執行的操作的回應結構描述的記錄。 例如，重新命名 「 InsertResponse"的節點。  
  
    3.  地圖**InsertResponse** EMPLOYEE 資料表的 Insert 作業的回應結構描述的節點。 若要這樣做，請以滑鼠右鍵按一下**InsertResponse**節點，然後按一下**屬性**。 在**屬性** 方塊中，從**資料結構型別**清單中，選取**InsertResponse （參考）**。  
  
    4.  重複這些步驟來加入 GET_LAST_EMP_DATA 預存程序和刪除作業的回應結構描述的節點。 指定節點名稱，然後將它們對應至對應的結構描述，如下列表格中所述。  
  
        |節點名稱|對應至結構描述|  
        |---------------|----------------------|  
        |GET_LAST_EMP_DATAResponse|GET_LAST_EMP_DATAResponse （參考）|  
        |DeleteResponse|DeleteResponse （參考）|  
  
6.  儲存**CompositeSchema.xsd**檔案。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您在最後一個步驟中建立複合結構描述會描述 「 類型 」 所需的協調流程中的訊息。 訊息通常是為其型別由對應的結構描述所定義的變數。 您現在必須建立協調流程的訊息，並將它們連結至您在上一個步驟中建立的結構描述。  
  
#### <a name="to-create-messages-and-link-to-schema"></a>建立訊息，以及連結至結構描述  
  
1.  BizTalk 專案中新增協調流程。 從 方案總管 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下 **新項目**。 輸入 BizTalk 協調流程的名稱，然後按一下**新增**。  
  
2.  如果它尚未開啟，請開啟 BizTalk 專案中，[協調流程檢視] 視窗。 若要這樣做，請按一下**檢視**，指向 **其他視窗**，然後按一下 **協調流程檢視**。  
  
3.  在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。  
  
4.  以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。  
  
5.  在**屬性**窗格**Message_1**，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|輸入 `Request`|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*CompositeOp.CompositeSchema.Request*CompositeOp 所在的 BizTalk 專案的名稱。 CompositeSchema 是手動建立的複合作業的結構描述。|  
  
6.  重複步驟 2 來建立新的訊息。 在**屬性**窗格新訊息中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|輸入 `Response`|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*CompositeOp.CompositeSchema.RequestResponse*。|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]執行 SQL Server 上的複合作業。 在此協調流程中，卸除要求訊息已定義的接收位置。 要求訊息必須符合您稍早建立的複合結構描述。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會取用這個訊息，並將它傳遞到 SQL Server。 從 SQL Server 的回應會儲存到另一個位置。 您必須包含傳送和接收送到 SQL Server 的訊息並接收回應，分別圖形。 用於執行複合操作的基本協調流程如下所示：  
  
 ![用於執行複合操作的協調流程](../../adapters-and-accelerators/adapter-oracle-database/media/4a1ecae7-8bf2-4c8a-a413-34d6a402cbfb.gif "4a1ecae7-8bf2-4c8a-a413-34d6a402cbfb")  
  
### <a name="adding-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息圖形指定下列屬性。 圖形資料行中所列的名稱是訊息 圖形的名稱，為顯示在剛才提及的協調流程中。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveMessage|Receive|-設定**名稱**至*ReceiveMessage*<br />-設定**啟動**至*，則為 True*|  
|SendMessage|Send|-設定**名稱**至*SendMessage*|  
|ReceiveResponse|Receive|-設定**名稱**至*ReceiveResponse*<br />-設定**啟動**至*False*|  
|SendResponse|Send|-設定**名稱**至*SendResponse*|  
  
### <a name="adding-ports"></a>新增連接埠  
 請確定您針對每個邏輯連接埠指定下列屬性。 連接埠資料行中所列的名稱是連接埠的名稱，為顯示協調流程中。  
  
|通訊埠|屬性|  
|----------|----------------|  
|MessageIn|-設定**識別碼**至*MessageIn*<br />-設定**類型**至*MessageInType*<br />-設定**通訊模式**至*單向*<br />-設定**通訊方向**至*接收*|  
|LOBPort|-設定**識別碼**至*LOBPort*<br />-設定**類型**至*LOBPortType*<br />-設定**通訊模式**至*要求-回應*<br />-設定**通訊方向**至*傳送接收*|  
|ResponseOut|-設定**識別碼**至*ResponseOut*<br />-設定**類型**至*ResponseOutType*<br />-設定**通訊模式**至*單向*<br />-設定**通訊方向**至*傳送*|  
  
### <a name="specify-messages-for-action-shapes-and-connect-them-to-ports"></a>指定訊息的動作圖形，並將它們連接至連接埠  
 下表指定屬性和其值，您應該設定來指定動作圖形的訊息，以及連結至連接埠的訊息。 圖形資料行中所列的名稱是 「 訊息 」 圖形的名稱，為顯示在協調流程中先前所述。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveMessage|-設定**訊息**至*要求*<br />-設定**作業**至*MessageIn.CompositeOp.Request*|  
|SendMessage|-設定**訊息**至*要求*<br />-設定**作業**至*LOBPort.CompositeOp.Request*|  
|ReceiveResponse|-設定**訊息**至*回應*<br />-設定**作業**至*LOBPort.CompositeOp.Response*|  
|SendResponse|-設定**訊息**至*回應*<br />-設定**作業**至*ResponseOut.CompositeOp.Request*|  
  
 您指定這些屬性之後，連接的訊息 圖形和連接埠，而且您的協調流程已完成。  
  
 您現在必須建置 BizTalk 方案，並部署到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱[建置和執行協調流程](../../core/building-and-running-orchestrations.md)。
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 在 [協調流程] 窗格中您已部署的 BizTalk 專案後，會列出您稍早建立的協調流程[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 您必須使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定應用程式。 如需逐步解說，請參閱[逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。
  
 設定應用程式包括：  
  
-   選取應用程式的主機。  
  
-   對應至實體連接埠在協調流程中建立的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 此協調流程中，您必須：  
  
    -   定義位置上的硬碟和對應的檔案連接埠，您將在此置放要求訊息。 BizTalk 協調流程會使用要求訊息，並將它傳送給 SQL Server 資料庫。  
  
    -   定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含從 SQL Server 資料庫回應的回應訊息。  
  
    -   定義實體 Wcf-custom 或 WCF SQL 傳送埠將訊息傳送至 SQL Server 資料庫。 因為作業都是因為在單一交易中，執行屬於複合作業確定**UseAmbientTransaction**繫結屬性設定為**True**。  
  
         您也必須在傳送埠中指定的動作。 複合操作的動作是 「**CompositeOperation**"。 如需如何建立連接埠相關資訊，請參閱[手動設定 SQL 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)。 如需如何指定連接埠動作的詳細資訊，請參閱[設定 SQL 配接器的 SOAP 動作](../../adapters-and-accelerators/adapter-sql/configure-the-soap-action-for-the-sql-adapter.md)。
  
        > [!NOTE]
        >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠的設定動作的相關資訊的繫結檔案。 您可以從這個繫結檔案匯[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 （適用於傳出呼叫） 的傳送埠或接收埠 （用於進行傳入呼叫時）。 如需詳細資訊，請參閱[設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。 如果您匯入此繫結檔案，Wcf-custom 或 WCF SQL 傳送埠上的動作會設定為與您在選取的所有作業都有關的動態動作[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]時產生結構描述。 複合作業中，您必須取代的動態 「 CompositeOperation 」 動作。  
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 BizTalk 應用程式執行的 SQL Server 資料庫上的複合作業。 如需啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。
  
 在這個階段，請確定：  
  
-   FILE 接收埠以接收要求訊息的協調流程執行。  
  
-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  
  
-   Wcf-custom 或 WCF SQL 傳送埠將訊息傳送至 SQL Server 資料庫正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，您必須先卸除要求訊息到檔案接收位置。 要求訊息的結構描述必須符合您稍早建立的複合作業的結構描述。 例如，員工資料表中插入記錄、 叫用的 GET_LAST_EMP_DATA 預存程序，並從 EMPLOYEE 資料表中刪除記錄的要求訊息是：  
  
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
  
 請參閱[複合操作的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md)如需有關執行 SQL Server 上的複合作業的要求訊息結構描述資料庫使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
 協調流程取用訊息，並將它傳送到 SQL Server 資料庫。 從 SQL Server 資料庫的回應會儲存在其他的協調流程中定義的檔案位置。 比方說，是從先前的要求訊息的 SQL Server 資料庫的回應：  
  
```  
\<?xml version="1.0" encoding="utf-8" ?>   
<RequestResponse xmlns="http://CompositeTest.CompositeSchema">  
  <InsertResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
    <InsertResult>  
      <long xmlns="http://schemas.microsoft.com/2003/10/Serialization/Arrays">10080</long>   
    </InsertResult>  
  </InsertResponse>  
  <GET_LAST_EMP_DATAResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/dbo">  
    <GET_LAST_EMP_DATAResult>  
      <DataSet xmlns="http://schemas.datacontract.org/2004/07/System.Data">  
        \<xs:schema id="NewDataSet" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
          \<xs:element msdata:IsDataSet="true" name="NewDataSet">  
            \<xs:complexType>  
              \<xs:sequence>  
                \<xs:element minOccurs="0" maxOccurs="unbounded" name="NewTable">  
                  \<xs:complexType>  
                    \<xs:sequence>  
                      \<xs:element minOccurs="0" name="Employee_ID" type="xs:int" />   
                      \<xs:element minOccurs="0" name="Name" type="xs:string" />   
                      \<xs:element minOccurs="0" name="DOJ" type="xs:dateTime" />   
                      \<xs:element minOccurs="0" name="Designation" type="xs:string" />   
                      \<xs:element minOccurs="0" name="Job_Description" type="xs:string" />   
                      \<xs:element minOccurs="0" name="Photo" type="xs:base64Binary" />   
                      \<xs:element minOccurs="0" name="Rating" type="xs:string" />   
                      \<xs:element minOccurs="0" name="Salary" type="xs:decimal" />   
                      \<xs:element minOccurs="0" name="Last_Modified" type="xs:base64Binary" />   
                    \</xs:sequence>  
                  \</xs:complexType>  
                \</xs:element>  
              \</xs:sequence>  
            \</xs:complexType>  
          \</xs:element>  
        \</xs:schema>  
        \<diffgr:diffgram xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
          <NewDataSet xmlns="">  
            <NewTable>  
              <Employee_ID>10080</Employee_ID>   
              <Name>John</Name>   
              <Designation>Manager</Designation>   
              <Salary>100000.00</Salary>   
              <Last_Modified>AAAAAAAAF40=</Last_Modified>   
            </NewTable>  
          </NewDataSet>  
        \</diffgr:diffgram>  
      </DataSet>  
    </GET_LAST_EMP_DATAResult>  
    <ReturnValue>0</ReturnValue>   
  </GET_LAST_EMP_DATAResponse>  
  <DeleteResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
    <DeleteResult>1</DeleteResult>   
  </DeleteResponse>  
</RequestResponse>  
```  
  
 上述的回應會包含多個結果集對應複合作業的一部分執行的不同作業。 例如，`InsertResult`元素包含 10080，這是新加入的記錄的唯一識別碼。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。 一旦產生繫結檔案時，可以組態設定匯入檔案，使您不需要建立項目，例如傳送埠和接收相同的協調流程連接埠。 如需繫結檔案的詳細資訊，請參閱[重複使用配接器繫結](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md)。
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)