---
title: "如何將 BAM 成品新增至應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications, definition files [BAM]
- BAM, applications
- managing [applications], definition files [BAM]
- definition files [BAM], managing
ms.assetid: 86f19030-e510-4527-ba74-10498c361c00
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44b4a55141b2e5cfbc527dd386c9f1cbdd464dc9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-bam-artifact-to-an-application"></a>如何將 BAM 成品新增至應用程式
本主題描述如何使用 [BizTalk Server 管理] 主控台或命令列，將 BAM 成品新增至 BizTalk 應用程式。 新增 BAM 定義檔案時，不會一併部署 BAM 定義。 當匯入應用程式 .msi 檔案時，會部署此 BAM 定義。  
  
 如果您想要覆寫應用程式中現有的 BAM 成品，請指定覆寫選項。 現有的 BAM 成品具有相同的檔案名稱與您想要加入時才需要覆寫選項。 如果未指定，而且 BAM 成品已經存在於相同的檔案名稱與所新增的應用程式，新增作業將會失敗。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="to-add-a-bam-artifact-to-an-application"></a>新增 BAM 成品至應用程式  
  
#### <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台  
  
1.  按一下**啟動**，按一下  **Al 程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]展開 BizTalk 群組、 展開 應用程式，，然後展開您要加入 BAM 成品檔案的應用程式。  
  
3.  以滑鼠右鍵按一下**資源**資料夾，指向**新增**，然後按一下 **資源**。  
  
4.  按一下**新增**選取 BAM 成品的檔案，然後按一下 **開啟**。  
  
5.  在**檔案類型**下拉式清單中，選取**system.biztalk: bam**。  
  
6.  在**目的地**，輸入從.msi 檔案，包括檔案名稱安裝應用程式時複製成品檔案之位置的完整路徑。 如果未提供此路徑，安裝期間就不會將檔案複製到本機檔案系統，以致安裝期間無法將元件寫入 Windows 登錄。  
  
     範例： **C:\My Applications\MyBAMfile.xml**  
  
7.  完成後，請按一下 **[確定]**。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別`cmd`，然後按一下 **確定**。  
  
2.  輸入下列命令，並以適當的值替代，如下表所述：  
  
     **BTSTask AddResource** [**/ApplicationName:***值*] **/Type:System.BizTalk:Bam** [**/覆寫**] **/Source:***值*[**/Destination:***值*] [**/Server:** *值*] [**/database:***值*]  
  
     範例：  
  
     **BTSTask AddResource /applicationname: myapplication /Type:System.BizTalk:Bam / 覆寫 /Source:"C:\Source BAMfiles\MyBAMfile.xml"/Destination:"%BTADInstallDir%\BAMfiles\MyBAMfile.xml"/Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
    |參數|值|  
    |---------------|-----------|  
    |**/ 應用程式名稱**|加入 BAM 成品的 BizTalk 應用程式的名稱。 若未指定應用程式名稱，將使用群組預設的 BizTalk 應用程式。 如果名稱包含空格，您必須將它括在雙引號 (") 中。|  
    |**/ 類型**|**System.biztalk: bam** （此值不區分大小寫）。|  
    |**/ 覆寫**|覆寫現有 BAM 成品的選項。 若未指定此選項，且應用程式中現有的 BAM 成品與所新增之 BAM 成品同檔名，則 AddResource 作業將會失敗。|  
    |**/ 來源**|BAM 成品檔案的完整路徑 (包含檔案名稱)。 如果路徑包含空格，您必須將它括在雙引號 (") 中。|  
    |**/ 目的地**|從 .msi 檔案安裝應用程式時，BAM 成品檔案之複製目的位置的完整路徑。 如果不提供，安裝期間就不會將檔案複製到本機檔案系統。 如果路徑包含空格，您必須將它括在雙引號 (") 中。 您可以在路徑中使用 %BTADInstallDir% 環境變數來指定應用程式安裝資料夾。|  
    |**/ 伺服器**|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
    |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="see-also"></a>另請參閱  
 [管理.NET 組件、 憑證和其他資源](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [AddResource 命令： BAM 成品](../core/addresource-command-bam-artifact.md)   
 [建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)   
 [如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)