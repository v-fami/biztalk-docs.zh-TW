---
title: 排程 SQL Server Integration Services 封裝 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 037ae2cf-c352-4823-95df-9a723f2b5a81
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 17d8518a8c74f1fef77cf713852f1dfc87c8ef23
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25975948"
---
# <a name="scheduling-sql-server-integration-services-packages"></a>排程 SQL Server Integration Services 封裝
使用者可以根據儲存於線上分析處理 (OLAP) Cube 中的資料建立 BAM 檢視。 Cube 更新 Integration Services 封裝會重新整理 Cube 中的資料，如此一來，OLAP 檢視就會反映正確的資料。  
  
 您至少必須執行一次這個封裝，OLAP 檢視才能運作。 為便於持續維護，您應該排程定期執行封裝。  
  
> [!IMPORTANT]
>  如果您在執行 Cube 更新 Integration Services 封裝之前，還原了 BAM 星狀結構描述資料庫或停止了 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，則必須先重新整理 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 分析管理員中的資料來源或重新啟動 OLAP 服務，然後才能順利執行此封裝。  
  
 您可以排程儲存的封裝，使其在特定時間執行，或每隔一段時間重複執行。 例如：  
  
-   每天午夜。  
  
-   每週日 06:00。  
  
-   每月第一天或最後一天。  
  
 已排程的封裝會由 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 當做作業來執行。  
  
 如需有關執行資訊[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]套件，請參閱[http://go.microsoft.com/fwlink/?LinkId=125738](http://go.microsoft.com/fwlink/?LinkId=125738)。  
  
> [!NOTE]
>  根據預設，針對封存和 cube 的 BAM SSIS 封裝的記錄已開啟，而且會儲存在 msdb 資料庫。 加班，這可能會導致大量的 SSIS 大量的 BAM 活動所造成的事件記錄檔資料，或經常執行 BAM 擁有 SSIS 封裝。 若要解決此問題，您可以刪除舊的記錄項目，因為這些項目主要用於偵錯。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以 BizTalk Server 系統管理員群組的成員身分登入，才能執行這些程序。  
  
### <a name="to-run-the-cube-update-integration-services-package"></a>若要執行 Cube 更新 Integration Services 封裝  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008 SP1**或**Microsoft SQL Server 2008 R2**，然後按一下  **SQL Server Management Studio**。  
  
2.  在**連接到伺服器**對話方塊中，於**伺服器類型**下拉式清單中，選取**Integration Services**。  
  
3.  在**伺服器名稱**下拉式清單中，選取 執行封裝的伺服器名稱。  
  
4.  在**驗證**下拉式清單中，選取您用來連接到伺服器的驗證類型。  
  
5.  必要時，請輸入使用者名稱和密碼。  
  
6.  按一下 **[連接]**。  
  
7.  在主控台樹狀目錄中，依序展開**Integration Services**，依序展開**存放的封裝**，然後按一下  **MSDB**。  
  
8.  以滑鼠右鍵按一下**BAM_AN_\<檢視名稱\>** 封裝，然後按一下 **執行封裝**。  
  
### <a name="to-run-the-maintaining-bam-data-integration-services-package"></a>若要執行維護 BAM 資料 Integration Services 封裝  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008 SP1**或**Microsoft SQL Server 2008 R2**，然後按一下  **SQL Server Management Studio**。  
  
2.  在**連接到伺服器**對話方塊中，於**伺服器類型**下拉式清單中，選取**Integration Services**。  
  
3.  在**伺服器名稱**下拉式清單中，選取 執行封裝的伺服器名稱。  
  
4.  在**驗證**下拉式清單中，選取您用來連接到伺服器的驗證類型。  
  
5.  必要時，請輸入使用者名稱和密碼。  
  
6.  按一下 **[連接]**。  
  
7.  在主控台樹狀目錄中，依序展開**Integration Services**，依序展開**存放的封裝**，然後按一下  **MSDB**。  
  
8.  以滑鼠右鍵按一下**BAM_DM_\<活動名稱\>** 封裝，然後按一下 **執行封裝**。  
  
### <a name="to-schedule-the-packages-to-run-regularly"></a>若要將這些封裝排程為定期執行  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008 SP1**或**Microsoft SQL Server 2008 R2**，然後按一下  **SQL Server Management Studio**。  
  
2.  在**連接到伺服器**對話方塊中，於**伺服器類型**下拉式清單中，選取**Database Engine**。  
  
3.  在**伺服器名稱**下拉式清單中，選取 執行封裝的伺服器名稱。  
  
4.  在**驗證**下拉式清單中，選取您用來連接到伺服器的驗證類型。  
  
5.  必要時，請輸入使用者名稱和密碼。  
  
6.  按一下 **[連接]**。  
  
7.  在主控台樹狀目錄中，展開您的伺服器，並選取**SQL Server Agent**。  
  
8.  如果**SQL Server Agent**是停用，以滑鼠右鍵按一下**SQL Server Agent**，然後選取**啟動**。  
  
9. 以滑鼠右鍵按一下**SQL Server Agent**，然後選取**新工作**。  
  
10. 在**新工作**對話方塊中，輸入的名稱中的作業**名稱**文字方塊。  
  
11. 在**選取頁面**視窗中，按一下 **步驟**，然後按一下 **新增**。 這會開啟**新增作業步驟** 對話方塊。  
  
12. 在**步驟名稱**文字方塊中，輸入步驟的識別名稱。  
  
13. 在**類型**下拉式清單中，選取**SQL Server Integration Services 封裝**和**套件來源**下拉式清單中，選取**SSIS 封裝存放區**.  
  
14. 在**伺服器**下拉式清單中，選取執行作業的伺服器。  
  
15. 按一下 檔案選取器按鈕**封裝**文字方塊中，選取要排程的封裝 (任一**BAM_DM_\<活動名稱\>** 或**BAM_AN_\<檢視名稱\>** 封裝)，然後按一下 **確定**。  
  
16. 在**選取頁面**視窗中，按一下 **排程**，然後按一下 **新增**。 這會開啟**新增作業排程** 對話方塊。  
  
17. 在**名稱** 文字方塊中，輸入排程名稱。  
  
18. 使用頻率欄位建立排程。  
  
19. 按一下 **[確定]** 以儲存作業。  
  
    > [!NOTE]
    >  如果 BAM 是使用非預設的 SQL Server 執行個體來設定，則 BAM_AN_POCube DTSPackage 就無法正確地進行排程/執行。 您必須修改組態檔，才能讓封裝繼續執行。 如需詳細資訊，請參閱 < 修改組態檔的內容 」 一節[http://go.microsoft.com/fwlink/?LinkId=196768](http://go.microsoft.com/fwlink/?LinkId=196768)。  
  
## <a name="see-also"></a>請參閱  
 [管理 BAM 資料庫](../core/managing-bam-databases.md)