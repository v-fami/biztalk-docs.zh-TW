---
title: 如何從測試環境中的 MessageBox 資料庫手動清除資料 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 398991a9-344a-487a-a817-dfc97d48ebe6
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d4a6d5f8b232e31a140ee4786b87d2bb270505f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254054"
---
# <a name="how-to-manually-purge-data-from-the-messagebox-database-in-a-test-environment"></a>如何手動從測試環境中的 MessageBox 資料庫清除資料
在開發或測試環境中執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，儲存在 MessageBox 資料庫中的資料通常不是重要的即時商務資料，因此可被刪除。 在這些實例中，您可能需要應急的方法來清除 MessageBox 資料庫中的資料。 請依照本主題中的程序，使用 bts_CleanupMsgbox 預存程序手動清除 MessageBox 資料庫中的資料。  
  
> [!NOTE]
>  您應該只在測試環境中執行這些步驟。 不支援在實際執行環境中手動清除 BizTalk MessageBox 資料庫。  
  
### <a name="to-stop-biztalk-services"></a>停止 BizTalk 服務  
  
1.  從 [服務] 主控台停止 BizTalk 服務的所有執行個體。  
  
2.  如果外掛式主控件有任何執行中的配接器 (例如 HTTP、SOAP 或 WCF)，請從命令提示字元執行 IISRESET 以重新啟動 IIS。  
  
3.  關閉所有正在執行的自訂外掛式配接器。  
  
### <a name="to-create-and-execute-the-btscleanupmsgbox-stored-procedure-using-sql-server-2008"></a>使用 SQL Server 2008 建立並執行 bts_CleanupMsgbox 預存程序  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008 R2**，然後按一下  **SQL Server Management Studio**。  
  
2.  在**連接到 SQL Server**對話方塊中，選取 SQL server 和適當的驗證方法，，然後按一下**連接**。  
  
3.  在**可用的資料庫**下拉式清單中，選取 BizTalk Messagebox 資料庫 (**BizTalkMsgBoxDB**依預設)。  
  
4.  按一下**新查詢**工具列上的圖示。  
  
5.  開啟**msgbox_cleanup_logic.sql**檔案從 SQL Server Management Studio。 msgbox_cleanup_logic.sql 檔案位於 BizTalk Server 電腦的 [[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Schema\] 目錄中。  
  
6.  按一下**執行查詢**圖示上以執行指令碼，以建立 bts_CleanupMsgbox 預存程序。 就可以在預存程序清單中看到代表 bts_CleanupMsgbox 預存程序的 dbo.bts_CleanupMsgbox。  
  
7.  按一下**新查詢**工具列上的圖示。  
  
8.  將下列命令貼到新的查詢視窗：  
  
    ```  
    exec bts_CleanupMsgbox  
    ```  
  
9. 按一下**執行查詢**圖示上以執行 bts_CleanupMsgbox 預存程序。  
  
    > [!IMPORTANT]
    >  請勿在執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的實際執行伺服器上執行 bts_CleanupMsgbox 預存程序。 您應該只在測試環境中執行 bts_CleanupMsgbox 預存程序。 不支援在實際執行環境中執行 bts_CleanupMsgbox 預存程序。  
  
10. 視需要重新啟動 BizTalk 服務。  
  
## <a name="considerations-when-running-the-btscleanupmsgbox-stored-procedure"></a>執行 bts_CleanupMsgbox 預存程序時的考量  
 執行 bts_CleanupMsgbox 預存程序時有下列考量：  
  
1.  如果您在測試系統上安裝更新 BizTalk 資料庫結構描述的 Hotfix，該 Hotfix 可能會將 bts_CleanupMsgbox 預存程序覆寫成空的版本。 在此情況下，您必須依照本主題中的程序來重新建立 bts_CleanupMsgbox 預存程序。  
  
2.  如果您建立新的 MessageBox 資料庫，bts_CleanupMsgbox 預存程序將是空白的，您必須依照本主題中的程序重新建立 bts_CleanupMsgbox 預存程序。  
  
3.  使用 bts_CleanupMsgbox 預存程序是**不支援**生產系統上。 此預存程序將會刪除 MessageBox 資料庫中的所有資料。  
  
## <a name="see-also"></a>另請參閱  
 [如何從 BizTalk 追蹤資料庫清除資料](../core/how-to-purge-data-from-the-biztalk-tracking-database.md)