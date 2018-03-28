---
title: 如何匯入原則 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- policies, requirements
- importing, policies
- policies, importing
- managing [policies], importing
ms.assetid: 92f6ef18-279f-416d-b13e-8b9642539d27
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac21ad1348dbc934c81d87f3c477977eeecd2ccf
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-import-a-policy"></a>如何匯入原則
本主題描述如何使用 [BizTalk Server 管理] 主控台將原則匯入到 BizTalk 群組，或是使用 BTSTask 命令列工具將原則匯入到 BizTalk 應用程式。  
  
 中所述，您可以使用 「 商務規則編輯器 」 中，建立原則[使用商務規則編輯器建立商務規則](../core/creating-business-rules-using-the-business-rule-composer.md)，並將它匯入直接或中所述，您可以從另一個 BizTalk 群組，匯出原則[如何匯出原則](../core/how-to-export-a-policy.md)然後匯入。  
  
 匯入原則會將它登錄在 BizTalk 群組的「規則引擎」資料庫中。 在您匯入原則之後，可以在 [BizTalk Server 管理] 主控台中檢視它。 如果您使用 BizTalk Server 管理主控台來匯入原則時，它會顯示在\<所有成品\>BizTalk 群組 節點。 您可以再發行，使它可以將它新增至 BizTalk 應用程式中所述[如何發佈原則](../core/how-to-publish-a-policy.md)。 如果您使用 BTSTask 命令列工具來匯入原則，將會自動發佈該原則，而且它會顯示在匯入所在之應用程式的原則資料夾內。  
  
 匯入原則時，請牢記下列要點：  
  
-   即使您指定了要以匯入的原則覆寫現有原則的選項，您還是無法匯入此群組的規則引擎資料庫中已經存在且已經部署的原則。 在此情況下，匯入作業會失敗。  
  
-   即使當從另一個 BizTalk 群組匯出此原則時，它是已部署的狀態，但是將它匯入時，它就會變成解除部署的狀態。  
  
-   BTSTask 沒有提供匯入原則的特定命令，不過您可以使用 BTSTask 的 ExportApp 命令來選擇只匯出應用程式中所需要的原則，而不包括其他的應用程式成品。 然後，您可以使用 ImportApp 命令將 .msi 檔案匯入到不同 BizTalk 群組的應用程式中。 這就是本主題所描述的方法。 當您進行這項處理時，此原則會自動匯入，並在 BizTalk 群組中發佈，然後新增至指定的應用程式。  
  
 如需使用原則的詳細資訊，請參閱[管理原則](../core/managing-policies.md)。 如需新增原則至應用程式的最佳作法，請參閱[部署 BizTalk 應用程式的最佳作法](../core/best-practices-for-deploying-a-biztalk-application.md)。  
  
> [!NOTE]
>  方案開發人員可以建立原則，然後匯入規則引擎資料庫群組使用 「 規則引擎部署精靈 」 中所述[如何部署和解除部署原則和詞彙](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md)。  
  
## <a name="prerequisites"></a>必要條件  
 下列是執行本主題所述程序的必要條件：  
  
-   您必須以 BizTalk Server Administrators 群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
-   必須安裝「商務規則引擎」。 如需詳細資訊，請參閱[BizTalk Server 2013 和 2013 R2 的安裝概觀](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)。  
  
-   如果您想要使用 [BizTalk Server 管理] 主控台來匯入原則，您必須有一個可用的 .xml 檔案，且其中包含您想要匯入的原則。 中所述，您可以藉由將原則匯出從另一個 BizTalk 群組或應用程式，產生這類.xml 檔案[如何匯出原則](../core/how-to-export-a-policy.md)，或使用 「 商務規則編輯器 」 中，如下所示[如何匯入和匯出原則和詞彙](../core/how-to-import-and-export-policies-and-vocabularies.md)。  
  
-   如果您想要使用 BTSTask 來匯入原則，您必須有一個 .msi 檔案，且其中包含您想要匯入的原則。 如需指示，請參閱[如何匯出原則](../core/how-to-export-a-policy.md)。  
  
## <a name="to-import-a-policy"></a>匯入原則  
  
#### <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台  
  
1.  按一下  **啟動**, ，按一下  **所有程式**, ，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], ，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，要匯入原則，請依序展開 BizTalk 群組**應用程式**，然後展開**\<所有成品\>**.  
  
3.  以滑鼠右鍵按一下 **原則**, ，然後按一下  **匯入**。  
  
4.  瀏覽至原則，然後按一下包含.xml 檔案 **開啟**。  
  
     原則匯入的群組，並顯示在**原則**資料夾**\<所有成品\>**。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1.  開啟命令提示字元，如下所示︰ 按一下 **啟動**, ，按一下  **執行**, ，型別 `cmd`, ，然後按一下  **確定**。  
  
2.  輸入下列命令，並以適當的值替代，如下表所述：  
  
     **BTSTask 的 ImportApp /Package:** *值*[**/ApplicationName: * **值*] [**/覆寫**] [**/Server:***值 *] [* * / d a t:***值 *]  
  
     範例：  
  
     **BTSTask 的 ImportApp /Package: 「 C:\MSI Files\MyApplication.msi"/Environment:Test /applicationname: myapplication / 覆寫**  
  
    |參數|Value|  
    |---------------|-----------|  
    |**/ 封裝**|包含要匯入之原則的 .msi 檔案的完整路徑。 如果路徑包含空格，您必須將它括在引號 (") 中。|  
    |**/ 應用程式名稱**|要將原則匯入其中的 BizTalk 應用程式名稱。 如果沒有指定，將會使用匯入 .msi 檔案時指定的應用程式名稱。 如果指定的應用程式不存在，則會建立該應用程式。 包含空格的應用程式名稱必須以雙引號 (") 圍住。|  
    |**/ 覆寫**|以 .msi 檔案中具有相同名稱和版本號碼的成品來覆寫應用程式中之原則的選項。 若未指定此選項，且應用程式中有一或多個原則與 .msi 檔案中的原則具有相同的名稱和版本號碼，匯入就會失敗。 您也可以使用應用程式中檢視原則的名稱和版本號碼[ListApp 命令](../core/listapp-command.md)。|  
    |**/ 伺服器**|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
    |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。 若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取 **系統管理員身分執行**。  
  
## <a name="see-also"></a>另請參閱  
 [匯入 BizTalk 應用程式、 繫結和原則](../core/importing-biztalk-applications-bindings-and-policies.md)   
 [匯出 BizTalk 應用程式、 繫結和原則](../core/exporting-biztalk-applications-bindings-and-policies.md)   
 [管理原則](../core/managing-policies.md)