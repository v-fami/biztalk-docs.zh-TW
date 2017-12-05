---
title: "如何復原 BAM 警示 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56c477b4-4605-4763-b20a-3baf4529f13f
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec36491dd7368e0e2fdbcd8fb5abab9d840c6b1e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-recover-bam-alerts"></a>如何復原 BAM 警示
復原過程[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，如果您使用商務活動監控 (BAM)，您就必須一併復原 BAM 警示。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators 群組成員的身分登入，才能執行此程序。  
  
### <a name="to-recover-bam-alerts-sql-server-2008"></a>若要復原 BAM 警示 (SQL Server 2008)  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008**，按一下 **組態工具**，然後按一下  **Notification Services 命令提示字元**。  
  
2.  在命令提示字元中，輸入：  
  
     **nscontrol register-name BamAlerts-server***\<ServerName\>***-服務-serviceusername"**  *\<ServiceUserName\>*  **"-servicepassword"**  *\<ServicePassword\>*  **"**   
  
     如此可讓 Notification Services 登入正確的資料庫 (nscontrol 將這項資訊保存在服務電腦的登錄中)。  
  
    > [!IMPORTANT]
    >  請記得使用新的 Notification Services 資料庫伺服器中**-伺服器**選項重新註冊服務時。 此外，您也應該將新的 Notification Services 服務的使用者名稱，保持與舊服務的使用者名稱一致。  
  
3.  按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。  
  
4.  在命令提示字元中，輸入： **net start NS$ BamAlerts**。  
  
## <a name="see-also"></a>請參閱  
 [復原執行 BizTalk Server 的電腦](../core/recovering-a-computer-running-biztalk-server.md)