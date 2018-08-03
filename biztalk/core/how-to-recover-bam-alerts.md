---
title: 如何復原 BAM 警示 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 56c477b4-4605-4763-b20a-3baf4529f13f
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec36491dd7368e0e2fdbcd8fb5abab9d840c6b1e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25972540"
---
# <a name="how-to-recover-bam-alerts"></a><span data-ttu-id="d21a6-102">如何復原 BAM 警示</span><span class="sxs-lookup"><span data-stu-id="d21a6-102">How to Recover BAM Alerts</span></span>
<span data-ttu-id="d21a6-103">復原過程[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，如果您使用商務活動監控 (BAM)，您就必須一併復原 BAM 警示。</span><span class="sxs-lookup"><span data-stu-id="d21a6-103">As a part of recovering [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], if you are using Business Activity Monitoring (BAM), you must also recover the BAM alerts.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d21a6-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="d21a6-104">Prerequisites</span></span>  
 <span data-ttu-id="d21a6-105">您必須以 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators 群組成員的身分登入，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="d21a6-105">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group to perform this procedure.</span></span>  
  
### <a name="to-recover-bam-alerts-sql-server-2008"></a><span data-ttu-id="d21a6-106">若要復原 BAM 警示 (SQL Server 2008)</span><span class="sxs-lookup"><span data-stu-id="d21a6-106">To recover BAM alerts (SQL Server 2008)</span></span>  
  
1.  <span data-ttu-id="d21a6-107">按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008**，按一下 **組態工具**，然後按一下  **Notification Services 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="d21a6-107">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008**, click **Configuration Tools**, and then click **Notification Services Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="d21a6-108">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="d21a6-108">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="d21a6-109">**nscontrol register-name BamAlerts-server***\<ServerName\>***-服務-serviceusername"** *\<ServiceUserName\>* **"-servicepassword"** *\<ServicePassword\>* **"** </span><span class="sxs-lookup"><span data-stu-id="d21a6-109">**nscontrol register -name BamAlerts -server**  *\<ServerName\>*  **-service -serviceusername "** *\<ServiceUserName\>* **" -servicepassword "** *\<ServicePassword\>* **"**</span></span>  
  
     <span data-ttu-id="d21a6-110">如此可讓 Notification Services 登入正確的資料庫 (nscontrol 將這項資訊保存在服務電腦的登錄中)。</span><span class="sxs-lookup"><span data-stu-id="d21a6-110">This enables Notification Services to log on to the correct database (this information is maintained in the registry of the service computer by nscontrol).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d21a6-111">請記得使用新的 Notification Services 資料庫伺服器中 **-伺服器**選項重新註冊服務時。</span><span class="sxs-lookup"><span data-stu-id="d21a6-111">Remember to use the new Notification Services databases server in the **-server** option when re-registering the service.</span></span> <span data-ttu-id="d21a6-112">此外，您也應該將新的 Notification Services 服務的使用者名稱，保持與舊服務的使用者名稱一致。</span><span class="sxs-lookup"><span data-stu-id="d21a6-112">In addition, you should use the same user name for the new Notification Services service as the old one.</span></span>  
  
3.  <span data-ttu-id="d21a6-113">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d21a6-113">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="d21a6-114">在命令提示字元中，輸入： **net start NS$ BamAlerts**。</span><span class="sxs-lookup"><span data-stu-id="d21a6-114">At the command prompt, type: **net start NS$BamAlerts**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d21a6-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="d21a6-115">See Also</span></span>  
 [<span data-ttu-id="d21a6-116">復原執行 BizTalk Server 的電腦</span><span class="sxs-lookup"><span data-stu-id="d21a6-116">Recovering a Computer Running BizTalk Server</span></span>](../core/recovering-a-computer-running-biztalk-server.md)