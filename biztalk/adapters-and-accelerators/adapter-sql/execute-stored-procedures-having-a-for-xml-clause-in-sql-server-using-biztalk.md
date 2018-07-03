---
title: 執行具有 FOR XML 子句中使用 BizTalk Server 的 SQL Server 中的預存程序 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d8fe927-90bf-48fc-a418-63b920b409ed
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3e407e981ed3f267bef61e27def1531bb794835b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998247"
---
# <a name="execute-stored-procedures-having-a-for-xml-clause-in-sql-server-using-biztalk-server"></a>執行具有 FOR XML 子句中使用 BizTalk Server 的 SQL Server 中的預存程序
在 SQL SELECT 陳述式可以有 FOR XML 子句，以 XML 傳回查詢結果，而不是資料列集。 您也可以具有 FOR XML 子句的 SELECT 陳述式的預存程序。 [FOR XML (SQL Server)](https://msdn.microsoft.com/library/ms178107.aspx)有詳細資訊。
  
 您可以使用以 WCF 為基礎[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]來執行這類預存程序。  
  
> [!IMPORTANT]
>  「 原生 」 的 SQL 配接器隨附[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]需要有一部分的 SELECT 陳述式的 FOR XML 子句的預存程序。 您可以使用這類預存程序，以 WCF 為基礎[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]而不需要對預存程序定義中的任何變更。  
> 
>  您可以隨時使用使用 'native' 提供與舊版的 SQL 配接器所產生的結構描述[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱 < [WCF-SQL 配接器使用 FOR XML 查詢](http://go.microsoft.com/fwlink/?LinkId=223428)(<http://go.microsoft.com/fwlink/?LinkId=223428>)。  
  
## <a name="how-to-invoke-stored-procedures-with-for-xml-clause"></a>如何叫用含有 FOR XML 子句的預存程序  
 當您叫用預存的程序，以在 SQL Server Management Studio，或使用 SQL 配接器隨附的 FOR XML 子句[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，輸出為 xml 訊息的格式。 若要使用這些程序以 WCF 為基礎[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，您必須有輸出訊息的結構描述。 以 WCF 為基礎[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]執行具有 FOR XML 子句的預存程序之後，從 SQL Server 接收回應訊息時需要此結構描述。 請注意，配接器本身所產生要叫用此預存程序的要求訊息。  
  
 除了有回應訊息的結構描述，您也必須執行某些工作，以使用以 WCF 為基礎的 FOR XML 子句中叫用預存程序[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
1. 產生具有 FOR XML 子句的預存程序的回應訊息的結構描述。 如果您已經有適用於 「 原生 」 SQL 配接器所產生的回應結構描述[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您可以略過此步驟。  
  
2. 建立 BizTalk 專案，並將產生的結構描述加入至專案。  
  
3. 搭配使用以 WCF 為基礎的 FOR XML 子句中產生結構描述的預存程序[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 這會提供配接器傳送到 SQL Server 叫用預存程序的要求訊息的結構描述。  
  
4. 建立 BizTalk 專案，來傳送和接收訊息，從 SQL Server 中的訊息。 配接器所產生的要求訊息的結構描述必須符合 「 要求 」 訊息。 回應訊息必須符合的結構描述使用 「 原生 」 的 SQL 配接器取得回應訊息，或藉由在 SQL Server Management Studio 中執行具有 FOR XML 子句的預存程序。  
  
5. 建立協調流程叫用 SQL Server 資料庫中的預存程序。  
  
6. 建置和部署 BizTalk 專案。  
  
7. 設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
8. 啟動 BizTalk 應用程式。  
  
##  <a name="BKMK_RespSchema"></a> 預存程序產生回應訊息的結構描述  
  
> [!NOTE]
>  您不需要執行此步驟中，如果您有適用於 SQL 配接器所產生的回應結構描述[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
 您可以在預存程序的 SELECT 陳述式提供產生預存程序的回應訊息的結構描述`xmlschema`子句搭配`for xml`子句。 本主題中，我們使用 GET_EMP_DETAILS_FOR_XML 預存程序，擷取特定的員工識別碼的員工詳細資料 若要執行預存程序，以擷取結構描述，SELECT 陳述式看起來如下所示：  
  
```  
SELECT [Employee_ID] ,[Name] ,[DOJ] ,[Designation] ,[Job_Description] ,[Photo] ,cast([Rating] as varchar(100)) as Rating ,[Salary] ,[Last_Modified] ,[Status] ,[Address]   
FROM [Adapt_Doc].[dbo].[Employee] for xml auto, xmlschema  
```  
  
 執行此預存的程序，以取得回應訊息的結構描述。 請注意，預存程序的回應包含結構描述，以及執行預存程序中的資料。 您必須從回應複製結構描述，並將它儲存到文字輸入板中。 此範例中，針對中，您可以命名為此結構描述**ResponseSchema.xsd**。 您現在必須建立 BizTalk 專案中的[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]並將此結構描述新增至專案。  
  
> [!IMPORTANT]
>  請確定您移除`xmlschema`子句之後執行預存程序，來產生結構描述。 如果您無法這樣做，請在最後執行預存程序，透過 BizTalk 時，您將回應訊息中，重新產生結構描述。 因此，若要取得回應訊息為 xml，您必須先移除`xmlschema`子句。  
  
#### <a name="to-add-the-schema-to-a-biztalk-project"></a>若要將結構描述加入 BizTalk 專案  
  
1. 建立 BizTalk 專案中的[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。  
  
2. 新增您的 BizTalk 專案的預存程序所產生的回應結構描述。 以滑鼠右鍵按一下 [方案總管] 中的 BizTalk 專案，指向**新增**，然後按一下**現有項目**。 在 [加入現有項目] 對話方塊中，瀏覽至您儲存的結構描述和按一下的位置**新增**。  
  
3. 開啟中的結構描述[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]並進行下列變更。  
  
   1.  將節點加入至結構描述，並移動現有的根節點，此新加入的節點之下。 為根節點名稱。 本主題中，重新命名的根節點**根**。  
  
   2.  產生預存程序的回應結構描述參考 sqltypes.xsd。 您可以取得的 sqltypes.xsd 結構描述[ http://go.microsoft.com/fwlink/?LinkId=131087 ](http://go.microsoft.com/fwlink/?LinkId=131087)。 Sqltypes.xsd 結構描述加入 BizTalk 專案中。  
  
   3.  在預存程序所產生的結構描述，將值變更`import schemaLocation`如下。  
  
       ```  
       import schemaLocation=”sqltypes.xsd”  
       ```  
  
        因為您已經將 sqltypes.xsd 結構描述加入 BizTalk 專案，您可以這麼做。  
  
   4.  提供結構描述目標命名空間。 按一下  **\<結構描述\>** 節點，並在 屬性 窗格中，指定的命名空間中**目標命名空間**屬性。 本主題中提供的命名空間`http://ForXmlStoredProcs/namespace`。  
  
## <a name="generating-schema-for-the-request-message-to-invoke-the-stored-procedure"></a>產生要叫用預存程序的要求訊息的結構描述  
 若要產生您可以使用要求訊息的結構描述[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]中的 BizTalk 專案從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。 本主題中，產生 GET_EMP_DETAILS_FOR_XML 預存程序的結構描述。 如需有關如何產生結構描述使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，請參閱 <<c2> [ 擷取使用 SQL 配接器的 Visual Studio 中的 SQL Server 作業的中繼資料](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)。  
  
> [!IMPORTANT]
>  您必須選取只會從程序來產生結構描述**程序**中的節點[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您稍早產生的結構描述會描述協調流程中的訊息所需的 「 類型 」。 訊息通常是一個變數，要為其類型會定義對應的結構。 現在，您必須建立協調流程的訊息，並將它們連結至您在上一個步驟中產生的結構描述。  
  
#### <a name="to-create-messages-and-link-to-schema"></a>若要建立訊息，並連結至結構描述  
  
1.  BizTalk 專案中新增協調流程。 從 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下**新項目**。 輸入 BizTalk 協調流程的名稱，然後按一下**新增**。  
  
2.  如果它尚未開啟，請開啟 BizTalk 專案，[協調流程檢視] 視窗。 若要這樣做，請按一下**檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。  
  
3.  在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。  
  
4.  以滑鼠右鍵按一下新建立的訊息，然後按**屬性 視窗**。  
  
5.  在 [**屬性**] 窗格**Message_1**，執行下列動作：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|輸入 `Request`|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取  *ForXMLProcedure.Procedure_dbo。GET_EMP_DETAILS_FOR_XML*ForXMLProcedure 所在的 BizTalk 專案的名稱。 Procedure_dbo 是叫用 GET_EMP_DETAILS_FOR_XML 程序所產生的結構描述。|  
  
6.  重複步驟 2 來建立新的訊息。 在 **屬性**窗格中的新訊息，執行下列動作：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|輸入 `Response`|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*ForXMLProcedure.ResponseSchema*ResponseSchema 所在的執行與預存程序所產生的回應結構描述名稱下所述[產生預存程序的回應訊息的結構描述](#BKMK_RespSchema)。|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]執行 SQL Server 中的預存程序。 在此協調流程中，卸除在要求訊息定義的接收位置。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會取用這個訊息，並將它傳遞到 SQL Server。 從 SQL Server 的回應會儲存到另一個位置。 您必須包含傳送和接收圖形，將訊息傳送至 SQL Server，並接收回應，分別。 範例協調流程叫用程序如下所示：  
  
 ![叫用預存程序協調流程](../../adapters-and-accelerators/adapter-sql/media/eac6e8b6-f0f4-44af-8218-03ca3864b267.gif "eac6e8b6-f0f4-44af-8218-03ca3864b267")  
  
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
|ReceiveMessage|-設定**訊息**到*要求*<br />-設定**作業**到*MessageIn.FOR_XML。要求*|  
|SendMessage|-設定**訊息**到*要求*<br />-設定**作業**到*LOBPort.FOR_XML。要求*|  
|ReceiveResponse|-設定**訊息**到*回應*<br />-設定**作業**到*LOBPort.FOR_XML。回應*|  
|SendResponse|-設定**訊息**到*回應*<br />-設定**作業**到*ResponseOut.FOR_XML。要求*|  
  
 您指定這些屬性之後，連線的訊息 圖形和連接埠和協調流程已完成。  
  
 您現在必須建置 BizTalk 方案，並將其部署至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 建置和執行協調流程](../../core/building-and-running-orchestrations.md)。
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在 [協調流程] 窗格底下[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 您必須使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定應用程式。 如需逐步解說，請參閱 <<c0> [ 逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。
  
 設定應用程式包含：  
  
- 選取應用程式主機。  
  
- 對應至實體連接埠在協調流程中建立的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 此協調流程中，您必須：  
  
  - 定義位置上的硬碟和對應的檔案連接埠，您將會卸除要求訊息。 BizTalk 協調流程將會取用的要求訊息，並將它傳送到 SQL Server 資料庫。  
  
  - 定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含從 SQL Server 資料庫回應的回應訊息。  
  
  - 定義實體 Wcf-custom 或 WCF SQL 傳送埠將訊息傳送至 SQL Server 資料庫。 如需有關如何建立傳送埠的指示，請參閱 <<c0> [ 手動設定 SQL 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)。
  
     您也必須在傳送埠中指定的動作。 包含 FOR XML 子句的程序，您必須以下列格式設定的動作。  
  
    ```  
    XmlProcedure/<schema_name>/<procedure_name>  
    ```  
  
     因此，本主題中，我們會在其中執行 GET_EMP_DETAILS_FOR_XML 程序，此動作會：  
  
    ```  
    XmlProcedure/dbo/GET_EMP_DETAILS_FOR_XML  
    ```  
  
     如需有關設定動作的詳細資訊，請參閱 <<c0> [ 設定 SQL 配接器的 SOAP 動作](../../adapters-and-accelerators/adapter-sql/configure-the-soap-action-for-the-sql-adapter.md)。
  
     執行具有 FOR XML 子句的預存程序時，您也必須設定下列繫結屬性。  
  
    |繫結屬性名稱|將此設為|  
    |---------------------------|-----------------|  
    |XmlStoredProcedureRootNodeName|指定的根節點底下所述，您新增至您為預存程序中，產生的回應結構描述名稱[產生預存程序的回應訊息的結構描述](#BKMK_RespSchema)。 本主題中，將此設為**根**。|  
    |XmlStoredProcedureRootNodeNamespace|指定您為預存程序中，產生的回應結構描述的目標命名空間，如底下所述[產生預存程序的回應訊息的結構描述](#BKMK_RespSchema)。 本主題中，將此設為`http://ForXmlStoredProcs/namespace`。|  
  
     如需指定繫結屬性的值的詳細資訊，請參閱[設定 SQL 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md)。  
  
    > [!NOTE]
    >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立繫結檔案，其中包含連接埠與那些連接埠設定動作的相關資訊。 您可以將從這個繫結檔案匯入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 （適用於輸出的呼叫） 的傳送埠或接收埠 （適用於輸入的呼叫）。 如需詳細資訊，請參閱 <<c0> [ 設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。
  
## <a name="starting-the-application"></a>啟動應用程式  
 SQL Server 資料庫中，您必須啟動叫用程序的 BizTalk 應用程式。 如需有關啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。
  
 在這個階段，請確定：  
  
-   FILE 接收埠以接收要求訊息的協調流程正在執行。  
  
-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  
  
-   WCF 自訂] 或 [WCF-SQL 傳送埠將訊息傳送至 SQL Server 資料庫正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，您必須先卸除要求訊息至檔案接收位置。 使用產生的程序的要求結構描述必須符合 「 要求 」 訊息的結構描述[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 例如，要叫用 GET_EMP_DETAILS_FOR XML 的要求訊息是：  
  
```  
<GET_EMP_DETAILS_FOR_XML xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/dbo">  
  <emp_id>10765</emp_id>  
</GET_EMP_DETAILS_FOR_XML>  
```  
  
 請參閱[程序和函式的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-procedures-and-functions.md)如需叫用 SQL Server 中的程序的要求訊息結構描述資料庫 使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
 協調流程取用訊息，並將它傳送到 SQL Server 資料庫。 SQL Server 資料庫的回應會儲存在其他定義的協調流程一部分的檔案位置。 例如，上述的要求訊息的 SQL Server 資料庫的回應是：  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<Root xmlns="http://ForXmlStoredProcs/namespace">  
  <Adapt_Doc.dbo.Employee Employee_ID="10765" Name="John" Designation="asdfaf" Salary="3434.00" Last_Modified="AAAAAAAANso=" Status="0" xmlns="" />  
</Root>  
```  
  
 請注意，執行預存程序所產生時，在相同的結構描述中接收回應。 也請注意，根節點和命名空間是您指定的值為相同**XmlStoredProcedureRootNodeName**並**XmlStoredProcedureRootNodeNamespace**分別繫結屬性。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。 一旦您產生繫結檔案時，您可以匯入的組態設定檔案，，讓您不需要建立項目，例如傳送埠和接收相同的協調流程的連接埠。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用配接器繫結](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md)。  
  
## <a name="see-also"></a>另請參閱  
[使用 SQL 配接器開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)