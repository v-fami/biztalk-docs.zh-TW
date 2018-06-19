---
title: 如何匯入 BizTalk 應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying, planning
- planning, importing
- importing, applications
- applications, planning
- planning, deploying
- applications, importing
- importing, planning
ms.assetid: 51169f35-d572-4612-9104-a59908e24874
caps.latest.revision: 70
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 65a2e29be82cb55b0c8509eb3adb346f48d5b794
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26010367"
---
# <a name="how-to-import-a-biztalk-application"></a>如何匯入 BizTalk 應用程式
本主題描述如何使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台或命令列匯入 BizTalk 應用程式的 BizTalk 群組。 匯入 BizTalk 應用程式會在 BizTalk 管理資料庫中註冊成品，並將成品的資料寫入適當的 BizTalk 資料庫。 如需詳細資訊，請參閱[什麼發生時匯入成品](../core/what-happens-when-artifacts-are-imported.md)。 匯入應用程式並不會安裝該應用程式， 您必須先安裝包含檔案架構成品的應用程式，才可以執行該應用程式。  
  
 當您使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台來匯入應用程式，讓您從中啟動 「 匯入 MSI 精靈 」 的位置決定您是否可以匯入成品的同時來建立新的應用程式。 如果是使用滑鼠右鍵按一下 BizTalk 群組來啟動精靈，就必須提供應用程式名稱。 如果 BizTalk 群組中具有您指定名稱的現有應用程式，就會將檔案中的成品匯入此應用程式；否則，會建立具有指定名稱的新應用程式，再將成品匯入其中。 如果是使用滑鼠右鍵按一下應用程式來啟動精靈，就無法指定應用程式名稱，而會將成品匯入目前的應用程式中。  
  
 使用 BTSTask 命令列工具匯入 .msi 檔案時，不一定需要提供應用程式名稱。 如果沒有提供應用程式名稱，就會將成品匯入預設應用程式中。  
  
 匯入後的成品，您可以檢視它們適當的資料夾中的應用程式的資料夾下[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 您也可以檢視成品的清單應用程式中使用 BTSTask 中, 所述[ListApp 命令](../core/listapp-command.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要匯入 BizTalk 應用程式，您必須登入帳戶的成員[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。 若要安裝 BizTalk 應用程式，則也必須具有本機檔案系統的寫入權限。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="considerations-for-importing-applications"></a>匯入應用程式的考量  
 匯入應用程式時，適用下列考量：  
  
-   **匯入應用程式從舊版的 BizTalk Server**。 如果您從 BizTalk Server 2006 R2 或 BizTalk Server 2009 中，匯入應用程式的應用程式包含 EDI/AS2 合作對象資料，應用程式匯入可能會失敗，因為交易夥伴管理模型已大幅變更，BizTalk Server 中。 您必須改用「合作對象移轉工具」，從舊版 BizTalk Server 移轉合作對象資料。 如需此工具的詳細資訊，請參閱[移轉 EDI 成品從 BizTalk Server 先前版本](http://msdn.microsoft.com/library/b956a97e-03d0-47ea-a2ce-c07a339c0f2c)。  
  
-   **匯入繫結永遠會覆寫現有的繫結。** 在現有應用程式中匯入包含繫結的 .msi 檔案時，現有繫結會遭到具有相同名稱的匯入繫結所覆寫。 即使您沒有在匯入 .msi 檔案時選取覆寫現有成品選項也會如此。 如果不想用匯入的應用程式繫結來覆寫要匯入 .msi 檔案的應用程式的現有繫結，則應該在匯出作業期間選擇不要將繫結檔案做為匯出資源。 如需詳細資訊，請參閱[如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)。  
  
     由於繫結是在匯入過程中套用，新的繫結會覆寫先前已套用的同名繫結。 也就是說，同名的繫結當中最後套用的繫結將會生效。 當您匯入應用程式時，將依下列順序套用繫結：  
  
    1.  應用程式所產生的繫結[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]不明確加入到應用程式透過繫結檔案，但匯出到應用程式.msi 檔案的使用者已明確選取的。  
  
    2.  已明確加入，但未指定目標部署環境的繫結檔案。 套用此集合中的繫結時，並無特定順序。  
  
    3.  已明確加入，且其相關聯目標部署環境與應用程式匯入所選定的部署環境相符的繫結。 套用此集合中的繫結時，並無特定順序。  
  
-   **群組中必須存在該主機。** BizTalk 群組中必須已經有主控件能夠相對於 .msi 檔案所含應用程式繫結中指定的主控件，否則匯入作業將失敗。 此外，主控件的信任層級也必須相符合。  
  
-   **您可能需要加入另一個應用程式的參考。** 如果要匯入的應用程式與另一個應用程式中的成品相依，則必須新增參考至此應用程式。 群組中必須已經有應用程式和必要的成品。 匯入精靈有提供這個選項。 如果您使用 BTSTask 的 ImportApp 命令，不過，您必須加入參考匯入之後，應用程式中所述[如何加入另一個應用程式的參考](../core/how-to-add-a-reference-to-another-application.md)。 如需背景資訊，請參閱[相依性和應用程式部署](../core/dependencies-and-application-deployment.md)。 匯入精靈會比對群組中現有應用程式的參考，並讓您選擇要新增參考或變更現有的參考。 您應該另外確認參考的應用程式是否包含必要的成品。  
  
-   **如果匯入作業逾時，資料分割到其他.msi 檔案的應用程式。** 匯入作業的持續時間一旦超過 3600 秒就會逾時。 如果您嘗試匯入某個 .msi 檔案而發生作業逾時，請重新匯出應用程式並分批選取所要匯出的部分成品，以將應用程式的內容分成多個 .msi 檔案。 如需詳細資訊，請參閱[如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)。  
  
> [!IMPORTANT]
>  基於安全性考量，應用程式匯出期間將從應用程式繫結移除密碼。 但是，並不是從新增至應用程式的繫結檔案中移除密碼。 匯入應用程式後，您必須重新設定密碼，應用程式才能正常運作。 您可以編輯繫結檔案或使用管理主控台，以完成這項作業。 如需有關編輯繫結檔案的詳細資訊，請參閱[自訂繫結檔案](../core/customizing-binding-files.md)。 如需設定配接器安全性的詳細資訊，請參閱[使用配接器](../core/using-adapters.md)。  
  
> [!NOTE]
>  如果匯入失敗，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]彙回所有匯入作業所自訂的指令碼執行任何動作除外。  
  
> [!NOTE]
>  如果您在一個使用其他應用程式中之屬性結構描述的應用程式內建立傳送埠的篩選，然後再將此應用程式匯入至新的 BizTalk 群組，那麼您在安裝及啟動應用程式時，將不會收到結構描述遺失的警告，並且篩選功能也無法運作。 在安裝沒有包含結構描述的應用程式之前，您可以先匯入包含結構描述的應用程式來修正問題。  
  
## <a name="to-import-a-biztalk-application"></a>匯入 BizTalk 應用程式  
  
#### <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，展開 [BizTalk 群組]，然後執行下列其中一項：  
  
    -   若要匯入的應用程式和成品到 BizTalk 群組包含在.msi 檔案中，以滑鼠右鍵按一下**應用程式**，指向 **匯入**，然後按一下  **MSI 檔案**。  
  
    -   若要匯入到現有的應用程式.msi 檔案中所包含的成品，請展開**應用程式**，應用程式上按一下滑鼠右鍵，指向**匯入**，然後按一下  **的MSI檔案**.  
  
3.  在歡迎使用匯入 MSI 精靈 頁面上，在**要匯入 MSI 檔案**，輸入.msi 檔案的路徑，然後按一下**下一步**。 如果有必要，您可以瀏覽.msi 檔案，即可 **...** 按鈕，可選取色彩。  
  
4.  在應用程式設定 頁面中**應用程式名稱**下拉式清單中，選取應用程式名稱，如果有的話。 當您將應用程式匯入 BizTalk 群組中，就會有此清單。  
  
    > [!NOTE]
    >  清單中包含 BizTalk 群組中目前的所有應用程式名稱，以及匯出 .msi 檔案的應用程式名稱。 如果您選取後面的應用程式名稱，而 BizTalk 群組中還沒有該應用程式，則匯入精靈會建立新的應用程式。 如果您選取群組中已經有的應用程式，則匯入精靈會從 .msi 檔案將成品匯入到現有應用程式中。  
  
5.  在**可用的應用程式將參考加入至**，選取要加入的參考，如果有的話，應用程式，然後按一下**下一步**。  
  
6.  如果您要匯入.msi 檔案到現有的應用程式，並想要覆寫現有的應用程式中的成品，選取**覆寫資源**。  
  
    > [!NOTE]
    >  如果沒有選取此選項，而包含成品的 .msi 檔案已經在應用程式中，則匯入作業即失敗並會進行回復。 BizTalk 應用程式或群組中的某些類型成品必須是唯一的。 如果新增的成品已經在 BizTalk 群組中，卻不在目前應用程式中，即使您指定了覆寫選項，匯入作業將會失敗。 如需有關哪些成品必須是唯一而且必須以何種方式就是唯一的詳細資訊，請參閱[成品，必須是唯一的應用程式或群組](../core/artifacts-that-must-be-unique-in-an-application-or-group.md)。  
  
7.  在 [應用程式目標環境設定] 頁面中**目標執行環境**下拉式清單中，選取之目標環境的這個應用程式，然後按一下**下一步**。 此清單包含針對新增至此應用程式的任何繫結檔案所指定的所有環境。 選取\<預設\>如果您想要套用在應用程式中已指定目標環境以外的所有繫結。 如果.msi 檔案不包含您想要明確套用的繫結檔案，您可以將\<預設\>選取。  
  
    > [!NOTE]
    >  當您將繫結檔案新增至應用程式時，可以指定繫結的目標環境。 如需背景資訊，請參閱[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。 如需新增繫結檔案的指示，請參閱[如何將繫結檔案新增至應用程式](../core/how-to-add-a-binding-file-to-an-application2.md)。  
  
8.  在匯入摘要] 頁面上，確認 [摘要資訊是否正確，，然後按一下**匯入**。  
  
9. 在匯入成功 頁面上，如果您想要在本機電腦上安裝應用程式，選取**執行應用程式安裝精靈在本機電腦上安裝應用程式**核取方塊。  
  
    > [!NOTE]
    >  因為目前已在本機電腦上設定這個選項，所以只有在您要執行應用程式時才會需要進行安裝。 但是，如果應用程式包含檔案架構成品，您必須在將會執行應用程式的所有電腦上安裝應用程式，它才能開始運作，因為匯入應用程式只是將其新增至 BizTalk 管理資料庫中。  
  
10. 按一下 **[完成]**。  
  
> [!NOTE]
>  如果安裝失敗 (例如您沒有本機檔案系統的寫入權限而失敗)，就會回復安裝作業，而非匯入作業。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別`cmd`，然後按一下 **確定**。  
  
2.  輸入下列命令，並以適當的值替代，如下表所述：  
  
     **BTSTask 的 ImportApp /Package:** *值*[**/Environment:***值*] [**/ApplicationName:** *值*] [**/覆寫**] [**/Server:***值*] [**/database:***值*]  
  
     範例：  
  
     **BTSTask 的 ImportApp /Package:"C:\MSI Files\MyApplication.msi"/Environment:Test /applicationname: myapplication / 覆寫**  
  
    |參數|值|  
    |---------------|-----------|  
    |**/ 封裝**|.msi 檔案的完整路徑。 如果路徑包含空格，您必須將它括在引號 (") 中。|  
    |**/ 環境**|所套用之繫結檔案的目標部署環境，例如 Test。 此值係針對已加入應用程式中的繫結檔案指定其目標部署環境。|  
    |**/ 應用程式名稱**|要從 .msi 檔案匯入成品的 BizTalk 應用程式的名稱。 如果沒有指定，將會使用匯入 .msi 檔案時指定的應用程式名稱。 如果指定的應用程式不存在，則會建立該應用程式。 包含空格的應用程式名稱必須以雙引號 (") 圍住。|  
    |**/ 覆寫**|此選項指定以 .msi 檔案中，本機唯一識別碼 (LUID) 相同的成品覆寫應用程式中的成品。 若未指定此選項，且應用程式中有一或多個成品與 .msi 檔案中的成品具有相同的 LUID，匯入就會失敗。 您也可以使用應用程式中檢視之成品的 Luid [ListApp 命令](../core/listapp-command.md)。|  
    |**/ 伺服器**|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
    |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="see-also"></a>請參閱  
 [匯入 BizTalk 應用程式、 繫結和原則](../core/importing-biztalk-applications-bindings-and-policies.md)   
 [ImportApp 命令](../core/importapp-command.md)