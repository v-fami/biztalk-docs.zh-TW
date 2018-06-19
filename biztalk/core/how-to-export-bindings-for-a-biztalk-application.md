---
title: 如何匯出 BizTalk 應用程式的繫結 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- bindings, exportings
- applications, exporting
- applications, bindings
ms.assetid: 700d2781-480b-42ed-a313-1a67a7406369
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d08b97146fd327619a97e304a4167c9b62871c8b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255078"
---
# <a name="how-to-export-bindings-for-a-biztalk-application"></a>如何匯出 BizTalk 應用程式的繫結
本主題說明如何使用 BizTalk Server 管理主控台或命令列，將 BizTalk 應用程式的繫結匯出到 .xml 檔案。 接著，您可以將繫結檔案匯入到另一個應用程式，以匯入的同名繫結覆寫應用程式中目前的繫結。 如需詳細資訊，請參閱[如何匯入到 BizTalk 應用程式的繫結](../core/how-to-import-bindings-into-a-biztalk-application.md)。 如需有關如何使用繫結檔案的詳細資訊，請參閱[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組或「BizTalk Server 操作員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="to-export-bindings-for-a-biztalk-application"></a>若要匯出 BizTalk 應用程式的繫結  
  
#### <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、 展開 [BizTalk 群組]，然後再展開**應用程式**。  
  
3.  以滑鼠右鍵按一下您想要匯出其繫的結指向應用程式**匯出**，然後按一下 **繫結**。  
  
4.  在 [匯出繫結] 頁面中**匯出至檔案**，輸入要匯出繫結的.xml 檔案的絕對路徑。  
  
     範例： **C:\Bindings\Application1Bindings_Staging1.xml**  
  
5.  請確認**從目前的應用程式匯出所有繫結**已選取，然後按一下**確定**。  
  
6.  若要匯出群組的所有合作對象資訊，請選取**匯出全域合作對象資訊**核取方塊。  
  
     繫結就會匯出到您所指定位置中的 .xml 檔案。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別`cmd`，然後按一下 **確定**。  
  
2.  輸入下列命令，並以適當的值替代，如下表所述：  
  
     **BTSTask ExportBindings /Destination:** *值*[**/ApplicationName:***值*] [**/GlobalParties**] [**/Server:***值*] [**/database:***值*]  
  
     範例：  
  
     **BTSTask ExportBindings /Destination:"C:\Binding Files\MyBindings.xml"/applicationname: myapplication /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
    |參數|值|  
    |---------------|-----------|  
    |**/ 目的地**|要建立的繫結檔案完整路徑 (包含檔案名稱)。 如果具有相同路徑的繫結檔案已存在，將會覆寫檔案。 如果路徑中有空格，您必須將它括在雙引號 (") 中。|  
    |**/ 應用程式名稱**|要匯出其繫結的應用程式名稱。 應用程式必須存在。 若要確認應用程式名稱，您可以使用**ListApps**命令中所述[ListApps 命令](../core/listapps-command.md)。 如果沒有指定這個參數，將會使用預設的 BizTalk 應用程式。 如果名稱中有空格，您必須將它括在雙引號 (") 中。|  
    |**/ GlobalParties**|如果有指定，將匯出群組的全域合作對象資訊。|  
    |**/ 伺服器**|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
    |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="see-also"></a>另請參閱  
 [匯出繫結](../core/exporting-bindings6.md)   
 [ExportBindings 命令](../core/exportbindings-command.md)   
 [匯入 BizTalk 應用程式、 繫結和原則](../core/importing-biztalk-applications-bindings-and-policies.md)