---
title: 如何從應用程式和 BizTalk 群組移除原則 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deleting, policies
- managing [policies], applications
- managing [policies], deleting
- groups, policies
- managing [policies], groups
- applications, policies
ms.assetid: e9882cb3-8808-4258-a107-a24905290288
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4bb4b162d90811a4eddaa513556ecb1f6c6cd8d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254510"
---
# <a name="how-to-remove-a-policy-from-an-application-and-the-biztalk-group"></a>如何從應用程式和 BizTalk 群組移除原則
本主題描述如何使用 [BizTalk Server 管理] 主控台或命令列將原則從應用程式以及 BizTalk 群組的「規則引擎」資料庫移除。  
  
 在移除原則之前，請牢記下列要點：  
  
-   您無法移除已部署的原則。 您必須先解除部署原則中所述[如何部署或解除部署原則](../core/how-to-deploy-or-undeploy-a-policy.md)。 解除部署原則會讓它成為非使用中，所以此原則在 BizTalk 群組中使用它的任何應用程式內都不再有任何作用。  
  
-   移除原則會將它從「規則引擎」資料庫中刪除。 如果想要再次使用這個原則，則應該在將它移除之前，先將它匯出至 .xml 檔案。 如需指示，請參閱[如何匯出原則](../core/how-to-export-a-policy.md)。  
  
-   如果有其他的應用程式使用該原則，則在移除之後，該原則在其他的應用程式都將失效。 請在移除原則之前，確認您不想再針對任何其他的應用程式使用該原則。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="to-remove-a-policy"></a>移除原則  
  
#### <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk Server 管理**、 依序展開 BizTalk 群組包含原則移除，和包含原則的應用程式  
  
3.  按一下**原則**，以滑鼠右鍵按一下原則，然後按一下**移除**。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別`cmd`，然後按一下 **確定**。  
  
2.  輸入下列命令，並以適當的值替代，如下表所述：  
  
     **BTSTask RemoveResource** [**/ApplicationName:***值*] **/Luid:***值*[**/Server:***值*] [**/database:***值*]  
  
     範例：  
  
     **BTSTask RemoveResource /applicationname: myapplication /Luid:"Rule/Policy1/1.0"**  
  
    |參數|Description|  
    |---------------|-----------------|  
    |**/ 應用程式名稱**|包含待刪除之原則的 BizTalk 應用程式的名稱。 如果沒有指定這個參數，將會使用預設的應用程式。|  
    |**/ Luid**|原則的本機唯一識別碼 (LUID)。 您可以使用來取得 LUID **ListApp**命令中所述[ListApp 命令](../core/listapp-command.md)。|  
    |**/ 伺服器**|裝載 BizTalk 管理資料庫的 SQL Server 執行個體名稱。 如果您指定 Database 參數，則為必要項。 如果未指定 Server 及 Database 參數，將會使用群組的預設 BizTalk 管理資料庫。|  
    |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果您指定 Server 參數，則為必要項。 如果未指定 Server 及 Database 參數，將會使用群組的預設 BizTalk 管理資料庫。|  
  
## <a name="see-also"></a>另請參閱  
 [管理原則](../core/managing-policies.md)