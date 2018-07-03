---
title: 如何將 COM 元件新增至應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [applications], COM components
- managing [resources], COM components
- applications, COM components
- COM components, applications
ms.assetid: fdda1a9d-96af-41fe-9d94-ee1fbd80a7c9
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca1abbb78f35535c84ee7cc0f83271919a82cd5f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015743"
---
# <a name="how-to-add-a-com-component-to-an-application"></a>如何將 COM 元件新增至應用程式
本主題描述如何使用 [BizTalk Server 管理] 主控台或命令列，將 COM 元件加入至 BizTalk 應用程式。  
  
 當您將 COM 元件新增至應用程式時，請牢記下列要點：  
  
-   如果您想要覆寫應用程式中現有的 COM 元件，請指定「覆寫」選項。 只有在兩個成品有相同的本機唯一識別碼 (LUID) 時，才需要覆寫選項。 若未指定此選項，而且在加入 COM 元件時，應用程式中已有元件具有相同的 LUID，則新增作業將會失敗。 您也可以使用應用程式中檢視成品的 Luid [ListApp 命令](../core/listapp-command.md)。  
  
-   BizTalk Server 不會檢查 COM 元件的相依性來驗證元件是否存在，所以您應該檢查元件相依的成品是否存在。  
  
-   如果您加入 64 位元的 Unmanaged COM 或 COM+ 元件，而試圖將含有這些 COM 或 COM+ 元件的應用程式安裝於 32 位元電腦，屆時就不會安裝元件。 只能安裝在 64 位元電腦上。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="to-add-a-com-component-to-an-application"></a>新增 COM 元件至應用程式  
  
#### <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台  
  
1. 按一下 **開始**，按一下**程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，展開 BizTalk Server 管理，展開 BizTalk 群組、 展開 應用程式，，然後展開您想要新增 COM 元件的應用程式。  
  
3. 以滑鼠右鍵按一下**資源**資料夾，指向**新增**，然後按一下**資源**。  
  
4. 按一下 **新增**，選取 COM 元件，然後按一下**開啟**。  
  
5. 在 **檔案類型**下拉式清單中，按一下**system.biztalk: com**。  
  
6. 在 **選項**，選取或清除**註冊目的地檔案 (regsvr32)** 根據是否想要在應用程式時，要加入至 Windows 登錄元件的核取方塊安裝。  
  
7. 在 **目的地**，輸入要複製在安裝應用程式從.msi 檔案，包括檔案名稱中的 COM 元件所在的位置的完整路徑。 如果未提供此路徑，安裝期間就不會將組件檔案複製到本機檔案系統。 如果您選取，則需要此路徑**註冊目的地檔案 (regsvr32)** 上一個步驟中的核取方塊。  
  
    範例： **%BTAD_InstallDir%\MyComponent.dll**  
  
8. 完成後，請按一下 **[確定]**。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1. 開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別`cmd`，然後按一下 **確定**。  
  
2. 輸入下列命令，並以適當的值替代，如下表所述：  
  
    **BTSTask AddResource** [**/ApplicationName:**<em>值</em>] **/Type:System.BizTalk:Com** [**/覆寫**] **/Source:**<em>值</em>[**/Destination:**<em>值</em>] [**/Options:Regsvr32OnInstall**] [**/Server:**<em>值</em>] [**/database:**<em>值</em>]  
  
    範例  
  
    **BTSTask AddResource /applicationname: myapplication /Type:System.BizTalk:Com / 覆寫 /Source:"C:\Source Components\COM.dll"/Destination:"C:\New Components\COM.dll"/Options:Regsvr32OnInstall /Server:MyDatabaseServer/資料庫：BizTalkMgmtDb**  
  
   |參數|ReplTest1|  
   |---------------|-----------|  
   |**/ 應用程式名稱**|加入 COM 元件的 BizTalk 應用程式的名稱。 若未指定應用程式名稱，將使用群組預設的 BizTalk 應用程式。 如果名稱包含空格，您必須將它括在雙引號 (") 中。|  
   |**/ 類型**|**System.biztalk: com** （此值不區分大小寫）。|  
   |**/ 覆寫**|此選項指定更新現有的 COM 元件。 若未指定此選項，且應用程式中現有的 COM 元件與所加入的 COM 元件具有相同的 LUID，AddResource 作業將會失敗。 您也可以使用應用程式中檢視成品的 Luid [ListApp 命令](../core/listapp-command.md)。|  
   |**/ 來源**|COM 元件 .dll 檔案的完整路徑 (包含檔案名稱)。 如果路徑包含空格，您必須將它括在雙引號 (") 中。|  
   |**/ 目的地**|從 .msi 檔案安裝應用程式時，COM 元件 .dll 檔案之複製目的位置的完整路徑。 如果不提供，安裝期間就不會將檔案複製到本機檔案系統，以致安裝期間並未將元件寫入 Windows 登錄。 如果路徑包含空格，您必須將它括在雙引號 (") 中。 如果指定了 Regsvr32OnInstallOption，就必須一併指定目的地。|  
   |**/] [選項**|**Regsvr32OnInstall。** 指定從 .msi 檔案安裝應用程式時，將 COM 元件寫入 Windows 登錄。 如果指定這個選項，您也必須指定目的地。|  
   |**/ 伺服器**|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
   |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="see-also"></a>另請參閱  
 [管理.NET 組件、 憑證和其他資源](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [AddResource 命令： COM 元件](../core/addresource-command-com-component.md)   
 [建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)