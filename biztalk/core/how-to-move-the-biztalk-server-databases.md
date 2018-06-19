---
title: 移動 BizTalk Server 資料庫 |Microsoft 文件
description: 將 BizTalk Server 資料庫移至新的伺服器，包括停止服務，以及使用 SQL Server Agent 作業步驟
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec302e6d-c89d-4fe7-849f-97b5566e8ba4
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12bd1d6bc8a46d4e63dc69166d87f3678a0e3272
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254174"
---
# <a name="how-to-move-the-biztalk-server-databases"></a>如何移動 BizTalk Server 資料庫

## <a name="overview"></a>概觀
您可以使用此程序來移動主要[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]另一部伺服器的資料庫。 這個相同的基本程序也可用來移動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫從本機[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]至遠端[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]或[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集。  

## <a name="prerequisites"></a>必要條件  
使用成員的帳戶登入[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]sysadmin 固定的伺服器角色，才能執行此程序。  
  
## <a name="move-steps"></a>移動步驟
  
1.  停止所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務。 如需詳細資訊，請參閱[重新啟動 BizTalk Server 服務，並關閉的 BizTalk Server](how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md)。
  
    > [!IMPORTANT]
    >  請務必確定所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在移動資料庫之前停止服務和工作。  
  
2.  停止 IIS 服務。  
  
3.  停止 SQL Server Agent 服務。  
  
4.  備份下列資料庫備份程序，如下所述 BizTalk 資料庫[Backing Up and Restoring BizTalk Server 資料庫](../core/backing-up-and-restoring-the-biztalk-server-databases.md)。  
  
5.  下列資料庫的新伺服器上的 BizTalk 資料庫還原程序，在還原[如何還原您的資料庫](../core/how-to-restore-your-databases.md)。  
  
6.  SQL Server Agent 作業下列要傳輸到新的伺服器，如下所述的指令碼[如何備份和還原 SQL 代理程式作業](../core/how-to-back-up-and-restore-sql-agent-jobs.md)。  執行每個指令碼來重新建立作業新的伺服器上。  
  
     執行每個指令碼來重新建立作業新的伺服器上。 某些作業，例如**備份 BizTalk Server (BizTalkMsgBoxDb)** 作業，必須重新設定，除非新的伺服器檔案路徑和伺服器名稱會與舊伺服器相同。  
  
    > [!NOTE]
    >  您也可以使用 SSIS/DTS**傳送作業**工作作業移至新的伺服器，但大部分的使用者可能會發現它更輕鬆地編寫指令碼工作使用 SQL Management Studio。  
  
7.  除了上一個步驟中所述，指令碼處理 SQL Server Agent 作業，您必須也撰寫指令碼登入中所述[如何備份和還原 SQL Server 登入](../core/how-to-back-up-and-restore-sql-server-logins.md)。 必須先在目的地伺服器上還原這些登入。  
  
8.  還原[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，依照下列步驟 9 中 22 到[如何還原您的資料庫](../core/how-to-restore-your-databases.md)。 此程序會更新 BizTalk 管理 (BizTalkMgmtDb) 資料庫和登錄 BizTalk 資料庫的新位置。  
  
    > [!NOTE]
    >  在**SampleUpdateInfo.xml**檔案，您已移到新伺服器的註解的所有資料庫除外。  
  
## <a name="see-also"></a>另請參閱  
 [移動 BizTalk Server 資料庫](../core/moving-biztalk-server-databases.md)