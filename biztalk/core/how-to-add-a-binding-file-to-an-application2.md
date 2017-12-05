---
title: "如何將繫結檔案新增至 Application2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [applications], binding files
- applications, binding files
- binding files, applications
ms.assetid: 1543ee5f-9ae4-4683-b6fe-ee84028c381d
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a1c7f0a73f811a6b339428e62a93916d9301edf
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-add-a-binding-file-to-an-application"></a>如何將繫結檔案新增至應用程式
本主題描述如何使用 BizTalk Server 管理主控台或命令列，將繫結檔案新增至 BizTalk 應用程式。 您可能想要這樣做可以讓應用程式或組件的部署更容易中所述[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。  
  
 中所述，您可以從 BizTalk 應用程式的組件、 應用程式或群組匯出繫結匯出到.xml 檔案[匯出繫結](../core/exporting-bindings6.md)，然後使用本主題中的其中一個程序將繫結檔案新增至應用程式。  
  
 這麼做之後，繫結檔案便會新增至 BizTalk 管理資料庫，也會顯示於 BizTalk Server 管理主控台，列在應用程式的 [資源] 資料夾中。 與匯入繫結檔案不同，新增繫結檔案不會立即套用其繫結， 而是在應用程式匯入到其他 BizTalk 群組時，才會套用繫結。  
  
> [!IMPORTANT]
>  基於安全性理由，當您匯出繫結時，BizTalk Server 會從該檔案移除繫結的密碼。 匯入繫結後，您必須重新設定密碼，傳送埠和接受位置才能正常運作。 您可以在 BizTalk Server 管理主控台的 [傳輸屬性] 對話方塊中，為傳送埠或接收位置設定密碼。 如需指示，請參閱[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。 另請參閱[如何建立接收位置](../core/how-to-create-a-receive-location.md)。  
  
> [!NOTE]
>  當您使用 [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] 中產生的繫結檔案時，要注意主控件的信任層級並未儲存於繫結檔案中。 在繫結匯入或應用程式匯入期間套用繫結時，只會根據主控件名稱將成品繫結到主控件。 您應該驗證成品確實已繫結到正確的主控件，而且信任層級確實適當。  
  
 當您新增繫結檔案至應用程式時，您可以使用代表環境 (例如「測試」或「實際執行」) 的字串指定目標部署環境的值。 您可以使用任意字串表示此值。 然後，當您匯入應用程式時，就可以藉由提供指定其目標部署環境的值，選取要套用的繫結檔案。 這麼做之後，便會從繫結檔案套用繫結。 該檔案中與應用程式現有繫結同名的繫結，將會自動覆寫現有的繫結。  
  
 當您匯入應用程式時，將依下列順序套用繫結。 由於繫結是在匯入過程中套用，新的繫結會覆寫先前已套用的同名繫結。 也就是說，同名的繫結當中最後套用的繫結將會生效。  
  
1.  並非透過繫結檔案明確加入至應用程式，而是使用者明確選定欲匯出至應用程式 .msi 檔案的應用程式繫結 (由 BizTalk Server 所產生)。  
  
2.  已明確加入，但未指定目標部署環境的繫結檔案。 套用此集合中的繫結時，並無特定順序。  
  
3.  已明確加入，且其相關聯目標部署環境與應用程式匯入所選定的部署環境相符的繫結。 套用此集合中的繫結時，並無特定順序。  
  
 如需有關匯入應用程式及套用繫結的詳細資訊，請參閱[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="to-add-a-binding-file-to-an-application"></a>將繫結檔案新增至應用程式  
  
#### <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，展開 BizTalk Server 管理 和 包含您要新增繫結檔案的應用程式的 BizTalk 群組。  
  
3.  展開 [應用程式]，然後以滑鼠右鍵按一下您想要在其中新增繫結檔案的應用程式。  
  
4.  指向**新增**，然後按一下 **資源**。  
  
5.  按一下**新增**，選取要新增，然後按一下檔案**開啟**。  
  
6.  若要覆寫此檔案名稱相同的應用程式中現有的繫結檔案，請選取**覆寫所有**核取方塊。 如果有另一個同名的檔案存在，而您未選取此核取方塊，新增作業就會失敗。  
  
7.  在**檔案類型**下拉式清單中，選取**system.biztalk: biztalkbinding**。  
  
8.  在**目標環境**，輸入一個字串，代表要套用，例如 「 測試 」，然後按一下 此檔案中的繫結的目標部署環境**確定**。  
  
    > [!IMPORTANT]
    >  如果讓這個欄位空白，則每當匯入應用程式時，就會套用這個檔案中的繫結。  
  
     新增繫結檔案之後，它會顯示在應用程式的 [資源] 資料夾中。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別`cmd`，然後按一下 **確定**。  
  
2.  輸入下列命令，並以適當的值替代，如下表所述：  
  
     **BTSTask AddResource** [**/ApplicationName:"***值***"**] **/Type:System.BizTalk:BizTalkBinding** [**/覆寫**] **/source:***值***/Property:TargetEnvironment ="***值* **"** [**/Server:***值*] [**/database:***值*]  
  
     範例：  
  
     **BTSTask AddResource /ApplicationName:"My Application"/Type:System.BizTalk:BizTalkBinding /Source:"C:\Binding Files\MyBinding.xml"/Property:TargetEnvironment = 「 生產 」 /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
    |參數|值|  
    |---------------|-----------|  
    |**/ 應用程式名稱**|加入繫結檔案的 BizTalk 應用程式的名稱。 如果沒有指定應用程式名稱，將會使用預設的 BizTalk 應用程式。 如果名稱包含空格，您必須將它括在雙引號 (") 中。|  
    |**/ 類型**|**System.biztalk: biztalkbinding** （此值不區分大小寫）。|  
    |**/ 覆寫**|此選項指定更新現有的繫結檔案。 若未指定此選項，且應用程式中現有的繫結檔案與所加入的繫結檔案同名，AddResource 作業將會失敗。|  
    |**/ 來源**|繫結檔案的完整路徑 (包含檔案名稱)。 如果路徑包含空格，您必須將它括在雙引號 (") 中。|  
    |**/Property:TargetEnvironment =**|用於指定目標部署環境的字串。 您可以使用任意字串，例如「實際執行」。 範例： **/Property:TargetEnvironment = 「 生產 」**<br /><br /> 如果未指定值為\<預設\>自動套用。 此值區分大小寫。 如果參數值包含空格，您必須將它括在雙引號 (") 中。 環境值的長度上限為 128 個字元。|  
    |**/ 伺服器**|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
    |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="see-also"></a>請參閱  
 [管理.NET 組件、 憑證和其他資源](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [AddResource 命令： BizTalk 繫結](../core/addresource-command-biztalk-binding.md)   
 [建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)