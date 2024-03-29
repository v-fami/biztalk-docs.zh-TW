---
title: 如何匯出 BizTalk 群組的繫結 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- bindings, exporting
- groups, bindings
- groups, exporting
ms.assetid: 51955266-f87f-41c9-992c-93036b40f663
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3fc33f0ea4783ba5d2065816103502ee75dae6d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997199"
---
# <a name="how-to-export-bindings-for-a-biztalk-group"></a>如何匯出 BizTalk 群組的繫結
本主題描述如何使用 [BizTalk Server 管理主控台] 或命令列，將 BizTalk 群組的繫結匯出到 .xml 檔案。 您可以接著這些繫結匯入到 BizTalk 群組或應用程式中所述[如何匯入到 BizTalk 群組的繫結](../core/how-to-import-bindings-into-a-biztalk-group.md)並[如何匯入至 BizTalk 應用程式的繫結](../core/how-to-import-bindings-into-a-biztalk-application.md)。 如需使用繫結檔案的詳細資訊，請參閱[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。  
  
> [!NOTE]
>  無論是否有指定這個選項，匯出群組的繫結必定都會匯出全域合作對象資訊。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行本主題中的程序，您必須使用「BizTalk Server 系統管理員」群組或「BizTalk 操作員」群組的成員帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="to-export-bindings-for-a-biztalk-group"></a>若要匯出 BizTalk 群組的繫結  
  
#### <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、 BizTalk 群組、 以滑鼠右鍵按一下**應用程式**，指向**匯出**，然後按一下**繫結**。  
  
3. 在 [匯出繫結] 頁面中**匯出至檔案**，輸入要用來匯出繫結的.xml 檔案的絕對路徑。  
  
    範例： C:\Bindings\Group1Bindings_Staging1.xml  
  
4. 請確認**從目前的群組匯出所有繫結**已選取，然後按一下**確定**。  
  
    繫結就會匯出到您所指定位置中的 .xml 檔案。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1. 開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別`cmd`，然後按一下 **確定**。  
  
2. 輸入下列命令，並以適當的值替代，如下表所述：  
  
    **BTSTask ExportBindings /Destination:** *值* **/GroupLevel** [**/GlobalParties**] [**/Server:** <em>值</em>] [**/database:**<em>值</em>]  
  
    範例  
  
    **/Destination BTSTask ExportBindings:"C:\Binding Files\MyBindings.xml"GroupLevel /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
   |參數|ReplTest1|  
   |---------------|-----------|  
   |**/ 目的地**|要建立的繫結檔案完整路徑 (包含檔案名稱)。 如果具有相同路徑的繫結檔案已存在，將會覆寫檔案。 如果路徑中有空格，您必須將它括在雙引號 (") 中。|  
   |**/ GroupLevel**|如果有指定，將匯出目前 BizTalk 群組中的所有繫結。|  
   |**/ GlobalParties**|如果有指定，將匯出群組的全域合作對象資訊。|  
   |**/ 伺服器**|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
   |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="see-also"></a>另請參閱  
 [匯出繫結](../core/exporting-bindings6.md)   
 [ExportBindings 命令](../core/exportbindings-command.md)   
 [匯入 BizTalk 應用程式、繫結和原則](../core/importing-biztalk-applications-bindings-and-policies.md)