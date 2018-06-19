---
title: 如何將檔案新增至應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [applications], adding files
- files, adding to applications
- managing [resources], adding files
ms.assetid: 6665b946-113a-4026-a0a3-6b67ede4b689
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4493eafe2bba4e1203a230180024e0e5a8a2ce08
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247734"
---
# <a name="how-to-add-a-file-to-an-application"></a>如何新增檔案至應用程式
本主題說明如何使用「BizTalk Server 管理」主控台或命令列，將檔案新增至 BizTalk 應用程式。 在安裝應用程式時，新增至應用程式的檔案會複製到安裝資料夾。 檔案也可以匯出至應用程式的 .msi 檔案中，並且隨著應用程式移至不同的部署環境。  
  
> [!NOTE]
>  如需新增讀我檔案的指示，請參閱[如何連結到讀我檔案](../core/how-to-link-to-a-readme-file.md)。  
  
 如果您想要覆寫應用程式中現有的檔案，請指定 [覆寫] 選項。 只有在兩個檔案都具有相同的名稱時，覆寫選項才有作用。 若未指定此選項，而且應用程式中現有的檔案與所加入的檔案同名，新增作業將會失敗。  
  
> [!NOTE]
>  不同於其他的成品類型，BizTalk 群組可包含一個以上的同名檔案。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="to-add-a-file-to-an-application"></a>若要新增檔案至應用程式  
  
#### <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開 [[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]] 和包含您想要新增檔案之應用程式的 BizTalk 群組。  
  
3.  展開 [應用程式]，再展開您想要在其中新增檔案的應用程式。  
  
4.  以滑鼠右鍵按一下**資源**資料夾，指向**新增**，然後按一下 **資源**。  
  
5.  按一下**新增**，並選取檔案，然後按一下 **開啟**。  
  
6.  在**檔案類型**下拉式清單中，選取**system.biztalk: file**。  
  
7.  在**目的地**，輸入從.msi 檔案，包括檔案名稱安裝應用程式時複製檔案之位置的完整路徑。 預設值為應用程式安裝資料夾 %BTAD_InstallDir%。 如果未提供此路徑，安裝期間就不會將組件檔案複製到本機檔案系統。  
  
8.  完成後，請按一下 **[確定]**。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別`cmd`，然後按一下 **確定**。  
  
2.  輸入下列命令，並以適當的值替代，如下表所述：  
  
     **BTSTask AddResource** [**/ApplicationName:***值*] **/Type:System.BizTalk:File** [**/覆寫**] **/Source:***值*[**/Destination:***值*] [**/Server:** *值*] [**/database:***值*]  
  
     範例：  
  
     **BTSTask AddResource /applicationname: myapplication /Type:System.BizTalk:File / 覆寫 /Source:"C:\Source Files\File.txt"/Destination:"C:\New Files\File.txt"/Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
    |參數|值|  
    |---------------|-----------|  
    |**/ 應用程式名稱**|加入檔案的 BizTalk 應用程式的名稱。 如果沒有指定應用程式名稱，將會使用預設的 BizTalk 應用程式。 如果名稱包含空格，您必須將它括在雙引號 (") 中。|  
    |**/ 類型**|**System.biztalk: file** （此值不區分大小寫）。|  
    |**/ 覆寫**|此選項指定更新現有的檔案。 若未指定此選項，且應用程式中現有的檔案與所加入的檔案同名，AddResource 作業將會失敗。|  
    |**/ 來源**|檔案的完整路徑 (包含檔案名稱)。 如果路徑包含空格，您必須將它括在雙引號 (") 中。|  
    |**/ 目的地**|從 .msi 檔案安裝應用程式時，檔案之複製目的位置的完整路徑。 如果路徑包含空格，您必須將它括在雙引號 (") 中。 如果不提供，安裝期間就不會將檔案複製到本機檔案系統。|  
    |**/ 伺服器**|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
    |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="see-also"></a>另請參閱  
 [管理.NET 組件、 憑證和其他資源](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [AddResource 命令： 檔案](../core/addresource-command-file.md)   
 [建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)