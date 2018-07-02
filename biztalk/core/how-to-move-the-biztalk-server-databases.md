---
title: 移動 BizTalk Server 資料庫 |Microsoft Docs
description: 若要將 BizTalk Server 資料庫移至新的伺服器，包括停止服務，以及使用 SQL Server Agent 作業步驟
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
ms.openlocfilehash: 7a3509a6a0297b0f58a16cfd3eff1dc29420232b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978903"
---
# <a name="how-to-move-the-biztalk-server-databases"></a>如何移動 BizTalk Server 資料庫

## <a name="overview"></a>概觀
您可以使用此程序，在主要複本移[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]另一部伺服器的資料庫。 這個相同的基本程序也可用來移動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫從本機[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]至遠端[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]或[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集。  

## <a name="prerequisites"></a>必要條件  
使用成員的帳戶登入[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]sysadmin 固定的伺服器角色，才能執行此程序。  
  
## <a name="move-steps"></a>移動步驟
  
1. 停止所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務。 如需詳細資訊，請參閱 <<c0> [ 重新啟動 BizTalk Server 服務，並關閉的 BizTalk Server](how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md)。
  
   > [!IMPORTANT]
   >  請務必確定所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在移動資料庫之前停止服務和作業。  
  
2. 停止 IIS 服務。  
  
3. 停止 SQL Server Agent 服務。  
  
4. 備份 BizTalk 資料庫遵循的資料庫備份程序，在所述[Backing Up and Restoring BizTalk Server 資料庫](../core/backing-up-and-restoring-the-biztalk-server-databases.md)。  
  
5. 還原資料庫，新伺服器上的 BizTalk 資料庫還原程序[如何還原您的資料庫](../core/how-to-restore-your-databases.md)。  
  
6. SQL Server Agent 作業下列傳輸到新的伺服器，在所述的指令碼[如何備份和還原 SQL 代理程式作業](../core/how-to-back-up-and-restore-sql-agent-jobs.md)。  執行每個指令碼來重新建立作業在新伺服器上。  
  
    執行每個指令碼來重新建立作業在新伺服器上。 某些作業，例如**備份 BizTalk Server (BizTalkMsgBoxDb)** 作業，必須重新設定，除非新的伺服器檔案路徑和伺服器名稱會與舊伺服器相同。  
  
   > [!NOTE]
   >  您也可以使用 SSIS/DTS**傳送作業**工作將作業移至新的伺服器，但大部分的使用者可能會發現它容易編寫指令碼工作使用 SQL Management Studio。  
  
7. 除了上一個步驟中所述，指令碼處理 SQL Server Agent 作業，您必須也編寫指令碼登入中所述[如何備份和還原 SQL Server 登入](../core/how-to-back-up-and-restore-sql-server-logins.md)。 這些登入，就必須在目的地伺服器上進行還原。  
  
8. 還原[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，依照下列步驟 9 至 22 英[還原您的資料庫如何](../core/how-to-restore-your-databases.md)。 此程序更新 BizTalk 資料庫的新位置的 BizTalk 管理資料庫 (BizTalkMgmtDb) 和登錄。  
  
   > [!NOTE]
   >  在  **SampleUpdateInfo.xml**檔案，標記為註解的所有資料庫，除了已移至新的伺服器。  
  
## <a name="see-also"></a>另請參閱  
 [移動 BizTalk Server 資料庫](../core/moving-biztalk-server-databases.md)