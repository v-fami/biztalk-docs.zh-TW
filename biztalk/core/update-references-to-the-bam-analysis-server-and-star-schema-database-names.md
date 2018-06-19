---
title: 如何更新 BAM Analysis Server 和星狀結構描述資料庫名稱參考 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- restoring [BAM], Analysis database
- Analysis database [BAM], restoring
- restoring, BAM
- restoring [BAM], updating references
- BAM, restoring
- Analysis database [BAM], updating references
ms.assetid: cbe5e500-0a25-427e-bc76-1eae24b3e5f3
caps.latest.revision: 29
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b4f98129efd2f7c027ecb6c3e69d494ff2e96e8b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287446"
---
# <a name="how-to-update-references-to-the-bam-analysis-server-and-star-schema-database-names"></a>如何更新 BAM Analysis Server 和星狀結構描述資料庫名稱的參考
如果您備份 BAMAnalysis 和 BAMStarSchema 資料庫，發生系統或資料失敗時可以將該備份還原至不同的電腦，您可以重新命名此備份。  
  
 若要還原 BAM Analysis Server 或 BAMStarSchema 資料庫，執行中的步驟[如何還原您的資料庫](../core/how-to-restore-your-databases.md)。 此外，您必須以新的伺服器名稱和資料庫名稱來更新 BAM Data Transformation Services (DTS) 封裝。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators 群組成員的身分登入，才能執行此程序。  
  
### <a name="to-update-references-to-the-bam-analysis-server-and-bam-star-schema-database-name-sql-server-2008-r2sp1"></a>若要更新 BAM Analysis Server 和 BAM 星狀結構描述資料庫名稱 (SQL Server 2008 R2/SP1) 的參考  
  
1.  停止任何 BAM cube 更新及資料維護 SSIS 封裝，或防止它們執行，直到您還原 BAMAnalysis 或 BAMStarSchema 資料庫。  
  
2.  停止 BizTalk 應用程式服務 （其中包含 BAM 事件匯流排服務） 讓它不會嘗試將資料庫詳細資料匯入。  
  
    1.  按一下**啟動**，按一下 **執行**，然後輸入**services.msc**。  
  
    2.  以滑鼠右鍵按一下**BizTalk Service BizTalk Group: BizTalkServerApplication**服務，然後按一下**停止**。  
  
    > [!TIP]
    >  若要停止服務的另一種方式是使用**Net Stop**命令。 若要停止使用 Net Stop 的 BizTalk 服務，請開啟**命令提示字元**(如果使用 Windows Server 2008 或 Windows Vista，啟動 命令提示字元使用**系統管理員身分執行**) 並輸入下列命令： `Net Stop BTSSvc$BizTalkServerApplication`然後按下**Enter**。  
  
3.  按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008 R2**，然後按一下  **SQL Server Business Intelligence Development Studio**.  
  
4.  在 SQL Server Business Intelligence Development Studio 中建立新專案。 按一下**檔案**，按一下 **新增**，然後按一下 **專案**。  
  
5.  中**新專案**對話方塊中，於**範本**，按一下**Integration Services 專案**，然後按一下**確定**。  
  
6.  在**Integration Services 專案**對話方塊中，於**方案總管] 中**，以滑鼠右鍵按一下**SSIS 封裝**，然後按一下 [**加入現有封裝**.  
  
7.  在**加入現有封裝的副本**對話方塊中，於**伺服器**下拉式清單方塊中，選取包含 BAM_AN 封裝的伺服器。  
  
8.  在**封裝路徑**，按一下省略符號按鈕。  
  
9. 中**SSIS 封裝**對話方塊方塊中，選取 BAM_AN 封裝，按一下**確定**，然後按一下  **確定**。  
  
     封裝現在會在 [方案總管] 中列出。  
  
10. 在**方案總管 中**，按兩下 BAM_AN 封裝。 在**連接管理員**，請按兩下資料庫數字 3 （MSDB 資料庫）。  
  
11. 在**連線管理員**對話方塊中，於**伺服器名稱**方塊中，輸入 MSDB 伺服器的名稱，然後按一下**確定**。  
  
12. 按一下**封裝總管**索引標籤上，按兩下**變數**資料夾，然後再更新主要匯入伺服器名稱及主要的值匯入資料庫名稱。  
  
13. 按一下**檔案**，然後按一下 **全部儲存**。  
  
14. 在**Microsoft SQL Server Management Studio**，按一下 **連接**。  
  
15. 按一下**Integration Services**，連按兩下**存放的封裝**，按一下  **MSDB**BAM_AN 封裝，以滑鼠右鍵按一下，然後按**匯入封裝**.  
  
16. 在**匯入封裝**對話方塊中，於**封裝位置**，選取**檔案系統**。  
  
17. 在**封裝路徑**、 瀏覽至您儲存的專案中，選取 BAM_AN\*.dtsx 檔案，然後按一下**開啟**。  
  
18. 在按一下**封裝名稱**方塊，以自動填入方塊。  
  
19. 按一下**確定**，然後按一下 **是**覆寫。  
  
20. 重新啟動 BizTalk 應用程式服務。  
  
    1.  按一下**啟動**，按一下 **執行**，然後輸入**services.msc**。  
  
    2.  以滑鼠右鍵按一下**BizTalk Service BizTalk Group: BizTalkServerApplication**服務，然後按一下**啟動**。  
  
21. 啟用任何 BAM Cube 更新和資料維護 SSIS 封裝。  
  
## <a name="see-also"></a>另請參閱  
 [備份和還原 BAM](../core/backing-up-and-restoring-bam.md)