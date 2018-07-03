---
title: 如何從應用程式移除協調流程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- applications, orchestrations
- deleting, orchestrations
- managing [orchestrations], deleting
- orchestrations, applications
- orchestrations, deleting
ms.assetid: e6d635ea-3513-42de-a667-b56c536e5328
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f6e024ec32a8b84cc1d883a2a9382e6aa06109b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998183"
---
# <a name="how-to-remove-an-orchestration-from-an-application"></a>如何從應用程式移除協調流程
本主題描述如何使用 BizTalk Server 管理主控台或命令列，從 BizTalk 應用程式移除協調流程。 從應用程式移除協調流程也會將它從 BizTalk 群組的 BizTalk 管理資料庫中刪除。  
  
 移除協調流程時，會發生下列情況：  
  
- 協調流程會從 BizTalk 管理資料庫中刪除。  
  
- 包含協調流程的 BizTalk 組件會從 BizTalk 管理資料庫中刪除，但是不會從本機檔案系統或全域組件快取 (GAC) 中移除 (如果存在於這些位置)。  
  
- 由於會刪除 BizTalk 組件，所以包含在組件中的所有成品也會從 BizTalk 管理資料庫中刪除。  
  
  從應用程式移除協調流程前，請牢住下列要點：  
  
- 如果其他成品對此協調流程或對包含在也將移除之組件中的成品有相依性，則當您移除協調流程時，這些成品將再也無法正確運作。 如需相依性的背景資訊，請參閱[相依性和應用程式部署](../core/dependencies-and-application-deployment.md)。  
  
- 您不可以移除具有執行中執行個體的協調流程。 您必須終止任何在執行中的執行個體。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="to-remove-an-orchestration-from-an-application"></a>從應用程式移除協調流程  
  
#### <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開 BizTalk 群組，展開**應用程式**，然後展開包含您想要移除的協調流程應用程式。  
  
3. 按一下 **協調流程**，以滑鼠右鍵按一下協調流程，然後按一下**取消登錄**。  
  
4. 選取協調流程，指向**檢視**，然後按一下**執行個體資訊**。  
  
5. 在查詢結果 窗格中，以滑鼠右鍵按一下協調流程執行個體，然後**Terminate**。  
  
   > [!NOTE]
   >  您可以取消登錄、 終止執行中的執行個體，並停止所有的應用程式中的協調流程一次使用完全停止 選項，則應用程式中所述[如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)。  
  
6. 按一下 **協調流程**，以滑鼠右鍵按一下協調流程，然後按一下**移除**。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1. 開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別`cmd`，然後按一下 **確定**。  
  
2. 輸入下列命令，並以適當的值替代，如下表所述：  
  
    **BTSTask RemoveResource** [**/ApplicationName:**<em>值</em>] **/Luid:**<em>值</em>[**/Server:** <em>值</em>] [**/database:**<em>值</em>]  
  
    範例  
  
    **BTSTask RemoveResource /applicationname: myapplication /Luid:"MyApp.Orchestrations，版本 = 1.0.0.0、 文化特性 = 中性，PublicKeyToken = 0123456789ABCDEF"**  
  
   |參數|描述|  
   |---------------|-----------------|  
   |**/ 應用程式名稱**|包含待刪除之協調流程的 BizTalk 應用程式的名稱。 如果名稱包含空格，您必須將它括在雙引號 (") 中。 如果沒有指定這個參數，將會使用預設的應用程式。|  
   |**/ Luid**|協調流程的本機唯一識別碼 (LUID)。 您可以使用來取得 LUID [ListApp 命令](../core/listapp-command.md)。|  
   |**/ 伺服器**|裝載 BizTalk 管理資料庫的 SQL Server 執行個體名稱。 如果您指定 Database 參數，則為必要項。 如果未指定 Server 及 Database 參數，將會使用群組的預設 BizTalk 管理資料庫。|  
   |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果您指定 Server 參數，則為必要項。 如果未指定 Server 及 Database 參數，將會使用群組的預設 BizTalk 管理資料庫。|  
  
## <a name="see-also"></a>另請參閱  
 [管理協調流程](../core/managing-orchestrations.md)   
 [RemoveResource 命令](../core/removeresource-command.md)