---
title: 從交易內容，使用 BizTalk Server 中的 SAP 接收 Idoc |Microsoft 文件
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
ms.openlocfilehash: a8903b6010555b3c7c6aba9a07e12c9204bcf19c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25962740"
---
# <a name="receive-idocs-from-sap-in-a-transactional-context-using-biztalk-server"></a>從交易內容，使用 BizTalk Server 中的 SAP 接收 Idoc
交易內容中接收 IDOC 是相似接收 tRFCs 交易內容中。 在這種情況下，從 SAP 系統接收的 IDOC 包含 TID 一部分 *\<TransactionalRfcOperationIdentifier\>* 項目。 此 TID 保存於 SQL 資料庫中的配接器。 如果 ABAP 程式碼會傳送 IDOC 之 SAP 系統中的有 「 認可工作 」 陳述式，TID 會刪除從 SQL database，將回應傳送到 SAP 系統之後。  
  
 無論是否 IDOC 收到交易內容中不相似的需要來接收 IDOC 的協調流程。 請參閱[從 SAP 接收 Idoc，使用 BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-using-biztalk-server.md)。 不過，您需要執行某些其他工作，以確定交易內容中接收 Idoc。  
  
1.  在設計階段產生您想要接收的 IDOC 的結構描述。  
  
2.  在執行階段，確定您設定的繫結屬性**TidDatabaseConnectionString**。 此屬性會接受連接字串以連接到 SQL 資料庫來存放 TID。 範例連接字串應該像這樣：  
  
    ```  
    Data Source=<myServerAddress>;Initial Catalog=<myDataBase>;User Id=<myUsername>;Password=<myPassword>;  
    ```  
  
     如需繫結屬性和設定方式的詳細資訊，請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
    > [!IMPORTANT]
    >  [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝精靈正在安裝的 SQL 指令碼、 SapAdapter-DbScript-Install.sql，必須執行 SQL Server 系統管理員可以在 SQL Server 中建立資料庫和資料庫物件。 指令碼通常會安裝在*\<安裝磁碟機\>*： 程式 FilesMicrosoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。  
    >   
    >  [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]保存 TIDs 會使用這些物件。 因此，SQL Server 系統管理員必須確定使用者名稱提供連接字串的一部分有足夠的權限可以執行預存程序。 提供 Windows 使用者具有足夠的權限的資料庫中執行預存程序，您也可以選擇 Windows 驗證。  
  
3.  請確定安裝配接器的電腦上啟用 MSDTC。 執行下列步驟來啟用 MSDTC。  
  
    1.  啟動 [元件服務] MMC 嵌入式管理單元。  
  
    2.  在 [元件服務] MMC 嵌入式管理單元，從左窗格展開**元件服務**，展開**電腦**，以滑鼠右鍵按一下**我的電腦**，然後按一下**屬性**。  
  
    3.  在**我的電腦內容**對話方塊中，按一下 [ **MSDTC** ] 索引標籤。  
  
    4.  在**交易設定**區段中，按一下**安全性組態** 按鈕。  
  
    5.  在**安全性組態**對話方塊中，選取**網路 DTC 存取**核取方塊，並在內，選取**允許遠端用戶端**核取方塊。  
  
    6.  在**交易管理員通訊**區段中，選取**允許輸入**和**允許輸出**核取方塊。  
  
    7.  在**安全性組態**對話方塊中，按一下 **確定**。  
  
    8.  按一下**是**中對話方塊方塊中，通知將會重新啟動 MSDTC 服務。 重新啟動 MSDTC 服務之後，請按一下**確定**在對話方塊中。  
  
    9. 在**我的電腦內容**對話方塊中，按一下 **確定**。  
  
4.  MSDTC Windows 防火牆例外清單中，如果未新增已新增。 執行下列命令。  
  
    ```  
    netsh firewall set allowedprogram %windir%\system32\msdtc.exe MSDTC enable  
    ```  
  
## <a name="see-also"></a>請參閱  
[開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)