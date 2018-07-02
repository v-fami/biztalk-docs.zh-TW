---
title: 插入、 更新、 刪除或選取 使用 SQL 配接器的 BizTalk Server 的作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d411b1a-a36d-4e3e-a56a-91804a5d69b9
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f3e81cf843473a544b915d185e4609d0748fc2e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982023"
---
# <a name="insert-update-delete-or-select-operations-using-biztalk-server-with-the-sql-adapter"></a>插入、 更新、 刪除或選取 使用 SQL 配接器的 BizTalk Server 作業
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]呈現一組 SQL Server 資料庫資料表和檢視表的標準作業。 這些稱為資料操作語言 (DML) 作業。 藉由使用 DML 作業，您可以執行簡單的 Insert、 Update、 Select、 和刪除資料表和檢視表上的作業。 如需配接器如何支援這些作業的詳細資訊，請參閱[Insert、 Update、 Delete 與資料表和 SQL 配接器的檢視表的選取作業](../../adapters-and-accelerators/adapter-sql/insert-update-delete-and-select-on-tables-and-views-with-the-sql-adapter.md)。 這些作業的 SOAP 訊息結構的相關資訊，請參閱[Insert、 Update、 Delete 與資料表和檢視表的選取作業的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md)。  
  
> [!NOTE]
>  如果您正在執行具有使用者定義類型的資料行的資料表上的作業，請確定您參考[資料表和檢視與使用 SQL 配接器的使用者定義型別上的作業](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md)開始開發您的應用程式之前。  
  
## <a name="how-to-perform-basic-operations-on-a-sql-server-database"></a>如何對 SQL Server 資料庫執行基本作業  
 使用執行 SQL Server 資料庫上的作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及中所述的程序性工作[開發使用 SQL 配接器的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)。 若要在 SQL Server 中執行 Insert、 Update、 Delete 或資料表和檢視表的 Select 作業，這些工作如下：  
  
1. 建立 BizTalk 專案，並產生您想要在 SQL Server 資料庫資料表或檢視表上叫用作業的結構描述。  
  
2. 建立傳送和接收訊息，從 SQL Server 資料庫的 BizTalk 專案中的訊息。  
  
3. 建立協調流程叫用 SQL Server 資料庫資料表或檢視的作業。  
  
4. 建置和部署 BizTalk 專案。  
  
5. 設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
6. 啟動 BizTalk 應用程式。  
  
   本主題提供執行這些工作的指示。  
  
## <a name="sample-based-on-this-topic"></a>根據本主題的範例  
 ，SelectTable，根據本主題提供了範例[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱 < [SQL 配接器的範例](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md)。  
  
## <a name="generating-schema"></a>產生結構描述  
 本主題示範如何執行基本的 DML 作業，從 SQL Server 資料庫中的 EMPLOYEE 資料表中選取記錄。 執行指令碼提供範例來建立員工資料表。 如需有關範例的詳細資訊，請參閱 <<c0> [ 結構描述範例](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md)。  
  
 為了示範如何選取資料錄，EMPLOYEE 資料表的選取作業產生結構描述。 您必須建立 BizTalk 專案，並使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生結構描述。 請參閱[擷取使用 SQL 配接器的 Visual Studio 中的 SQL Server 作業的中繼資料](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)如需有關如何產生結構描述。  
  
> [!IMPORTANT]
>  如果您要產生作業的使用者定義型別 (Udt) 資料行的資料表上的中繼資料，請確定個別的組件的 Udt 上有相同的位置[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]可執行檔的 devenv.exe。 可執行檔通常會在`<installation drive>:\Program Files\Microsoft Visual Studio <version>\Common7\IDE`。 在此範例中，[員工] 資料表會有一個 UDT （點） 資料行。 請確認您已複製的相同位置中的個別組件[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]可執行檔。  
> 
>  如需有關如何建立 UDT 的資訊，請參閱 <<c0> [ 建立使用者定義型別](https://msdn.microsoft.com/library/ms131106.aspx)。 如需如何註冊 SQL Server 中的 UDT 的資訊，請參閱[Registering User-Defined SQL Server 中的型別](https://msdn.microsoft.com/library/eybzcxe6(v=vs.85).aspx)。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您稍早產生的結構描述會描述協調流程中的訊息所需的 「 類型 」。 訊息通常是的變數，其對應的結構描述所定義的型別。 現在，您必須建立協調流程的訊息，並將它們連結至您在上一個步驟中產生的結構描述。  
  
1.  BizTalk 專案中新增協調流程。 從 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下**新項目**。 輸入 BizTalk 協調流程的名稱，然後按一下**新增**。  
  
2.  如果它尚未開啟，請開啟 BizTalk 專案，[協調流程檢視] 視窗。 若要這樣做，請按一下**檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。  
  
3.  在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。  
  
4.  以滑鼠右鍵按一下新建立的訊息，然後按**屬性 視窗**。  
  
5.  在 [**屬性**] 窗格**Message_1**，執行下列動作：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|輸入 `Request`|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*SelectTable.TableOperation_dbo_Employee.Select*SelectTable 所在的 BizTalk 專案的名稱。 TableOperation_dbo_Employee 是 EMPLOYEE 資料表的 Select 作業產生的結構描述。|  
  
6.  重複步驟 2 來建立新的訊息。 在 **屬性**窗格中的新訊息，執行下列動作：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|輸入 `Response`|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*SelectTable.TableOperation_dbo_Employee.SelectResponse*。|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]執行 SQL Server 上的作業。 在此協調流程中，卸除在要求訊息定義的接收位置。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會取用這個訊息，並將它傳遞到 SQL Server。 從 SQL Server 的回應會儲存到另一個位置。 您必須包含傳送和接收圖形，將訊息傳送至 SQL Server，並接收回應，分別。 選取作業的範例協調流程如下所示：  
  
 ![SQL Server 上的選取作業的協調流程](../../adapters-and-accelerators/adapter-sql/media/e74e342f-ba66-41fe-bd34-d45cd8767ef8.gif "e74e342f-ba66-41fe-bd34-d45cd8767ef8")  
  
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
|ReceiveMessage|-設定**訊息**到*要求*<br />-設定**作業**到*MessageIn.Select.Request*|  
|SendMessage|-設定**訊息**到*要求*<br />-設定**作業**到*LOBPort.Select.Request*|  
|ReceiveResponse|-設定**訊息**到*回應*<br />-設定**作業**到*LOBPort.Select.Response*|  
|SendResponse|-設定**訊息**到*回應*<br />-設定**作業**到*ResponseOut.Select.Request*|  
  
 指定這些屬性之後，訊息 圖形和連接埠都連接，且您的協調流程完成。  
  
 現在，您必須建置 BizTalk 方案，並將它部署到 BizTalk Server。 如需詳細資訊，請參閱 <<c0> [ 建置和執行協調流程](../../core/building-and-running-orchestrations.md)。  
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在 [協調流程] 窗格底下[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 您必須使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定應用程式。 如需逐步解說，請參閱 <<c0> [ 逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。
  
 設定應用程式包含：  
  
- 選取應用程式主機。  
  
- 對應至實體連接埠在協調流程中建立的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 此協調流程中，您必須：  
  
  - 定義位置上的硬碟和對應的檔案連接埠，您將會卸除要求訊息。 BizTalk 協調流程將會取用的要求訊息，並將它傳送到 SQL Server 資料庫。  
  
  - 定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含從 SQL Server 資料庫回應的回應訊息。  
  
  - 定義實體 Wcf-custom 或 WCF SQL 傳送埠將訊息傳送至 SQL Server 資料庫。 您也必須在傳送埠中指定的動作。 如需有關如何建立連接埠的資訊，請參閱 <<c0> [ 手動設定 SQL 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)。
  
    > [!NOTE]
    >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立繫結檔案，其中包含連接埠與那些連接埠設定動作的相關資訊。 您可以將從這個繫結檔案匯入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 （適用於輸出的呼叫） 的傳送埠或接收埠 （適用於輸入的呼叫）。 如需詳細資訊，請參閱 <<c0> [ 設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 BizTalk 應用程式，從 SQL Server 資料庫資料表中選取記錄。 如需啟動 BizTalk 應用程式的步驟，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。
  
 在這個階段，請確定：  
  
-   FILE 接收埠以接收要求訊息的協調流程正在執行。  
  
-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  
  
-   WCF 自訂] 或 [WCF-SQL 傳送埠將訊息傳送至 SQL Server 資料庫正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
> [!IMPORTANT]
>  如果您正在執行的使用者定義型別 (Udt) 資料行的資料表上的作業，請確定個別的組件的 Udt 上有相同的位置[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]可執行檔，btsntsvc.exe。 可執行檔通常會在`<installation drive>:\Program Files\Microsoft BizTalk Server <version>`。 在此範例中，[員工] 資料表會有一個 UDT （點） 資料行。 請確認您已複製的相同位置中的個別組件[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]可執行檔。  
> 
>  如需有關如何建立 UDT 的資訊，請參閱 <<c0> [ 建立使用者定義型別](https://msdn.microsoft.com/library/ms131106.aspx)。 如需如何註冊 SQL Server 中的 UDT 的資訊，請參閱[Register User-Defined SQL Server 中的型別](https://msdn.microsoft.com/library/ms131079.aspx)。  
  
## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，您必須先卸除要求訊息至檔案接收位置。 要求訊息的結構描述必須符合的結構描述，選取您稍早產生的作業。 例如，要選取 [員工] 資料表中的所有記錄的要求訊息是：  
  
```  
<Select xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
  <Columns>*</Columns>  
  <Query>where Employee_ID=10001</Query>  
</Select>  
```  
  
 此要求訊息會從滿足指定條件的員工資料表擷取記錄`<Query>`項目。 如果您想要從資料表中擷取特定資料行，您必須指定在 < 資料行\>項目，以逗號分隔，以相同順序出現在資料表定義。 如果您不想指定條件，以擷取資料，請將保留`<Query>`空白的項目。 請參閱[Insert、 Update、 Delete 與資料表和檢視表的選取作業的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md)如需有關執行 SQL Server 上的基本 DML 作業的要求訊息結構描述資料庫資料表和檢視使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
 協調流程取用訊息，並將它傳送到 SQL Server 資料庫。 SQL Server 資料庫的回應會儲存在其他定義的協調流程一部分的檔案位置。 例如，上述的要求訊息的 SQL Server 資料庫的回應是：  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<SelectResponse xmlns="mssql://Microsoft.LobServices.Sql/2008/01/TVOp/dbo/Employee">  
  <SelectResult>  
    <Employee xmlns="mssql://Microsoft.LobServices.Sql/2008/01/Types/Tables/dbo">  
      <Employee_ID>10001</Employee_ID>  
      <Name>John</Name>  
      <DOJ>1983-12-31T00:00:00Z</DOJ>  
      <Designation>Manager</Designation>  
      <Job_Description>Management</Job_Description>  
      <Photo>EjRVYzRFVQ==</Photo>  
      <Rating>1,2</Rating>  
      <Salary>100000.00</Salary>  
      <Last_Modified>AAAAAAAAD6I=</Last_Modified>  
    </Employee>  
  </SelectResult>  
</SelectResponse>  
```  
  
## <a name="best-practices"></a>最佳作法  
  
-   您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。 一旦您產生繫結檔案時，您可以匯入的組態設定檔案，，讓您不需要建立項目，例如傳送埠和接收相同的協調流程的連接埠。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用的 SQL 配接器繫結](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md)。
  
-   如果您要插入、 更新或刪除大量的資料進行確定您正確的逾時值個 WCF 配接器和設定 MSDTC 交易。 如需詳細資訊，請參閱 「 無法插入、 更新或刪除大量資料，在單一作業中使用 BizTalk Server 配接器 」 中的問題[疑難排解操作問題 SQL 配接器](../../adapters-and-accelerators/adapter-sql/troubleshoot-operational-issues-with-the-sql-adapter.md)。  
  
## <a name="see-also"></a>另請參閱  
[使用 SQL 配接器開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)