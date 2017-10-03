---
title: "如何將.NET 組件新增至應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [.NET assemblies], adding to applications
- managing [applications], .NET assemblies
- managing [.NET assemblies], applications
- applications, .NET assemblies
- .NET assemblies, adding to applications
ms.assetid: 75dc3303-a622-40df-881e-3109cbc81c91
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b455dfb8f84580e3a8a4f5b6e2322c4f4e1d1b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-net-assembly-to-an-application"></a>如何將 .NET 組件新增至應用程式
本主題說明如何使用 BizTalk Server 管理主控台或命令列，將非 BizTalk 組件的 .NET 組件新增至 BizTalk 應用程式。 當您將 .NET 組件新增至應用程式時，請牢記下列要點：  
  
-   如果您想要覆寫應用程式中現有的組件，請指定 [覆寫] 選項。 只有在兩個組件有相同的 LUID 時，才需要覆寫選項。 若未指定此選項，而且在加入組件時應用程式中現有組件具有相同的 LUID，則新增作業將會失敗。 您也可以使用應用程式中檢視成品的 Luid [ListApp 命令](../core/listapp-command.md)。  
  
-   新增 .NET 組件時，您可以指定下列的一或多個選項，將組件安裝到全域組件快取 (GAC)：  
  
    -   **新增至全域組件快取新增資源 (gacutil) 上。** 如果選取此選項，當您使用本主題中的程序新增組件至應用程式時，會將組件安裝在本機電腦上的 GAC 中。  
  
    -   **新增至 MSI 檔案匯入 (gacutil) 的全域組件快取。** 選取此選項時，如果應用程式是匯出至 .msi 檔案，而 .msi 檔案又會匯出至 BizTalk 群組中，則匯出程序會將組件安裝在本機電腦上的 GAC 中。 當應用程式包含原則及其依賴的組件時，請選取這個選項。 這是因為當您匯入包含原則的應用程式時，原則依賴的任何組件都必須存在於 GAC。  
  
    -   **新增至 MSI 檔案安裝 (gacutil) 的全域組件快取。** 選取此選項時，如果應用程式是匯出至 .msi 檔案，再由 .msi 檔案將應用程式安裝在電腦上，則安裝程序會將組件安裝在本機電腦上的 GAC 中。  
  
    -   **顯示 COM 元件 (regasm)。** 選取此選項時，如果應用程式是匯出至 .msi 檔案，而且應用程式是從 .msi 檔案安裝到電腦中，便會做為安裝程序的一部分，而將 Managed COM 組件新增至本機電腦中的 Windows 登錄中。 如果您指定這個選項，也就必須在 [目的] 中指定檔案的位置。  
  
    -   **註冊已服務元件 (regsvcs)。** 當您選取此選項時，如果應用程式匯出至.msi 檔案，並從.msi 檔案的電腦上安裝應用程式時，managed 的 COM + 組件會加入至 Windows 登錄在本機電腦安裝程序的一部分。 如果您指定這個選項，也就必須在 [目的] 中指定檔案的位置。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="to-add-a-net-assembly-to-an-application"></a>若要將 .NET 組件新增至應用程式  
  
#### <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、 依序展開 BizTalk 群組、 展開**應用程式**，然後展開您要新增.NET 組件的應用程式。  
  
3.  以滑鼠右鍵按一下**資源**資料夾，指向**新增**，然後按一下 **資源**。  
  
4.  按一下**新增**，按一下 組件，然後按一下**開啟**。  
  
5.  在**檔案類型**下拉式清單中，選取**system.biztalk: assembly**。  
  
6.  在**選項**，選取這個組件的部署選項。  
  
7.  在**目的地**，輸入從.msi 檔案，包括檔案名稱安裝應用程式時複製檔案之位置的完整路徑。 如果未提供此路徑，安裝期間就不會將組件檔案複製到本機檔案系統。 若要將檔案複製到應用程式安裝資料夾，您可以在路徑中使用 %BTAD_InstallDir% 環境變數，它會接受應用程式在安裝時應用程式安裝資料夾的值。 如此一來，當您指定目的位置時，便不需要知道應用程式安裝資料夾的路徑。  
  
     範例： **%BTADInstall_Dir%\Assemblies\Orchestrations.dll**  
  
8.  按一下**相依性**索引標籤上，並檢視這個組件所依賴的成品。  
  
9. 如果這個組件所依賴的成品不存在於此應用程式，而且您想要新增它，請按一下**應用程式中加入**，瀏覽至成品，然後按一下**開啟**。  
  
10. 完成後，請按一下 **[確定]**。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別`cmd`，然後按一下 **確定**。  
  
2.  輸入下列命令，並以適當的值替代，如下表所述：  
  
     **BTSTask AddResource** [**/ApplicationName:***值*] **/Type:System.BizTalk:Assembly** [**/覆寫**]**/Source:***值*[**/Destination:***值*] [**/Options:GacOnAdd***&#124;* **GacOnInstall***&#124;***GacOnImport**&#124;**RegasmOnInstall**&#124;**RegsvcsOnInstall**] [**/Server:***值*] [**/database:***值*]  
  
     範例：  
  
     **BTSTask AddResource /applicationname: myapplication /Type:System.BizTalk:Assembly / 覆寫 /Source:"C:\Source Assemblies\MyAssembly.dll"/Destination:"%BTAD_InstallDir%\New Assemblies\MyAssembly.dll"/Options:GacOnAdd、 RegasmOnInstall/Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
    |參數|值|  
    |---------------|-----------|  
    |**/ 應用程式名稱**|加入組件之 BizTalk 應用程式的名稱。 若未指定應用程式名稱，將使用群組預設的 BizTalk 應用程式。 如果名稱包含空格，您必須將它括在雙引號 (") 中。|  
    |**/ 類型**|**System.biztalk: assembly** （此值不區分大小寫）。|  
    |**/ 覆寫**|此選項指定更新現有的組件。 若未指定此選項，且應用程式中現有的組件與所加入的組件具有相同的完整名稱，AddResource 作業將會失敗。 完整名稱是由組件檔案名稱、版本、文化特性和公開金鑰 Token 所組成。 您也可以使用應用程式中檢視成品的 Luid [ListApp 命令](../core/listapp-command.md)。|  
    |**/ 來源**|組件檔案的完整路徑 (包含檔案名稱)。 如果路徑包含空格，您必須將它括在雙引號 (") 中。|  
    |**/ 目的地**|從 .msi 檔案安裝應用程式時，組件檔案之複製目的位置的完整路徑。 如果不提供，安裝期間就不會將組件檔案複製到本機檔案系統。 如果路徑包含空格，您必須將它括在雙引號 (") 中。 如果指定 RegasmOnInstall 或 RegsvcsOnInstall 選項，您也必須指定目的地。 **注意：**您可以在路徑中使用 %btad_installdir%環境變數。 它會接受應用程式在安裝時應用程式安裝資料夾的值。 如此一來，當您指定目的位置時，便不需要知道應用程式安裝資料夾的路徑。 範例： %BTAD_InstallDir%\Assemblies\Orchestrations.dll|  
    |**/ 選項**|-   **為 GacOnAdd**： 在 AddResource 作業期間，在本機電腦上安裝至全域組件快取 (GAC) 組件。<br />-   **GacOnInstall**： 從.msi 檔案安裝應用程式時，將組件安裝到 GAC。<br />-   **GacOnImport**： 匯入應用程式.msi 檔案時，將組件安裝到 GAC。<br />-   **RegasmOnInstall**： 將 managed 的 COM 組件加入至 Windows 登錄中，從.msi 檔案安裝應用程式。 如果指定這個選項，您也必須指定目的地。<br />-   **RegsvcsOnInstall**： 將 managed 的 COM + 組件加入至 Windows 登錄中，從.msi 檔案安裝應用程式。 如果指定這個選項，您也必須指定目的地。<br /><br /> 您必須以逗點分隔多個選項。|  
    |**/ 伺服器**|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
    |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="see-also"></a>另請參閱  
 [管理.NET 組件、 憑證和其他資源](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [AddResource 命令：.NET 組件](../core/addresource-command-net-assembly.md)   
 [建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)