---
title: "如何將繫結匯入到 BizTalk 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bindings, applications
- applications, importing
- applications, bindings
- bindings, importing
ms.assetid: 89841b23-4e1b-46ff-8f00-cdad65d6216d
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b07e2c7cb5e63ee3e03ac69ad591d7939b22d5d6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-import-bindings-into-a-biztalk-application"></a>如何將繫結匯入到 BizTalk 應用程式
本主題描述如何使用 [BizTalk Server 管理] 主控台或命令列，從 .xml 檔案將繫結匯入到 BizTalk 應用程式。 您也可以匯入繫結至 BizTalk 群組，如中所述[如何匯入到 BizTalk 群組的繫結](../core/how-to-import-bindings-into-a-biztalk-group.md)。  
  
 您可以匯入已經從組件、應用程式或群組匯出的繫結。 如果您要匯入群組繫結，只有同名應用程式的繫結才會套用到匯入繫結的目標應用程式。 您也可以從不同名稱的應用程式匯入繫結。 如需匯出繫結的指示，請參閱[匯出繫結](../core/exporting-bindings6.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="to-import-bindings-into-a-biztalk-application"></a>將繫結匯入到 BizTalk 應用程式  
  
#### <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀結構中，依序展開 [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、BizTalk 群組和 [應用程式]。  
  
3.  以滑鼠右鍵按一下應用的程式想要匯入繫結，並指向**匯入**，然後按一下 **繫結**。  
  
4.  按一下 繫結檔案，然後按一下**開啟**。  
  
     繫結檔案中的成品會寫入此應用程式， 這些成品會顯示在應用程式的適當資料夾中。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別`cmd`，然後按一下 **確定**。  
  
2.  輸入下列命令，並以適當的值替代，如下表所述：  
  
     **BTSTask ImportBindings /Source:** *值*[**/ApplicationName:***值*] [**/Server:** *值*] [**/database:***值*]  
  
     例如，下列命令會將繫結匯入到預設 BizTalk 群組中名為 MyApplication 的應用程式。  
  
     **BTSTask ImportBindings /applicationname: myapplication** /**Source:C:\Bindings\Binding1.xml**  
  
    |參數|值|  
    |---------------|-----------|  
    |**/ 來源**|要匯入的繫結檔案完整路徑 (包含檔案名稱)。 路徑如果包含空格，必須括在引號 (") 中。|  
    |**/ 應用程式名稱**|要匯入繫結的 BizTalk 應用程式名稱。 應用程式必須存在，否則匯入作業將會失敗。 如果沒有指定這個參數，將會使用預設的 BizTalk 應用程式。 應用程式名稱如果包含空格，必須括在引號 (") 中。|  
    |**/ 伺服器**|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
    |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="see-also"></a>另請參閱  
 [匯入 BizTalk 應用程式、 繫結和原則](../core/importing-biztalk-applications-bindings-and-policies.md)   
 [ImportBindings 命令](../core/importbindings-command.md)