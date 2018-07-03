---
title: 如何匯出 BizTalk 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, exporting
- exporting, warnings
- exporting, applications
- applications, exporting
- applications, security
- applications, warnings
- exporting, security
ms.assetid: a1d6ffca-3d29-44c7-a811-6cf8b42e23f6
caps.latest.revision: 50
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c6bdab45366e4f1a540e436ee44f6736b04cee08
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977511"
---
# <a name="how-to-export-a-biztalk-application"></a>如何匯出 BizTalk 應用程式
本主題描述如何使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台或命令列匯出應用程式。 匯出 BizTalk 應用程式會產生 Windows Installer (.msi) 檔案，此檔案包含該應用程式及其中您選擇匯出的任何成品。 預設選項為選取該應用程式的所有成品，但您可選取其子集。 然後您可將 .msi 檔案匯入另一個 BizTalk 群組，將成品新增至新群組中的現有應用程式、更新現有應用程式中的成品，或在包含要匯入之成品的群組中建立新的應用程式。 如需詳細資訊，請參閱 <<c0> [ 如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。 您也使用.msi 檔案中所述，將會執行它，在電腦上安裝應用程式[如何安裝 BizTalk 應用程式](../core/how-to-install-a-biztalk-application.md)。 如果應用程式包含以檔案為基礎的成品，您還必須先安裝它之後才能開始運作。  
  
 匯出應用程式時，請牢記下列要點：  
  
- **匯入繫結時，會自動覆寫現有的繫結。** 如果您不希望正在匯出之應用程式中的繫結覆寫將匯入 .msi 檔案之應用程式中的繫結，則您不應該選取繫結檔案做為要匯出的資源。 當您匯入包含繫結檔案的 .msi 檔案到現有的應用程式中時，所匯入的繫結會覆寫現有的繫結，即使您並未選取覆寫現有成品的選項。  
  
- **使用者可能正在進行變更的成品時您正在匯出應用程式。** 如果使用者正在修改以資料庫為基礎的成品，例如虛擬目錄、 憑證或原則，匯出作業正在進行時，所做的變更將不會反映在匯出的.msi 檔案中。 因此，Microsoft 建議您將匯出作業排定在使用者可能不會對這些成品進行變更的時間。  
  
- **在 Windows Vista 上安裝.msi 時，就可以顯示不正確的錯誤**。 當使用安裝.msi 套件匯出[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您可能會收到下列不正確的錯誤，「 安裝程式發現意外的錯誤，安裝此套件。 這可能表示封裝有問題。 錯誤碼是 2869」。 若要更正這個錯誤，第一次匯入.msi 封裝使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]及重新匯出並安裝套件。  
  
- **應用程式可能相依於另一個應用程式。** 這可能影響您部署應用程式的方式。 如需詳細資訊，請參閱 <<c0> [ 相依性和應用程式部署](../core/dependencies-and-application-deployment.md)。  
  
- **在 匯出您的應用程式之前，您可以修改資源的目的地目錄。** 如果您想要變更的目的地位置，依序展開 應用程式的 資源 節點、 以滑鼠右鍵按一下您想要變更，然後選擇 的 resource**修改**。 在 [修改資源] 對話方塊中，輸入新的位置中**目的地位置**。  
  
- **如果應用程式包含已從 「 規則引擎 」 資料庫移除原則，匯出會失敗。** 當您使用規則引擎部署精靈從規則引擎資料庫移除原則後，在「未發佈」狀態下它會顯示在管理主控台中，且您無法匯出該應用程式。 如需有關 「 規則引擎部署精靈 」 的詳細資訊，請參閱[如何部署和解除部署原則和詞彙](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md)。  
  
> [!IMPORTANT]
>  .msi 檔案可能包含機密資料。 請確定執行步驟以確保檔案是安全的。 如需詳細資訊，請參閱 <<c0> [ 安全性和 Windows Installer](../core/security-and-windows-installer.md)。  
> 
>  在應用程式匯出期間，密碼會從應用程式繫結移除。 從 .msi 檔案安裝應用程式後，您必須重新設定密碼，應用程式才能運作。 然而，密碼不會從您新增至應用程式的任何繫結檔案移除。  
> 
>  如果應用程式包含使用 Web 服務的網站或協調流程，請注意虛擬目錄上的安全性設定，就是在應用程式匯出期間產生 .msi 檔案時生效的那些安全性設定。 如果您將應用程式部署到實際執行環境，則在匯出應用程式之前，應該驗證設定是否符合安全性需求。 如果虛擬目錄已存在於主機電腦，其安全性設定不會被覆寫，但應用程式中的檔案會新增至該虛擬目錄。 在應用程式匯入後，您應驗證安全性設定。  
> 
>  當應用程式匯出時，所有的判別存取控制清單 (DACL) 都會從檔案和資料夾中移除。 安裝應用程式之後，您應該重新設定檔案和資料夾上的所有安全性設定，包括虛擬目錄。  
> 
> [!NOTE]
>  如果匯出作業失敗，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]刪除所有的暫存檔案以及.msi 檔案中，若已建立。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組成員的帳戶登入。 如需詳細的權限的相關資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。 此外，還必須安裝「商務規則引擎」。 如需詳細資訊，請參閱 < [BizTalk Server 2013 和 2013 R2 的安裝概觀](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)。  
  
## <a name="to-export-an-application"></a>匯出應用程式  
  
#### <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台  
  
1. 按一下 **開始**，按一下**所有程式**， [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。  
  
2. 在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開 BizTalk 群組，然後再展開**應用程式**。  
  
3. 以滑鼠右鍵按一下您想要匯出，並指向應用程式**匯出**，然後按一下**MSI 檔案**。  
  
4. 在歡迎使用匯出 MSI 檔案精靈頁面中，按一下**下一步**。  
  
5. 在選取資源 頁面上，選取要匯出至.msi 檔案中，成品，然後按一下**下一步**。  
  
6. 如果出現提示，請在 [指定 IIS 主控件] 頁面中，輸入主控您想要包含此項目，然後按一下 [虛擬目錄之電腦的伺服器名稱**下一步]**。 只有在虛擬目錄先前已新增至 BizTalk 管理資料庫，例如已新增至應用程式或匯入應用程式時，系統才會提示您指定伺服器。  
  
7. 在 [相依性] 頁面中，檢閱應用程式的相依性，然後按一下 [**下一步]**。  
  
8. 在 [目的地] 頁面中**目的地應用程式名稱**，輸入應用程式名稱。  
  
9. 在  **MSI 檔案來產生**，輸入.msi 檔案的完整路徑，然後按一下**匯出**。 範例：C:\MSI\Errorhandling.msi  
  
    > [!NOTE]
    >  Microsoft 建議您將 .msi 檔案儲存在安全的資料夾中。  
  
10. 在上 摘要 頁面中，記下這項作業，記錄檔的位置，然後按一下 **完成**。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1. 開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別`cmd`，然後按一下 **確定**。  
  
2. 輸入下列命令，並以適當的值替代，如下表所述：  
  
    **BTSTask ExportApp** [**/ApplicationName:**<em>值</em>] **/package:**<em>值</em>[**ResourceSpec:**<em>值</em>[**/Server:**<em>值</em>] [**/database:**<em>值</em>]  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
    範例  
  
    **BTSTask ExportApp /applicationname: myapplication /Package:C:/MSI/MyApplication.msi /ResourceSpec:"C:\My Files\ResourceSpec.xml"/Server:MySQLServer /Database:BizTalkMgmtDb**  
  
    您所指定的成品會匯入至指定位置的 .msi 檔案中。  
  
   |參數|ReplTest1|  
   |---------------|-----------|  
   |**/ 應用程式名稱**|要匯出的 BizTalk 應用程式的名稱。 如果沒有指定應用程式名稱，將會使用預設的 BizTalk 應用程式。 如果名稱包含空格，必須以雙引號 (") 將其括住。|  
   |**/ 套件**|要建立之 .msi 檔案的路徑，包含其檔案名稱。|  
   |**/ ResourceSpec**|資源規格 XML 檔案的路徑，包含檔案名稱。 您可以指定要匯出的編輯資源規格 XML 檔案，當您執行 ListApp 建立哪些成品命令搭配 ResourceSpec 參數中所述[ListApp 命令](../core/listapp-command.md)。 您必須手動編輯此檔案，在 Web 伺服器位於遠端電腦上時，為您想匯出的虛擬目錄新增 Internet Information Services (IIS) 主機伺服器名稱。|  
   |**/ 伺服器**|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
   |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="see-also"></a>另請參閱  
 [匯出 BizTalk 應用程式、 繫結和原則](../core/exporting-biztalk-applications-bindings-and-policies.md)   
 [ExportApp 命令](../core/exportapp-command.md)