---
title: 如何將 BizTalk 組件新增至應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [applications], adding assemblies
- assemblies, applications
- managing [assemblies], adding to applications
- applications, assemblies
- managing [assemblies], applications
ms.assetid: 1525a0f6-cb0f-43bf-a851-40c06ab2135e
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e6921612c84d3f37604e1330195c1c652d5b3fe
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008535"
---
# <a name="how-to-add-a-biztalk-assembly-to-an-application"></a>如何將 BizTalk 組件新增至應用程式
本主題描述如何使用 BizTalk Server 管理主控台或命令列，將 BizTalk 組件新增至應用程式。  
  
 當您新增 BizTalk 組件至應用程式時，請牢記下列要點：  
  
-   如果您想要新增和覆寫的組件，具有與應用程式中現有組件相同的本機唯一識別碼 (LUID)，請指定 Overwrite 選項。 若未指定此選項，且應用程式中現有的組件與所加入的組件具有相同的 LUID，則作業將會失敗。 LUID 包含組件檔案名稱、 版本、 文化特性和公開金鑰語彙基元。 您也可以使用應用程式中檢視成品的 Luid [ListApp 命令](../core/listapp-command.md)。  
  
-   如果您要加入的組件與未包含在此應用程式中的其他成品具有相依性，新增作業將會失敗。  
  
-   新增 BizTalk 組件時，您可以指定下列的一或多個選項，將組件安裝到全域組件快取 (GAC)。  
  
    -   **新增至全域組件快取新增資源 (gacutil) 上。** 如果選取此選項，當您使用本主題中的程序新增組件至應用程式時，會將組件安裝在本機電腦上的 GAC 中。  
  
    -   **新增至 MSI 檔案匯入 (gacutil) 的全域組件快取。** 選取此選項時，如果應用程式是匯出至 .msi 檔案，而 .msi 檔案又會匯出至 BizTalk 群組中，則匯出程序會將組件安裝在本機電腦上的 GAC 中。  
  
    -   **新增至 MSI 檔案安裝 (gacutil) 的全域組件快取。** 選取此選項時，如果應用程式是匯出至 .msi 檔案，再由 .msi 檔案將應用程式安裝在電腦上，則安裝程序會將組件安裝在本機電腦上的 GAC 中。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="to-add-a-biztalk-assembly-to-an-application"></a>將 BizTalk 組件新增至應用程式  
  
#### <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，展開 [BizTalk Server 管理] 和包含您要新增 BizTalk 組件的應用程式的 BizTalk 群組。  
  
3. 展開 [應用程式]，再展開您想要在其中新增 BizTalk 組件的應用程式。  
  
4. 以滑鼠右鍵按一下**資源**，指向**新增**，然後按一下  **BizTalk 組件**。  
  
5. 按一下 **新增**，選取 BizTalk 組件檔案，然後按一下**開啟**。  
  
6. 在 **目的地**，輸入要複製在安裝應用程式從.msi 檔案，包括檔案名稱中的組件檔案所在的位置的完整路徑。 如果不提供，安裝期間就不會將組件檔案複製到本機檔案系統。  
  
7. 在 **選項**，指定 BizTalk 組件安裝到 GAC 的選項，然後按一下**確定**。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1. 開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別`cmd`，然後按一下 **確定**。  
  
2. 輸入下列命令，並以適當的值替代，如下表所述：  
  
    **BTSTask AddResource** [**/ApplicationName:**<em>值</em>] **/Type:System.BizTalk:BizTalkAssembly** [**/Overwrite**] **/Source:**<em>值</em>[**/Destination:**<em>值</em>] [**/Options:GacOnAdd** &#124; **GacOnInstall**&#124;**GacOnImport**] [**/Server:**<em>值</em>] [**/資料庫：**<em>值</em>]  
  
    範例  
  
    **BTSTask AddResource /applicationname: myapplication /Type:System.BizTalk:BizTalkAssembly / 覆寫 /Source:"C:\BizTalk Assemblies\MyOrchestration.dll"/Destination:"C:\New BizTalk Assemblies\ MyOrchestration.dll"/Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
   |參數|ReplTest1|  
   |---------------|-----------|  
   |**/ 應用程式名稱**|加入 BizTalk 組件之 BizTalk 應用程式的名稱。 如果沒有指定應用程式名稱，將會使用預設的 BizTalk 應用程式。 如果名稱包含空格，您必須將它括在雙引號 (") 中。|  
   |**/ 類型**|**System.biztalk: biztalkassembly**|  
   |**/ 覆寫**|此選項指定更新現有的組件。 若未指定此選項，且應用程式中現有的組件與所加入的組件具有相同的 LUID，AddResource 作業將會失敗。 您也可以使用應用程式中檢視成品的 Luid [ListApp 命令](../core/listapp-command.md)。 如果其他應用程式相依於即將覆寫的組件，則即使指定此參數，AddResource 作業也會失敗。|  
   |**/ 來源**|組件檔案的完整路徑 (包含檔案名稱)。 如果路徑包含空格，您必須將它括在雙引號 (") 中。|  
   |**/ 目的地**|從 .msi 檔案安裝應用程式時，組件檔案之複製目的位置的完整路徑。 如果不提供，安裝期間就不會將組件檔案複製到本機檔案系統。 如果路徑包含空格，您必須將它括在雙引號 (") 中。|  
   |**/] [選項**|-   **GacOnAdd**： 在 AddResource 作業期間指定的組件安裝至全域組件快取 (GAC) 在本機電腦上。<br />-   **GacOnInstall**： 指定從.msi 檔案安裝應用程式時，將組件安裝到 GAC。<br />-   **GacOnImport**： 將組件安裝到 GAC，匯入應用程式.msi 檔案時指定。<br /><br /> 您必須以逗點分隔多個選項。|  
   |**/ 伺服器**|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
   |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="see-also"></a>另請參閱  
 [管理 BizTalk 組件](../core/managing-biztalk-assemblies.md)   
 [AddResource 命令：BizTalk 組件](../core/addresource-command-biztalk-assembly.md)