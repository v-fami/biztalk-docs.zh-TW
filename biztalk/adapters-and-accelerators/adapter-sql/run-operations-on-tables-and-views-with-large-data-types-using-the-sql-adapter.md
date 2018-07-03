---
title: 具有使用 SQL 配接器的大型資料類型的資料表和檢視表執行作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cec15b01-7a57-4917-8c21-44a1cfaadc59
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2c1bc305e45747c4471894cc362ebeeec2ee36a9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013103"
---
# <a name="run-operations-on-tables-and-views-with-large-data-types-using-the-sql-adapter"></a>具有使用 SQL 配接器的大型資料類型的資料表和檢視表執行作業
[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]啟用讀取和更新的大型資料類型資料行中的資料，也就是配接器用戶端、 varchar （max）、 nvarchar （max） 或 varbinary （max）。 若要從這類資料行中讀取資料，配接器用戶端可以使用選取的作業。 若要插入或更新資料到這類資料行，配接器會公開 < column_name > 設定作業中，其中 < column_name > 是類型 varchar （max）、 nvarchar （max），或 varbinary （max） 資料行的名稱。  
  
 此外，在 SQL Server 2008 中，您可以儲存非結構化的資料，例如文字文件和影像 varbinay(max) 資料行。 這類非結構化的資料就會呼叫 FILESTREAM 資料。 FILESTREAM 資料可以儲存為檔案系統上的檔案。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可讓用戶端將輸入資料行類型 varbinary （max） FILESTREAM 資料。 如需有關 FILESTREAM 儲存體的詳細資訊，請參閱 < [FILESTREAM 概觀](https://msdn.microsoft.com/library/bb933993(SQL.100).aspx)。  
  
 本主題提供您必須執行特定工作的相關資訊的電腦上執行 SQL Server 和執行配接器用戶端能夠插入或更新 FILESTREAM 資料的電腦。 本主題也會提供執行插入 FILESTREAM 資料的集合 < column_name > 作業的指示。  
  
> [!NOTE]
>  如果您正在執行具有使用者定義類型的資料行的資料表上的作業，請確定您參考[資料表和檢視與使用 SQL 配接器的使用者定義型別上的作業](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md)開始開發您的應用程式之前。  
  
## <a name="prerequisites"></a>必要條件  
 您必須執行 SQL Server 的電腦和執行配接器用戶端電腦上執行下列工作。  

  
- **執行 SQL Server 的電腦上**  
  
  -   您必須在 SQL Server 執行個體上啟用 FILESTREAM。 如需詳細資訊，請參閱 < [ http://go.microsoft.com/fwlink/?LinkId=122486 ](http://go.microsoft.com/fwlink/?LinkId=122486)。  
  
  -   您必須建立啟用 FILESTREAM 的資料庫。 如需詳細資訊，請參閱 < [ http://go.microsoft.com/fwlink/?LinkId=122487 ](http://go.microsoft.com/fwlink/?LinkId=122487)。  
  
  -   您必須擁有儲存 FILESTREAM 資料的資料表。 如需詳細資訊，請參閱 < [ http://go.microsoft.com/fwlink/?LinkId=122488 ](http://go.microsoft.com/fwlink/?LinkId=122488)。  
  
  -   您必須在裝載 SQL Server 資料庫的電腦上設定 MSDTC。 如需有關如何設定 MSDTC 的指示，請參閱[設定 SQL Server 和配接器的用戶端上的 MSDTC](../../adapters-and-accelerators/adapter-sql/configure-msdtc-on-sql-server-and-adapter-client.md)。  
  
- **在電腦上執行 配接器用戶端**  
  
  -   您必須安裝 SQL 用戶端連接性 SDK。 您可以安裝 SQL 用戶端連接性 SDK，以執行 SQL Server 2008 安裝程式，然後選取**SQL 用戶端連接性 SDK**中**特徵選取**精靈頁面。 配接器會使用 sqlncli10.dll，安裝 SQL 用戶端連接性 SDK，與用於執行 FILESTREAM 操作。  
  
  -   您必須執行配接器用戶端的電腦上設定 MSDTC。 如需有關如何設定 MSDTC 的指示，請參閱[設定 SQL Server 和配接器的用戶端上的 MSDTC](../../adapters-and-accelerators/adapter-sql/configure-msdtc-on-sql-server-and-adapter-client.md)。  
  
  您已完成這些工作之後，您為所有設定為插入或更新 SQL Server 2008 資料庫資料表中的 FILESTREAM 資料。  
  
## <a name="how-this-topic-demonstrates-operations-on-large-data-types"></a>本主題將大型資料類型上的作業的示範  
 為了示範如何設定 < column_name > 資料表上執行作業含有大型資料類型，需要資料表，其識別碼和文件的資料行的記錄。 識別碼資料行的類型 uniqueidentifier 且採用 GUID。 文件資料行是 varbinary （max） 類型。 假設識別碼資料行已經有一個 GUID '`438B7B4C-5491-409F-BCC1-78817C399EC3`'。 若要更新的文件欄，配接器會公開 SetDocument 作業。  
  
> [!NOTE]
>  SQL Server 2008 中，為了示範 FILESTREAM 作業，假設文件資料行可儲存 FILESTREAM 資料。  
  
## <a name="how-to-perform-operations-on-a-sql-server-database"></a>如何在 SQL Server 資料庫上執行作業  
 使用執行 SQL Server 資料庫上的作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及中所述的程序性工作[開發使用 SQL 配接器的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)。 若要執行大型資料類型的資料表作業，這些工作如下：  
  
1. 建立 BizTalk 專案，並產生結構描述的集合 < column_name > 作業。 本主題中，產生結構描述**SetDocument**作業**記錄**資料表。  
  
2. 建立傳送和接收訊息，從 SQL Server 資料庫的 BizTalk 專案中的訊息。  
  
3. 建立協調流程叫用 SetDocument 資料表上的作業記錄。  
  
4. 建置和部署 BizTalk 專案。  
  
5. 設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
6. 啟動 BizTalk 應用程式。  
  
   本主題提供執行這些工作的指示。  
  
## <a name="sample-based-on-this-topic"></a>根據本主題的範例  
 ，FILESTREAMOperation，根據本主題提供了範例[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱 < [SQL 配接器的範例](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md)。  
  
## <a name="generating-schema"></a>產生結構描述  
 若要示範如何更新大型資料類型的資料行中的值，產生 SetDocument 作業的記錄資料表的結構描述。 您必須建立 BizTalk 專案，並使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生結構描述。 請參閱[擷取使用 SQL 配接器的 Visual Studio 中的 SQL Server 作業的中繼資料](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)如需有關如何產生結構描述。  
  
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
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*SetOperation.TableOperation_dbo_Records.SetDocument*SetOperation 所在的 BizTalk 專案的名稱。 TableOperation_dbo_Records 是 SetDocument 作業記錄資料表上產生的結構描述。|  
  
6.  重複步驟 2 來建立新的訊息。 在 **屬性**窗格中的新訊息，執行下列動作：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|輸入 `Response`|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*SetOperation.TableOperation_dbo_Records.SetDocumentResponse*。|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]執行 SQL Server 上的作業。 在此協調流程中，卸除在要求訊息定義的接收位置。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會取用這個訊息，並將它傳遞到 SQL Server。 從 SQL Server 的回應會儲存到另一個位置。 您必須包含傳送和接收圖形，將訊息傳送至 SQL Server，並接收回應，分別。 範例協調流程 SetDocument 作業如下所示：  
  
 ![用於執行 FILESTREAM 操作的協調流程](../../adapters-and-accelerators/adapter-sql/media/b8c1c04c-142f-44a0-a545-8ec0cfdd9a5b.gif "b8c1c04c-142f-44a0-a545-8ec0cfdd9a5b")  
  
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
|ReceiveMessage|-設定**訊息**到*要求*<br />-設定**作業**到*MessageIn.FileStream.Request*|  
|SendMessage|-設定**訊息**到*要求*<br />-設定**作業**到*LOBPort.FileStream.Request*|  
|ReceiveResponse|-設定**訊息**到*回應*<br />-設定**作業**到*LOBPort.FileStream.Response*|  
|SendResponse|-設定**訊息**到*回應*<br />-設定**作業**到*ResponseOut.FileStream.Request*|  
  
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
  
    > [!IMPORTANT]
    >  要輸入 FILESTREAM 資料的作業必須在交易內執行。 因此，請確定**UseAmbientTransaction**繫結屬性設定為 **，則為 True** Wcf-custom 或 WCF SQL 傳送埠。 如需有關繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
    > 
    > [!IMPORTANT]
    >  執行作業插入 FILESTREAM 資料您永遠必須使用 Windows 驗證來連接到 SQL Server 上 Wcf-custom 或 WCF SQL 傳送埠。 因此，在**認證**索引標籤，在連接埠屬性 對話方塊中，選取**不會使用單一登入**選項，並將保留的使用者名稱和密碼的空白。  
    > 
    > [!NOTE]
    >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立繫結檔案，其中包含連接埠與那些連接埠設定動作的相關資訊。 您可以將從這個繫結檔案匯入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 （適用於輸出的呼叫） 的傳送埠或接收埠 （適用於輸入的呼叫）。 如需詳細資訊，請參閱 <<c0> [ 設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 BizTalk 應用程式來執行**SetDocument**上的作業**記錄**資料表。 如需有關啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。
  
 在這個階段，請確定：  
  
-   FILE 接收埠以接收要求訊息的協調流程正在執行。  
  
-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  
  
-   WCF 自訂] 或 [WCF-SQL 傳送埠將訊息傳送至 SQL Server 資料庫正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，您必須先卸除要求訊息至檔案接收位置。 要求訊息的結構描述必須符合您稍早產生 SetDocument 作業的結構描述。 比方說，是要更新的文件資料行的要求訊息：  
  
```  
<SetDocument xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Records">  
  <Filter>WHERE Id='438B7B4C-5491-409F-BCC1-78817C399EC3'</Filter>  
  <Data>UwBlAHQAdgBfAHYAYQByAGIAaQBuAGEAcgB5AE0AQQBYAA==</Data>  
</SetDocument>  
```  
  
> [!IMPORTANT]
>  `Filter`元素必須包含 WHERE 子句基礎所在配接器更新的記錄。 `Data`元素必須包含您想要插入至文件資料行的 base64 編碼值。  
  
 此要求訊息會更新文件的資料行，以指定的值。 協調流程取用訊息，並將它傳送到 SQL Server 資料庫。 從 SQL Server 資料庫的回應會儲存在其他定義的協調流程一部分的檔案位置。 例如，從先前的要求訊息的 SQL Server 資料庫的回應是：  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<SetDocumentResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Records" />  
```  
  
 配接器傳送空的回應**設定 < column_name >** 作業。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。 一旦您產生繫結檔案時，您可以匯入的組態設定檔案，，讓您不需要建立項目，例如傳送埠和接收相同的協調流程的連接埠。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用配接器繫結](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md)。
  
## <a name="see-also"></a>另請參閱  
[使用 SQL 配接器開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)