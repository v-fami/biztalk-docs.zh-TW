---
title: 如何從應用程式移除 BizTalk 組件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [applications], assemblies
- assemblies, deleting
- deleting, assemblies
- applications, assemblies
- managing [assemblies], deleting
ms.assetid: 0691c3b6-476d-4e01-b50b-47d7c0b299bf
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 89e46b8610114149e8618811361090d8644f82aa
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26008455"
---
# <a name="how-to-remove-a-biztalk-assembly-from-an-application"></a>如何從應用程式移除 BizTalk 組件
本主題描述如何使用 BizTalk Server 管理主控台或命令列，從 BizTalk 應用程式移除 BizTalk 組件。 當您這麼做時，將會從應用程式及 BizTalk 管理資料庫移除組件及其包含的成品 (例如，協調流程、結構描述和管線)。  
  
 在移除 BizTalk 組件時，請牢記下列要點：  
  
-   移除 BizTalk 組件時，不會自動移除位於全域組件快取 (GAC) 或本機檔案系統中的組件檔案。 您必須手動移除它。 如需指示，請參閱[如何從 GAC 解除安裝組件](http://msdn.microsoft.com/library/464706a8-f902-4d05-a724-19169facd2b4)和[如何移除其他檔案和設定 BizTalk 應用程式](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md)。  
  
-   如果您移除包含管線的 BizTalk 組件，則在同一應用程式中，任何使用該管線的傳送埠都會重設為使用預設的 PassThruTransmit 管線。  
  
-   您無法移除有其他成品相依於其上的 BizTalk 組件。 您必須先移除相依的成品， 然後才能移除該 BizTalk 組件。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="to-remove-a-biztalk-assembly-from-an-application"></a>從應用程式移除 BizTalk 組件  
  
#### <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，展開 [BizTalk Server 管理]，展開包含要移除的 BizTalk 組件的 BizTalk 群組，然後展開包含 BizTalk 組件的應用程式。  
  
3.  按一下**資源**資料夾中，以滑鼠右鍵按一下 BizTalk 組件，然後按一下**移除**。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別`cmd`，然後按一下 **確定**。  
  
2.  輸入下列命令，並以適當的值替代，如下表所述：  
  
     **BTSTask RemoveResource** [**/ApplicationName:***值*] **/Luid:***值*[**/Server:***值*] [**/database:***值*]  
  
     範例：  
  
     **BTSTask RemoveResource /applicationname: myapplication /Luid:"MyApp.Orchestrations，版本 = 1.0.0.0，Culture = neutral，PublicKeyToken = 0123456789ABCDEF"**  
  
    |參數|Description|  
    |---------------|-----------------|  
    |**/ 應用程式名稱**|包含待刪除之 BizTalk 組件的 BizTalk 應用程式的名稱。 如果沒有指定這個參數，將會使用預設的應用程式。 如果名稱包含空格，您必須將它括在雙引號 (") 中。|  
    |**/ Luid**|BizTalk 組件的本機唯一識別碼 (LUID)。 您可以使用來取得 LUID **ListApp**命令中所述[ListApp 命令](../core/listapp-command.md)。|  
    |**/ 伺服器**|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
    |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="see-also"></a>請參閱  
 [管理 BizTalk 組件](../core/managing-biztalk-assemblies.md)   
 [RemoveResource 命令](../core/removeresource-command.md)