---
title: "如何從 BizTalk 群組刪除 BizTalk 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- undeploying, applications
- applications, deleting
- applications, groups
- undeploying, deleting
- managing [applications], deleting
- deleting, applications
- applications, undeploying
- managing [applications], groups
- groups, applications
ms.assetid: 968a6436-ae1a-4f85-bb44-e704826a0197
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 269ef99a3244d0aba55d9dad856c0262d0d14ba0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-delete-a-biztalk-application-from-the-biztalk-group"></a>如何從 BizTalk 群組刪除 BizTalk 應用程式
您可以從 BizTalk 群組刪除應用程式， 這樣會從此群組的 BizTalk 資料庫中移除它的所有資料，而此應用程式將不再顯示於 BizTalk Server 管理主控台中； 但是，這並不會解除安裝應用程式。  
  
 在您刪除應用程式之前，請牢記下列要點：  
  
-   您必須先停止應用程式，才能將它刪除。 中所述，您應該停止應用程式，使用完全停止 選項[如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)。  
  
-   只有當沒有其他應用程式包含此應用程式的參考時，您才可以刪除此應用程式。 如果其他應用程式含有對此即將移除之應用程式的參考，您必須先從其他應用程式移除這些參考。 如需指示，請參閱[如何移除另一個應用程式的參考](../core/how-to-remove-a-reference-to-another-application.md)。  
  
-   如果應用程式含有傳送埠群組，而另一個應用程式中的傳送埠是該群組的成員時，您無法刪除此應用程式。 您必須取消登錄該成員傳送埠，然後才能刪除應用程式。 如需指示，請參閱[如何取消登錄傳送埠或傳送埠群組](../core/how-to-unenlist-a-send-port-or-send-port-group.md)。  
  
-   如果應用程式含有某合作對象所參考的傳送埠，您將無法刪除此應用程式。 您可以刪除該合作對象所做的參考、刪除此傳送埠，或將傳送埠移至其他應用程式。 如需執行這些工作的指示，請參閱[如何檢視或編輯合作對象](http://msdn.microsoft.com/library/42e6f3a0-8f7d-4f6c-ab05-a1fab7bf46ca)，[如何刪除傳送埠](../core/how-to-delete-a-send-port.md)，或[如何將成品移至不同的應用程式](../core/how-to-move-an-artifact-to-a-different-application.md)。  
  
-   您無法刪除預設應用程式。 如果您要將其刪除，必須先指定其他應用程式做為預設應用程式。 如需指示，請參閱[如何變更預設的應用程式](../core/how-to-change-the-default-application.md)。  
  
-   如果應用程式中有協調流程具有擱置的執行個體，您將無法刪除此應用程式。  
  
-   若要完全解除部署 BizTalk 應用程式，您還必須考慮中所述的步驟[如何解除安裝 BizTalk 應用程式](../core/how-to-uninstall-a-biztalk-application.md)，而且您也可能需要移除其他檔案和設定 中所述[如何移除其他檔案和設定 BizTalk 應用程式](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="to-delete-a-biztalk-application"></a>刪除 BizTalk 應用程式  
  
#### <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，依序展開 [BizTalk 群組] 並展開**應用程式**。  
  
3.  以滑鼠右鍵按一下 [應用程式] 資料夾，然後按一下**刪除**。  
  
4.  按一下**是**確認刪除。  
  
     BizTalk Server 會從 BizTalk 資料庫刪除所有的應用程式資料，並從管理主控台移除此應用程式。  
  
     如果 BizTalk Server 無法刪除任何應用程式成品，刪除作業會失敗。 在此情況下，BizTalk Server 會嘗試回復刪除作業。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別`cmd`，然後按一下 **確定**。  
  
2.  輸入下列命令，並以適當的值替代，如下表所述：  
  
     **BTSTask RemoveApp /ApplicationName:** *值*[**/Server:***值*] [**/database:** *值*]  
  
     範例：  
  
     **BTSTask RemoveApp /applicationname: myapplication**  
  
    |參數|值|  
    |---------------|-----------|  
    |**/ 應用程式名稱**|要刪除的 BizTalk 應用程式的名稱。 如果名稱包含空格，您必須將它括在雙引號 (") 中。|  
    |**/ 伺服器**|裝載 BizTalk 管理資料庫的 SQL Server 執行個體名稱。 如果您指定 Database 參數，則為必要項。 如果未指定 Server 及 Database 參數，將會使用群組的預設 BizTalk 管理資料庫。|  
    |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果您指定 Server 參數，則為必要項。 如果未指定 Server 及 Database 參數，將會使用群組的預設 BizTalk 管理資料庫。|  
  
## <a name="see-also"></a>另請參閱  
 [解除部署 BizTalk 應用程式](../core/undeploying-biztalk-applications.md)   
 [部署 BizTalk 應用程式](../core/deploying-biztalk-applications.md)