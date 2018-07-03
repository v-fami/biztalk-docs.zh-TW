---
title: 如何將繫結匯入到 BizTalk 群組 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- groups, importing
- importing, bindings
- groups, bindings
- bindings, groups
ms.assetid: 38da14fb-3522-4274-a633-2ff24e4bd574
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1bdc3f8c25e50567c9e12df5c61ba28cc225e5a9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000375"
---
# <a name="how-to-import-bindings-into-a-biztalk-group"></a>如何將繫結匯入到 BizTalk 群組
本主題描述如何使用 [BizTalk Server 管理主控台] 或命令列，從 .xml 檔案將繫結匯入到 BizTalk 群組。 如需從 BizTalk 群組匯出繫結，到.xml 檔案，您可以匯入的指示，請參閱 <<c0> [ 如何為 BizTalk 群組匯出的繫結](../core/how-to-export-bindings-for-a-biztalk-group.md)。  
  
 您也可以匯入繫結至 BizTalk 應用程式中所述[如何匯入至 BizTalk 應用程式的繫結](../core/how-to-import-bindings-into-a-biztalk-application.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="to-import-bindings-into-a-biztalk-group"></a>若要將繫結匯入到 BizTalk 群組  
  
#### <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開 BizTalk 群組，然後以滑鼠右鍵按一下**應用程式**。  
  
3. 指向**匯入**，然後按一下**繫結**。  
  
4. 按一下 繫結檔案，然後按一下**開啟**。  
  
    繫結檔案中的成品會寫入此群組。 在適當資料夾中顯示\<所有成品\>節點。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1. 開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別`cmd`，然後按一下 **確定**。  
  
2. 輸入下列命令，並以適當的值替代，如下表所述：  
  
    **BTSTask ImportBindings /Source:** *值* **/GroupLevel** [**/Server:**<em>值</em>] [  **/資料庫:**<em>值</em>]  
  
    例如，下列命令會將繫結匯入到在 BizTalk 管理資料庫中定義的群組，該資料庫則是在名為 MyServer 的 SQL Server 執行個體上執行。  
  
    **BTSTask ImportBindings GroupLevel /Server:MyServer /Database:BiztalkMgmtDb /Source:C:\Bindings\Binding1.xml**  
  
   |參數|ReplTest1|  
   |---------------|-----------|  
   |**/ 來源**|要匯入的繫結檔案完整路徑 (包含檔案名稱)。 路徑如果包含空格，必須括在引號 (") 中。|  
   |**/ GroupLevel**|此選項指定將繫結檔案匯入到目前的群組。|  
   |**/ 伺服器**|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
   |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="see-also"></a>另請參閱  
 [匯入 BizTalk 應用程式、 繫結和原則](../core/importing-biztalk-applications-bindings-and-policies.md)   
 [ImportBindings 命令](../core/importbindings-command.md)