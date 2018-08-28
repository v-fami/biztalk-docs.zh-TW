---
title: 從使用 BizTalk Server 的 SAP 接收輸入的 tRFC 呼叫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tRFC calls, receiving using BizTalk Server
- tRFCs, sample
ms.assetid: 500eedea-3d27-478c-a64c-903a1fa2b02f
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49d83d8710b36d0900c2d7b3a6b02c7d0a389ba4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978615"
---
# <a name="receive-inbound-trfc-calls-from-sap-using-biztalk-server"></a>從使用 BizTalk Server 的 SAP 接收輸入的 tRFC 呼叫
TRFC 伺服器呼叫是交易式的 RFC 伺服器呼叫。 交易內容中接收 RFC 所需的協調流程是類似於讓協調流程接收其他 SAP 系統所傳來的輸入的 RFC。 不過，您需要執行某些額外的工作，藉此確定 Rfc 接收交易內容中。 如需有關從 SAP 系統使用接收輸入的 RFC [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱 < [SAP 使用 BizTalk Server 從接收輸入的 RFC 呼叫](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-from-sap-using-biztalk-server.md)。 如需有關如何[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援接收輸入的 tRFC 呼叫從 SAP 系統，請參閱[對 sap 的 Trfc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md)。  
  
 接收輸入的 tRFC 從 SAP 系統傳送大致接收輸入的 RFC，但有下列差異：  
  
1. 在設計階段，在產生結構描述，請確定選取 下的一個 tRFC **TRFC**節點。  
  
2. 在執行階段，確定您設定的繫結屬性**TidDatabaseConnectionString**。 此屬性會接受連接字串以連接到 SQL 資料庫來存放 TID。 範例連接字串如下：  
  
   ```  
   Data Source=<myServerAddress>;Initial Catalog=<myDataBase>;User Id=<myUsername>;Password=<myPassword>;  
   ```  
  
    如需有關繫結屬性，以及如何將它設定的詳細資訊，請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
   > [!IMPORTANT]
   >  [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝精靈安裝 SQL 指令碼，SapAdapter-DbScript-Install.sql，必須先執行 SQL Server 系統管理員會將 SQL Server 中建立資料庫和資料庫物件。 指令碼通常會安裝在*\<安裝磁碟機\>: Program Filessystem [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]* 。  
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
  
> [!IMPORTANT]
>  從 「 交易式 」 的內容中的 SAP 系統接收 Idoc 時，會使用輸入的 tRFC 呼叫。  
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)