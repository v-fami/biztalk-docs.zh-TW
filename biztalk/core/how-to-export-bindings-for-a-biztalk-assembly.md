---
title: "如何匯出 BizTalk 組件的繫結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies, bindings
- assemblies, exporting
- exporting, assemblies
ms.assetid: 7e37348d-5fa5-43cc-b3c0-2d8cb6a8f394
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64086cc8e54d89180d3c95268c78bc53e5ec9f55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-export-bindings-for-a-biztalk-assembly"></a>如何匯出 BizTalk 組件的繫結
本主題說明如何使用 BizTalk Server 管理主控台或命令列，將 BizTalk 組件的繫結匯出至 .xml 檔案。 接著您可以將這些繫結匯入至 BizTalk 應用程式，這時匯入的同名繫結會覆寫現有繫結。 在更新組件之前，您可能想要匯出其繫結，以便在更新後匯入繫結，重新套用它們。 如需更新應用程式和組件的詳細資訊，請參閱[更新 BizTalk 應用程式](../core/updating-biztalk-applications.md)。 如需有關如何使用繫結檔案的詳細資訊，請參閱[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組或「BizTalk Server 操作員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="to-export-bindings-for-a-biztalk-assembly"></a>若要匯出 BizTalk 組件的繫結  
  
#### <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀結構中，依序展開 [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、BizTalk 群組和 [應用程式]。  
  
3.  以滑鼠右鍵按一下包含組件的應用程式，指向**匯出**，然後按一下 **繫結**。  
  
4.  在 [匯出繫結] 頁面中**匯出至檔案**，輸入要匯出繫結的.xml 檔案的絕對路徑。  
  
     範例： **C:\Bindings\MyAssemblyBindings_Staging1.xml**  
  
5.  在匯出繫結 頁面上，按一下 **匯出所選組件的繫結**，然後在**組件**，按一下 組件。  
  
6.  如果您要匯出的所有群組中的合作對象資訊，請選取**匯出全域合作對象資訊**。  
  
     繫結就會匯出到您所指定位置中的 .xml 檔案。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別`cmd`，然後按一下 **確定**。  
  
2.  輸入下列命令，並以適當的值替代，如下表所述：  
  
     **BTSTask ExportBindings /Destination:** *值* **/AssemblyName:** *值*[**/GlobalParties**] [**/Server:***值*] [**/database:***值*]  
  
     範例：  
  
     **BTSTask ExportBindings /Destination:"C:\Binding Files\MyBindings.xml"/AssemblyName:"ErrorHandling.ErrorHandler，Version = 1.0.0.0，Culture = neutral，PublicKeyToken = 11e921d58826420e"/Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
    |參數|值|  
    |---------------|-----------|  
    |**/ 目的地**|要建立的繫結檔案完整路徑 (包含檔案名稱)。 如果具有相同路徑的繫結檔案已存在，將會覆寫檔案。 如果路徑中有空格，您必須將它括在雙引號 (") 中。|  
    |**/ AssemblyName**|要匯出其繫結的組件的本機唯一識別碼 (LUID)。 您可以使用，以取得應用程式中的成品的 Luid 清單[ListApp 命令](../core/listapp-command.md)。|  
    |**/ GlobalParties**|如果有指定，將匯出群組的全域合作對象資訊。|  
    |**/ 伺服器**|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
    |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="see-also"></a>另請參閱  
 [匯出繫結](../core/exporting-bindings6.md)   
 [ExportBindings 命令](../core/exportbindings-command.md)   
 [匯入 BizTalk 應用程式、 繫結和原則](../core/importing-biztalk-applications-bindings-and-policies.md)