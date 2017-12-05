---
title: "使用 BFILE 資料型別使用 BizTalk Server 的 Oracle 資料庫中執行的資料表上的作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- operations on tables with BFILE data types, performing by using BizTalk Server
- BFILE data types
ms.assetid: 2e4af5a9-acde-419b-a99c-3eaa0c72daa8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a716056bdeb16900c23bdf748028e9d60e4316ab
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="run-operations-on-tables-with-bfile-data-types-in-oracle-database-using-biztalk-server"></a>使用 BFILE 資料型別使用 BizTalk Server 的 Oracle 資料庫中執行的資料表上的作業
[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]資料表和預存程序中支援 BFILE 資料型別。 本節提供如何有 BFILE 資料型別的一個資料行的資料表上執行作業的資訊。 如需有關如何[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援 BFILE，請參閱[資料表 BFILE 資料類型的 Oracle 資料庫中的作業](../../adapters-and-accelerators/adapter-oracle-database/operations-on-tables-with-bfile-data-types-in-oracle-database.md)。  
  
## <a name="setting-up-your-oracle-database-server-for-operations-on-bfile"></a>設定 Oracle 資料庫伺服器上 BFILE 作業  
 本節示範如何叫用的程序會將記錄插入 SCOTT。CUSTOMERDOC 資料表。 這個資料表包含 BFILE 資料型別資料行，而由的執行 SQL 指令碼隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]範例。 若要深入了解範例和 SQL 指令碼，請參閱[適用於 Oracle 資料庫配接器範例](../../adapters-and-accelerators/adapter-oracle-database/samples-for-the-oracle-database-adapter.md)。  
  
 執行指令碼來建立 CUSTOMERDOC 資料表之後，您必須執行，讓作業在 BFILE 資料型別上的 Oracle 資料庫的電腦上執行某些動作。 您必須對 Oracle 資料庫執行的工作如下：  
  
1.  執行 Oracle 資料庫的電腦上建立目錄 C:\MYDIR。  
  
2.  Oracle 資料庫中建立邏輯的目錄。 這通常需要以 SYSDBA 的權限的使用者。 例如：  
  
    ```  
    CREATE OR REPLACE DIRECTORY MYDIR AS 'C:\MYDIR';  
    ```  
  
3.  加入使用者存取在 Oracle 中的邏輯目錄的權限。 例如：  
  
    ```  
    GRANT READ, WRITE ON DIRECTORY MYDIR to SCOTT;  
    ```  
  
4.  複製到執行 Oracle 資料庫時，在 Oracle 中的邏輯目錄相關聯的電腦上的實體目錄位置，存取檔案。 您在步驟 1 中建立此目錄。  
  
     根據上述範例中，將檔案複製，到目錄 C:\MYDIR customer_profile.txt。 這個檔案現在是可供 BFILE 作業。 如需有關執行作業的詳細資訊，請參閱[大型物件資料類型所使用 BizTalk Server 的 Oracle 資料庫中之資料表上執行的作業](../../adapters-and-accelerators/adapter-oracle-database/run-operations-on-tables-with-large-object-data-types-in-oracle-database.md)。  
  
    > [!IMPORTANT]
    >  BFILE 資料型別之資料表上支援 ReadLOB 作業。 不支援 UpdateLOB 作業。 不過，使用者可以或者使用更新作業。  
  
## <a name="how-to-perform-operations-using-bfile-data-types"></a>如何執行作業使用 BFILE 資料型別  
 針對 Oracle 資料庫使用執行運算[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[開發 BizTalk 應用程式與 Oracle 資料庫的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)。 叫用的程序會將記錄插入 SCOTT。CUSTOMERDOC 資料表，這些工作包括：  
  
1.  建立 BizTalk 專案，並產生 CREATE_CUSTOMERDOC 預存程序結構描述。  
  
2.  建立傳送和從 Oracle 資料庫接收訊息的 BizTalk 專案中的訊息。  
  
3.  建立協調流程叫用 Oracle 資料庫資料表或檢視表上的作業。  
  
4.  建置和部署 BizTalk 專案。  
  
5.  設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
6.  啟動 BizTalk 應用程式。  
  
 本主題提供執行這些工作的指示。  
  
## <a name="sample-based-on-this-topic"></a>根據本主題的範例  
 基礎的範例，Operate_BFILE，本主題也會提供[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱[適用於 Oracle 資料庫配接器範例](../../adapters-and-accelerators/adapter-oracle-database/samples-for-the-oracle-database-adapter.md)。  
  
## <a name="generating-schema"></a>產生結構描述  
 本主題中，以示範如何執行 BFILE 資料行，資料表上的作業我們會叫用 CREATE_CUSTOMERDOC 程序。 此程序之下 SCOTT\Package\ACCOUNT_PKG 結構描述中，執行下列 SQL 指令碼提供範例。 此程序會採用 BFILE 記錄類型和 CUSTOMERDOC 資料表中新增一筆記錄。 如需 SQL 指令碼的詳細資訊，請參閱[結構描述範例](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md)。  
  
 請參閱[擷取 Oracle 作業在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)如需有關如何產生結構描述。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您先前產生的結構描述會描述 「 類型 」 所需的協調流程中的訊息。 訊息通常是為其型別由對應的結構描述所定義的變數。 您必須連結產生的結構描述您在第一個步驟中的訊息從 BizTalk 專案的 [協調流程檢視] 視窗。  
  
 本主題中，您必須建立兩個訊息，其中將要求傳送至 Oracle 資料庫與另一個則接收回應。  
  
 執行下列步驟來建立訊息，並將其連結至結構描述。  
  
#### <a name="to-create-messages-and-link-to-schema"></a>建立訊息，以及連結至結構描述  
  
1.  如果它尚未開啟，請開啟 BizTalk 專案中，[協調流程檢視] 視窗。 若要這樣做，請按一下**檢視**，指向 **其他視窗**，然後按一下 **協調流程檢視**。  
  
2.  在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。  
  
3.  以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。  
  
4.  在**屬性**窗格**Message_1**，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|型別**要求**。|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*BFILE_Operations.OracleDBBindingSchema.CREATE_CUSTOMERDOC*，其中*BFILE_Operations*的名稱您的 BizTalk 專案。 *OracleDBBindingSchema*是 CREATE_CUSTOMERDOC 程序產生的結構描述。|  
  
5.  重複步驟 2 來建立新的訊息。 在**屬性**窗格新訊息中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|型別**回應**。|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*BFILE_Operations.OracleDBBindingSchema.CREATE_CUSTOMERDOCResponse*。|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]來執行程序。 在此協調流程中，卸除要求訊息已定義的接收位置。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會取用這個訊息，並將它傳遞到 Oracle 資料庫中，透過 ODP。 從 Oracle 資料庫的回應會儲存到另一個位置。 在 Oracle 資料庫資料表中執行 BFILE 資料行上的作業的一般協調流程就會包含：  
  
-   傳送和接收圖形以將訊息傳送至 Oracle 資料庫，並接收回應。  
  
-   單向接收埠以接收要求訊息傳送到 Oracle 資料庫。  
  
-   雙向傳送埠以傳送要求訊息到 Oracle 資料庫，並接收回應。  
  
-   單向傳送埠，以便從 Oracle 資料庫的回應傳送到資料夾。  
  
 範例協調流程如下所示：  
  
 ![用於以 BFILE 執行操作的協調流程](../../adapters-and-accelerators/adapter-oracle-database/media/5902cf48-0555-4d9a-b902-5208949b6c87.gif "5902cf48-0555-4d9a-b902-5208949b6c87")  
  
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
|FileIn|-設定**識別碼**至*FileIn*<br />-設定**類型**至*FileInType*<br />-設定**通訊模式**至*單向*<br />-設定**通訊方向**至*接收*|  
|LOBPort|-設定**識別碼**至*LOBPort*<br />-設定**類型**至*LOBPortType*<br />-設定**通訊模式**至*要求-回應*<br />-設定**通訊方向**至*傳送接收*|  
|SaveResponse|-設定**識別碼**至*SaveResponse*<br />-設定**類型**至*SaveResponseType*<br />-設定**通訊模式**至*單向*<br />-設定**通訊方向**至*傳送*|  
  
## <a name="specify-messages-for-action-shapes-and-connect-them-to-ports"></a>指定訊息的動作圖形，並將它們連接至連接埠  
 下表指定屬性和其值，您應該設定來指定動作圖形的訊息，以及連結至連接埠的訊息。 圖形資料行中所列的名稱是 「 訊息 」 圖形的名稱，為顯示在協調流程中先前所述。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveMessage|-設定**訊息**至*要求*<br />-設定**作業**至*FileIn.Create_BFILE。要求*|  
|SendMessage|-設定**訊息**至*要求*<br />-設定**作業**至*LOBPort.Create_BFILE。要求*|  
|ReceiveResponse|-設定**訊息**至*回應*<br />-設定**作業**至*LOBPort.Create_BFILE。回應*|  
|SendResponse|-設定**訊息**至*回應*<br />-設定**作業**至*SaveResponse.Create_BFILE。要求*|  
  
 您指定這些屬性之後，連接的訊息 圖形和連接埠，而且您的協調流程已完成。  
  
 您現在必須建置 BizTalk 方案，並部署到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱[建置和執行協調流程](../../core/building-and-running-orchestrations.md)。  
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 部署 BizTalk 專案之後，您稍早建立的協調流程會列在**協調流程**BizTalk Server 管理主控台 窗格。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 如需逐步解說，請參閱[逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。
  
 設定應用程式包括：  
  
-   選取應用程式的主機。  
  
-   對應至 BizTalk Server 管理主控台中的實體連接埠在協調流程中建立的連接埠。 此協調流程中，您必須：  
  
    -   定義位置上的硬碟和對應的檔案連接埠，您將在此置放要求訊息。 BizTalk 協調流程會使用要求訊息，並將它傳送到 Oracle 資料庫。  
  
    -   定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含從 Oracle 資料庫回應的回應訊息。  
  
    -   定義實體 Wcf-custom 或 Wcf-oracledb 傳送埠將訊息傳送至 Oracle 資料庫。 您也必須在傳送埠中指定的動作。 如需如何建立 Wcf-custom 或 Wcf-oracledb 連接埠相關資訊，請參閱[手動設定 Oracle 資料庫配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md)。  
  
        > [!NOTE]
        >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠的設定動作的相關資訊的繫結檔案。 您可以從 BizTalk Server 管理主控台來建立 （適用於傳出呼叫） 的傳送埠或接收埠 （適用於進行傳入呼叫時），以匯入此繫結檔案。 如需詳細資訊，請參閱[設定使用 Oracle 資料庫的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md)。  
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 BizTalk 應用程式叫用 CUSTOMERDOC 資料表中建立一筆記錄的程序。 如需啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。  
  
 在這個階段，請確定：  
  
-   FILE 接收埠以接收要求訊息的協調流程執行。  
  
-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  
  
-   Wcf-custom 或 Wcf-oracledb 傳送埠將訊息傳送至 Oracle 資料庫正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，您必須先卸除要求訊息到檔案接收位置。 要求訊息的結構描述必須符合您先前產生的程序的結構描述。 請參閱[函數和程序的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-functions-and-procedures.md)如需有關要求訊息結構描述，來叫用程序使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
 例如，要叫用 CREATE_CUSTOMERDOC 程序的要求訊息是：  
  
```  
<CREATE_CUSTOMERDOC xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG">  
  <CNAME>John Smith</CNAME>  
  <CDOC>MYDIR/John_Smith_profile.txt</CDOC>  
</CREATE_CUSTOMERDOC>  
```  
  
> [!NOTE]
>  文字檔，John_Smith_profile.txt 中必須要有與 Oracle 中的邏輯目錄相關聯的實體目錄位置。 例如，文字檔案中必須要有 C:\MYDIR  
  
 協調流程取用訊息，並將它傳送到 Oracle 資料庫。 從 Oracle 資料庫的回應會儲存在其他的協調流程中定義的檔案位置。 比方說，是來自上述的要求訊息的 Oracle 資料庫的回應：  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CREATE_CUSTOMERDOCResponse xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG"></CREATE_CUSTOMERDOCResponse>  
```  
  
> [!NOTE]
>  您可以建立類似的協調流程有 BFILE 類型欄位的資料表中讀取資料。 隨附於 SQL 指令碼[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]建立 ACCOUNT_PKG 包含 GET_CUSTOMERDOC 程序。 您可以使用此程序來擷取 SCOTT BFILE 資料。CUSTOMERDOC 資料表。  
>   
>  範例中，Operate_BFILE，也是隨附的範例[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 這個範例示範如何將記錄插入至 SCOTT。使用 CREATE_CUSTOMERDOC CUSTOMERDOC 資料表預存程序 （如本主題中。）此範例也示範如何從 SCOTT 讀取 BFILE 資料。使用 GET_CUSTOMERDOC CUSTOMERDOC 資料表預存程序。  
  
## <a name="possible-exceptions"></a>可能的例外狀況  
 如需有關例外狀況資訊可能會遇到執行 DML 作業使用時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[例外狀況和錯誤處理](../../adapters-and-accelerators/adapter-oracle-database/exceptions-and-error-handling-with-the-oracle-database-adapter.md)。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。 一旦產生繫結檔案時，您可以匯入組態設定從檔案，因此您不需要建立傳送埠、 接收埠，等。 針對相同的協調流程。 如需繫結檔案的詳細資訊，請參閱[重複使用的 Oracle 資料庫配接器繫結](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md)。  
  
## <a name="see-also"></a>請參閱  
[開發 BizTalk 應用程式與 Oracle 資料庫的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)