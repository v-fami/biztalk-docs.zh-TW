---
title: 如何從應用程式移除前置或後置處理指令碼 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [scripts], deleting
- deleting, scripts
- managing [applications], scripts
- scripts, deleting
- applications, scripts
ms.assetid: 7911f098-97f2-4a5d-87fe-20b55231113e
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c9742b6c523f193a8670c1171f38949ef5dd1cc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010007"
---
# <a name="how-to-remove-a-pre--or-post-processing-script-from-an-application"></a>如何從應用程式移除前置或後置處理指令碼
本主題說明如何使用 BizTalk Server 管理主控台或命令列，將前置或後置處理指令碼從應用程式移除。 這會從 BizTalk 管理資料庫移除指令碼，所以它不會匯出到應用程式 .msi 檔案中。 如果在本機檔案系統中有此指令碼，則不會移除它。  
  
 如果包含指令碼的應用程式已安裝在本機檔案系統，而且指令碼是設計為解除安裝期間執行，您必須從檔案系統移除此指令碼，以避免在解除安裝應用程式時執行它。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="to-remove-a-script-from-an-application"></a>若要從應用程式移除指令碼  
  
#### <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開 BizTalk 群組包含指令碼中移除，然後再展開 包含的指令碼的應用程式。  
  
3. 按一下 **資源**資料夾中，以滑鼠右鍵按一下指令碼，然後**移除**。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1. 開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別`cmd`，然後按一下 **確定**。  
  
2. 輸入下列命令，並以適當的值替代，如下表所述：  
  
    **BTSTask RemoveResource** [**/ApplicationName:**<em>值</em>] **/Luid:**<em>值</em>[**/Server:** <em>值</em>] [**/database:**<em>值</em>]  
  
    範例  
  
    **BTSTask RemoveResource /applicationname: myapplication /Luid:"MyApplication:MyScript.vbs"**  
  
   |參數|描述|  
   |---------------|-----------------|  
   |**/ 應用程式名稱**|含有所要刪除之 BizTalk 指令碼的 BizTalk 應用程式的名稱。 如果名稱包含空格，必須以雙引號 (") 將其括住。 如果沒有指定這個參數，將會使用預設的應用程式。|  
   |**/ Luid**|指令碼的本機唯一識別碼 (LUID)。 您可以使用來取得 LUID [ListApp 命令](../core/listapp-command.md)。|  
   |**/ 伺服器**|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
   |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="see-also"></a>另請參閱  
 [管理前置和後置處理指令碼](../core/managing-pre-and-post-processing-scripts.md)   
 [RemoveResource 命令](../core/removeresource-command.md)