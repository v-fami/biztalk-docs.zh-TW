---
title: "交易式配接器 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31a13377-cc89-4763-ad1b-508a16fc9708
caps.latest.revision: "36"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f934857103952a035159cc08678c8ce8c8e51a56
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="transactional-adapter-biztalk-server-sample"></a>交易式配接器 （BizTalk Server 範例）
交易式配接器範例示範如何建立和使用在處理期間針對資料庫明確 Microsoft 分散式交易協調器 (MSDTC) 交易[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]訊息。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 此範例包含接收配接器，會依使用者指定的間隔執行 SQL 陳述式，以便從使用 MSDTC 交易的 SQL Server 資料庫取得資料。 資料然後提交給[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]相同交易的內容下，以訊息形式的 MessageBox 資料庫。  
  
 對應的傳送配接器會使用交易環境中的 BizTalk 訊息的輸入，以執行使用者指定的 SQL 預存程序。 它使用該訊息中的特定資料，透過上述相同交易從 MessageBox 資料庫中尋找和刪除對應訊息。  
  
## <a name="how-this-sample-is-designed-and-why"></a>此範例的設計方式和原因  
 這個範例在其解決方案中有兩個專案。 第一個是管理專案 (Admin)，可在執行階段前用來讓使用者設定使用此配接器的接收位置和傳送埠。 第二個是執行階段專案 (Runtime)，可在傳送配接器及接收配接器正在執行時執行。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 這個範例位於下列 SDK 位置：  
  
 \<*範例路徑*\>\Samples\AdaptersDevelopment\TransactionalAdapter。 管理組態專案位於 \Admin 資料夾，而執行階段專案則存在於 \Runtime 資料夾。  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|Admin 專案檔案名稱|Admin 專案檔案描述|  
|----------------------------|------------------------------------|  
|TransactionalAdmin.csproj|用於執行階段前組態的配接器管理專案檔案|  
|TransactionalReceiveHandler.xsd|接收處理常式屬性的 XSD|  
|TransactionalReceiveLocation.xsd|接收位置屬性的 XSD|  
|TransactionalTransmitLocation.xsd|傳輸位置屬性的 XSD|  
|TransactionalTransmitHandler.xsd|傳輸處理常式屬性的 XSD|  
|TransactionalAdapterManagement.cs|配接器組態管理。 包含 GetConfigSchema，這是由 BizTalk 配接器架構所叫用，以傳回它支援的每一個組態類型 (共四個可能類型) 的 XSD 組態結構描述。|  
  
|執行階段專案檔案名稱|執行階段專案檔案描述|  
|------------------------------|--------------------------------------|  
|Transactional.csproj|配接器執行階段專案檔案|  
|TransactionalAsyncBatch.cs|配接器傳送組件的非同步實作|  
|TransactionalDeleteBatch.cs|刪除訊息及表決批次以認可或中止交易|  
|TransactionalProperties.cs|擷取和設定組態屬性|  
|TransactionalReceiver.cs|建立和管理接收結束點|  
|TransactionalReceiverEndpoint.cs|每個接收位置的實際監聽或輪詢|  
|TransactionalTransmitter.cs|從傳訊引擎接受要被傳送的訊息批次|  
  
## <a name="how-to-use-this-sample"></a>如何使用此範例  
 這個範例主要提供可用來做為使用明確交易建立自訂傳送配接器及接收配接器的架構。  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
  
> [!IMPORTANT]
>  如果 BizTalk 安裝是 64 位元，或安裝位置已有修改，則需要隨之變更 OutboundAssemblyPath、InboundAssemblyPath、AdapterMgmtAssemblyPath。  
  
#### <a name="create-a-strong-name-key-for-the-transactional-adapter-sample"></a>建立交易式配接器範例的強式名稱金鑰  
  
1.  啟動 **Visual Studio 命令提示字元**。  
  
2.  在命令提示字元輸入下列命令，然後按下 ENTER：  
  
    ```  
    cd \Program Files\Microsoft BizTalk Server <version>\SDK\Samples\AdaptersDevelopment\TransactionalAdapter\Runtime  
    ```  
  
3.  在命令提示字元輸入下列命令，然後按下 ENTER：  
  
    ```  
    sn –k TransactionalAdapter.snk  
    ```  
  
4.  在命令提示字元中，輸入 **結束**, ，然後按 enter 鍵關閉命令提示字元 視窗。  
  
#### <a name="build-the-transactional-adapter-solution"></a>建立交易式配接器解決方案  
  
1.  按一下  **啟動**, ，指向  **所有程式**, ，指向 **附屬應用程式**, ，然後按一下  **Windows 檔案總管**。  
  
2.  瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\AdaptersDevelopment\TransactionalAdapter，然後按兩下**TransactionalAdapter.sln**來開啟這個解決方案[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
  
3.  若要建置這兩個方案總管] 中的交易式配接器專案 （Admin 和 Runtime），以滑鼠右鍵按一下 **解決方案 TransactionalAdapter**, ，然後按一下 [ **重建**。  
  
## <a name="running-this-sample"></a>執行此範例  
  
#### <a name="register-the-transactional-adapter"></a>註冊交易式配接器  
  
1.  在 [Windows 檔案總管] 中，瀏覽至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\AdaptersDevelopment\TransactionalAdapter\Admin。  
  
2.  若要將交易式配接器的資料加入至登錄中，按兩下 **TransactionalAdmin.reg**。  
  
    > [!NOTE]
    >  **TransactionalAdmin.reg**包含硬式編碼路徑 C:\Program Files\Microsoft BizTalk Server\\。 如果您未將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝在預設位置中，或者已從舊版升級 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝，則必須以適當的路徑來修改 TransactionalAdmin.reg 檔案。 更新與 "InboundAssemblyPath"、"OutboundAssemblyPath" 和 "AdapterMgmtAssemblyPath" 值相關聯的路徑，以指向指定檔案的正確位置。  
  
    > [!IMPORTANT]
    >  如果您在 64 位元電腦上安裝 BizTalk，變更所有 HKEY_CLASSES_ROOT\CLSID\ 登錄項目執行個體都變更為 HKEY_CLASSES_ROOT\Wow6432Node\CLSID\ 中 **TransactionalAdmin.reg** 登錄檔。  
  
3.  在 **登錄編輯程式** 對話方塊中，按一下  **是** 以將範例配接器新增至登錄，然後按一下 **確定**。  
  
4.  若要關閉 Windows 檔案總管中，按一下 **檔案**, ，然後按一下  **關閉**。  
  
#### <a name="add-the-transactional-adapter-to-biztalk-server"></a>將交易式配接器加入至 BizTalk Server  
  
1.  按一下**啟動**功能表上，選取**所有程式**，選取[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後選取**BizTalk Server 管理**。  
  
2.  在[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk Server 管理**樹狀目錄中，展開  **BizTalk 群組**樹狀結構、，然後展開 **平台設定**樹狀目錄中。  
  
3.  以滑鼠右鍵按一下 **配接器**, ，按一下  **新增**, ，然後按一下  **配接器**。  
  
4.  在 **配接器屬性** 對話方塊方塊中，執行下列動作。  
  
    |使用|動作|  
    |--------------|----------------|  
    |名稱|型別 **TransactionalAdapter**。|  
    |配接器|選取 **Txn** 從下拉式清單。 執行此項目出現 **TransactionalAdmin.reg** 先前檔案。|  
    |Description|型別 **範例交易式配接器**。|  
  
5.  按一下 **[確定].** 配接器隨即會出現在 BizTalk 管理主控台右側視窗的配接器清單中。  
  
#### <a name="create-a-receive-port-and-location-that-uses-the-adapter"></a>建立使用配接器的接收埠和接收位置  
  
1.  展開**BizTalk 群組 [伺服器名稱]**節點[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**應用程式**] 節點，展開 [ **BizTalk Application 1**節點。  
  
2.  以滑鼠右鍵按一下 **接收埠**, ，然後按一下  **新增**, ，請選取 **單向接收埠。**  
  
3.  如 **名稱**, ，輸入 **TxnReceivePort1**, ，然後按一下  **確定**。  
  
4.  以滑鼠右鍵按一下 **接收位置** 節點中，按一下  **新增**, ，然後選取 **單向接收位置**。  
  
5.  在**選取接收埠** 對話方塊中，選取 **TxnReceivePort1**, ，然後按一下  **確定**。  
  
6.  在 **接收位置屬性** 對話方塊的  **一般** 索引標籤上，輸入 **TxnReceiveLocation1** 的 **名稱**。 請確定 **接收埠** 標籤顯示 **TxnReceivePort1**。  
  
7.  在**類型** 下拉式清單方塊中 **傳輸** 框架中，選取 **TransactionalAdapter。**  
  
8.  在 **接收 * * * 管線** 方塊中，確認 **PassThruReceive** 已選取。 剩下的屬性則保留其預設設定。  
  
9. 按一下  **設定** 旁 **類型** 下拉式方塊。 這樣會顯示這個配接器專用的對話方塊。 指定下列各項視情況需要，然後按一下  **確定**。  
  
    |屬性|設定|  
    |--------------|-------------|  
    |連接字串|用來連接和驗證 Northwind 資料庫的 SQL 資料庫連接字串。 我們稍後會執行使用這個資料庫的 SQL 指令碼。|  
    |命令文字|對 Northwind 資料庫所執行的 SQL 陳述式，用意在取得資料以置入 BizTalk 訊息中。|  
    |Cookie|包含 URI 的一部分，因此輸入唯一的值，例如接收位置的名稱，例如︰ TxnReceiveLocation1。|  
    |輪詢間隔單位|資料輪詢的時間量值單位數。 設定為秒數。|  
    |輪詢間隔|資料輪詢的時間量值單位。 設定為 15 秒。|  
  
10. 按一下**[確定]**關閉 [設定] 對話方塊中，然後**確定**] 以關閉 [**接收位置屬性**對話方塊，即可返回[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。  
  
#### <a name="create-a-send-port-and-send-handler-that-use-the-adapter"></a>建立使用配接器的傳送埠和傳送處理常式  
  
1.  使用 **BizTalk Application 1** 節點保持展開，以滑鼠右鍵按一下 **傳送埠**, ，然後按一下  **新增**, ，然後選取 **靜態單向傳送埠**。  
  
2.  在 **名稱** 欄位中，輸入 **TxnSendPort1**。  
  
3.  在 **傳輸** 框架 **類型** 下拉式清單中，選取**TransactionalAdapter**`.`  
  
4.  在 **傳送管線** 方塊中，確認 **PassThruTransmit** 已選取。  
  
5.  按一下  **設定** 旁 **傳輸** 下拉式清單。在出現的對話方塊中指定下列視情況需要，然後按一下  **確定**。  
  
    |屬性|設定|  
    |--------------|-------------|  
    |Cookie|包含組件的 URI-輸入唯一的值，例如接收位置的名稱，例如︰ **TxnSendPort1**。|  
    |連接字串|用來連接和驗證 Northwind 資料庫的 SQL 資料庫連接字串。 它很可能會用來設定相同 **TxnReceiveLocation1** 接收位置。|  
    |預存程序|預存程序名稱，執行以輪詢資料庫- **sp_txnProc**。 BizTalk 訊息傳送至該主體做為字串參數呼叫預存程序@Data。 例如，使用者會在此情況下稍後預存程序的名稱設定**sp_txnProc**。 配接器的執行階段會對資料庫執行相當於這個呼叫的命令。<br /><br /> exec sp_txnProc @Data = 「 BizTalk 訊息的內容 」|  
  
6.  在左的導覽窗格中，按一下  **篩選**。  
  
7.  在篩選條件運算式編輯器中，輸入下列運算式設定訂閱，讓此傳送埠接收 TxnReceivePort1 接收埠收到的任何訊息。  
  
     輸入這些值︰**BTS。ReceivePortName = = TxnReceivePort1**  
  
    1.  `(property)`  **BTS。ReceivePortName**  
  
    2.  `(operator)`  **==**  
  
    3.  `(value)`  **TxnReceivePort1**  
  
8.  配接器屬性的其餘部分使用的預設值，並選取 **確定**。  
  
## <a name="run-the-sample"></a>執行範例  
  
1.  按一下  **啟動**, ，指向  **所有程式**, ，指向  **Microsoft SQL Server 2008 R2**, ，請選取 **SQL Server Management Studio**。  
  
2.  在 **連接到伺服器** 對話方塊方塊中，請確定 **伺服器類型** 設為 **Database Engine**, ，並輸入認證來驗證資料庫伺服器，然後選取 **連接**。  
  
3.  選取 **新查詢** 工具列按鈕，再將下列內容貼入新的查詢視窗，將測試資料表、 測試資料和測試預存程序插入 Northwind 資料庫。 選取 **Execute** 工具列按鈕。  
  
    ```  
    use [Northwind]  
    GO  
    if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[scratch]') and OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    drop table [dbo].[scratch]  
    GO  
    CREATE TABLE [dbo].[scratch] (  
         [id] [int] IDENTITY (1, 1) NOT NULL ,  
         [msg] [nvarchar] (4000) NOT NULL   
    ) ON [PRIMARY]  
    GO  
    GRANT SELECT , UPDATE , INSERT ON [dbo].[scratch] TO [public]  
    GO  
    if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[sp_txnProc]') and OBJECTPROPERTY(id, N'IsProcedure') = 1)  
    drop procedure [dbo].[sp_txnProc]  
    GO  
    CREATE PROCEDURE [dbo].[sp_txnProc] @Data nvarchar (4000)  
    AS   
    INSERT scratch ( msg ) values ( @Data )  
    GO  
    GRANT EXECUTE ON [dbo].[sp_txnProc] TO [public]  
    GO  
    ```  
  
4.  在[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**傳送埠**節點中，選取**TxnSendPort1**傳送埠，然後選取**啟動**。  
  
5.  在[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**ReceiveLocations**節點中，選取**[txnrecievelocation1]**接收位置，然後再選取**啟用**。  
  
6.  一旦啟用接收位置，它會自動輪詢資料庫，在指定的時間間隔的資料。  
  
## <a name="classes-or-methods-used-in-the-sample"></a>類別或方法中使用範例  
* IBTTransmitterBatch 介面 (COM)
  
* IBTTransportProxy 介面 (COM)

將描述這些方法[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。 
  
## <a name="see-also"></a>另請參閱  
 [配接器範例-開發](../core/adapter-samples-development.md)   
 [註冊配接器](../core/registering-an-adapter.md)