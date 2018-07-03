---
title: 從交易內容，使用 BizTalk Server 中的 SAP 接收 Idoc |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transactional context
- IDOCs, receiving in a transactional context using BizTalk Server
ms.assetid: 6a01bb82-7292-4b70-8ad7-996d389a9365
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c58bccbb48603af8bf5a5cc0d12b4c2200e78704
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013361"
---
# <a name="receive-idocs-from-sap-in-a-transactional-context-using-biztalk-server"></a>從交易內容，使用 BizTalk Server 中的 SAP 接收 Idoc
交易內容中接收 IDOC 是相似接收 Trfc 交易內容中。 在此情況下，從 SAP 系統接收 IDOC，請包含做為一部分的 TID *\<TransactionalRfcOperationIdentifier\>* 項目。 此 TID 會保存在 SQL database 中，配接器。 如果 ABAP 程式碼，傳送 IDOC 之 SAP 系統中的有 「 認可工作 」 陳述式，TID 會刪除從 SQL database 中，將回應傳送到 SAP 系統之後。  
  
 無論是否 IDOC 收到交易內容中不需要接收 IDOC 的協調流程大致。 請參閱[藉由使用 BizTalk Server 從 SAP 接收 Idoc](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-using-biztalk-server.md)。 不過，您需要執行某些額外的工作，藉此確定交易內容中接收的 Idoc。  
  
1. 在設計階段，產生您想要接收的 IDOC 的結構描述。  
  
2. 在執行階段，確定您設定的繫結屬性**TidDatabaseConnectionString**。 此屬性會接受連接字串以連接到 SQL 資料庫來存放 TID。 範例連接字串如下：  
  
   ```  
   Data Source=<myServerAddress>;Initial Catalog=<myDataBase>;User Id=<myUsername>;Password=<myPassword>;  
   ```  
  
    如需有關繫結屬性，以及如何將它設定的詳細資訊，請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
   > [!IMPORTANT]
   >  [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝精靈安裝 SQL 指令碼，SapAdapter-DbScript-Install.sql，必須先執行 SQL Server 系統管理員會將 SQL Server 中建立資料庫和資料庫物件。 指令碼通常會安裝在*\<安裝磁碟機\>*: Program Filessystem [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。  
   > 
   >  [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]保存 TIDs 會使用這些物件。 因此，SQL Server 系統管理員必須確定使用者名稱提供的連接字串的組件具有足夠的權限來執行預存程序。 提供 Windows 使用者具有足夠的權限，在資料庫中執行預存程序，您也可以選擇 Windows 驗證。  
  
3. 請確定安裝配接器的電腦上啟用 MSDTC。 執行下列步驟來啟用 MSDTC。  
  
   1.  啟動 [元件服務] MMC 嵌入式管理單元。  
  
   2.  在 [元件服務] MMC 嵌入式管理單元，從左窗格中展開**元件服務**，展開**電腦**，以滑鼠右鍵按一下**我的電腦**，然後按一下**屬性**。  
  
   3.  在 **我的電腦內容** 對話方塊中，按一下**MSDTC**  索引標籤。  
  
   4.  在 [**交易設定**區段中，按一下**安全性設定**] 按鈕。  
  
   5.  在 **安全性設定**對話方塊中，選取**網路 DTC 存取**核取方塊，然後在其中選取**允許遠端用戶端**核取方塊。  
  
   6.  在 **交易管理員通訊**區段中，選取**允許輸入**並**允許輸出**核取方塊。  
  
   7.  在 [**安全性設定**] 對話方塊中，按一下**確定**。  
  
   8.  按一下 **是**中對話方塊方塊中，通知將會重新啟動 MSDTC 服務。 重新啟動 MSDTC 服務之後，請按一下**確定**在對話方塊中。  
  
   9. 在 [**我的電腦內容**] 對話方塊中，按一下**確定**。  
  
4. 將 MSDTC 新增至 Windows 防火牆例外清單中，如果沒有已經新增。 執行下列命令。  
  
   ```  
   netsh firewall set allowedprogram %windir%\system32\msdtc.exe MSDTC enable  
   ```  
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)