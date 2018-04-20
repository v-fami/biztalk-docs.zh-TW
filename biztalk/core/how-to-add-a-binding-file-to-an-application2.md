---
title: 應用程式中加入繫結檔案 |Microsoft 文件
description: 新增繫結檔案，使用 BizTalk Server 管理，或使用 BizTalk Server 中的 命令提示字元
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1543ee5f-9ae4-4683-b6fe-ee84028c381d
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f6d2a999be4a12860616bc92f3086b37dbd265f
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="add-a-binding-file-to-an-application"></a>應用程式中加入繫結檔案

## <a name="overview"></a>概觀
將繫結檔案新增至 BizTalk 應用程式中使用 BizTalk Server 管理主控台或命令列。 您可能想要這樣做可以讓應用程式或組件的部署更容易中所述[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。  
  
 中所述，您可以從 BizTalk 應用程式的組件、 應用程式或群組匯出繫結匯出到.xml 檔案[匯出繫結](../core/exporting-bindings6.md)，然後使用本主題中的其中一個程序將繫結檔案新增至應用程式。  
  
 這麼做之後，繫結檔案便會新增至 BizTalk 管理資料庫，也會顯示於 BizTalk Server 管理主控台，列在應用程式的 [資源] 資料夾中。 與匯入繫結檔案不同，新增繫結檔案不會立即套用其繫結， 而是在應用程式匯入到其他 BizTalk 群組時，才會套用繫結。  
  
> [!IMPORTANT]
>  基於安全性理由，當您匯出繫結時，BizTalk Server 會從該檔案移除繫結的密碼。 匯入繫結後，您必須重新設定密碼，傳送埠和接受位置才能正常運作。 BizTalk Server 관리 콘솔의 전송 속성 대화 상자에서 송신 포트나 수신 위치의 암호를 구성합니다. 請參閱[建立傳送埠](../core/how-to-create-a-send-port2.md)或[建立接收位置](../core/how-to-create-a-receive-location.md)。  
  
> [!NOTE]
>  當您使用的繫結檔案時，您應該驗證成品，已繫結至正確的主控件和信任層級是適當。  
  
 當您新增繫結檔案至應用程式時，您可以使用代表環境 (例如「測試」或「實際執行」) 的字串指定目標部署環境的值。 您可以使用任意字串表示此值。 然後，當您匯入應用程式時，就可以藉由提供指定其目標部署環境的值，選取要套用的繫結檔案。 這麼做之後，便會從繫結檔案套用繫結。 該檔案中與應用程式現有繫結同名的繫結，將會自動覆寫現有的繫結。  
  
 當您匯入應用程式時，將依下列順序套用繫結。 由於繫結是在匯入過程中套用，新的繫結會覆寫先前已套用的同名繫結。 也就是說，同名的繫結當中最後套用的繫結將會生效。  
  
1.  並非透過繫結檔案明確加入至應用程式，而是使用者明確選定欲匯出至應用程式 .msi 檔案的應用程式繫結 (由 BizTalk Server 所產生)。  
  
2.  已明確加入，但未指定目標部署環境的繫結檔案。 套用此集合中的繫結時，並無特定順序。  
  
3.  已明確加入，且其相關聯目標部署環境與應用程式匯入所選定的部署環境相符的繫結。 套用此集合中的繫結時，並無特定順序。  
  
 如需有關匯入應用程式及套用繫結的詳細資訊，請參閱[匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。  
  
## <a name="prerequisites"></a>필수 구성 요소  
使用 BizTalk Server 系統管理員群組的成員帳戶登入。 [部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)提供更多詳細資料。
  
## <a name="add-a-binding-file-using-biztalk-administration"></a>新增繫結檔案，使用 BizTalk 管理  
  
1.  開啟**BizTalk Server 管理**（在 [開始] 功能表中）。
  
2.  展開 BizTalk Server 管理、 BizTalk 群組、 展開 應用程式，和以滑鼠右鍵按一下您要新增繫結檔案的應用程式。  
  
3.  指向 **新增**, ，然後按一下  **資源**。  
  
4.  按一下  **新增**, ，選取要新增，然後再按檔案 **開啟**。  
  
5.  若要覆寫現有的繫結檔案中有相同的檔案名稱，此應用程式，請選取 **覆寫所有** 核取方塊。 如果有另一個同名的檔案存在，而您未選取此核取方塊，新增作業就會失敗。  
  
6.  在 **檔案類型** 下拉式清單中，選取 **system.biztalk: biztalkbinding**。  
  
7.  在 **目標環境**, ，輸入一個字串，代表您想要套用，例如測試，然後按一下此檔案中的繫結的目標部署環境 **確定**。  
  
    > [!IMPORTANT]
    >  如果讓這個欄位空白，則每當匯入應用程式時，就會套用這個檔案中的繫結。  
  
     新增繫結檔案之後，它會顯示在應用程式的 [資源] 資料夾中。  
  
## <a name="add-a-binding-file-using-the-command-line"></a>新增繫結檔案，使用命令列  
  
1.  開啟命令提示字元 (**啟動**功能表 > 輸入`cmd`> 選取**命令提示字元**)。  
  
2.  輸入下列命令，並以適當的值替代，如下表所述：  
  
     **BTSTask AddResource** [**/ApplicationName:"***值***"**] **/Type:System.BizTalk:BizTalkBinding** [**/Overwrite**] **/Source:***值***/Property:TargetEnvironment="***值***"** [**/Server:***值*][**/:***值*]  
  
     範例：  
  
     **BTSTask AddResource /ApplicationName: 「 我的應用程式 」 /type /Source:"C:\Binding Files\MyBinding.xml"/property: targetenvironment ="Production"/server /Database:BizTalkMgmtDb**  
  
    |參數|Value|  
    |---------------|-----------|  
    |**/ 應用程式名稱**|加入繫結檔案的 BizTalk 應用程式的名稱。 如果沒有指定應用程式名稱，將會使用預設的 BizTalk 應用程式。 如果名稱包含空格，您必須將它括在雙引號 (") 中。|  
    |**/ 型別**|**System.biztalk: biztalkbinding** （此值不區分大小寫）。|  
    |**/ 覆寫**|此選項指定更新現有的繫結檔案。 若未指定此選項，且應用程式中現有的繫結檔案與所加入的繫結檔案同名，AddResource 作業將會失敗。|  
    |**/ 來源**|繫結檔案的完整路徑 (包含檔案名稱)。 如果路徑包含空格，您必須將它括在雙引號 (") 中。|  
    |**/Property: targetenvironment =**|用於指定目標部署環境的字串。 您可以使用任意字串，例如「實際執行」。 範例︰ **/property: targetenvironment = 「 生產 」**<br /><br /> 如果未指定值為\<預設\>自動套用。 此值區分大小寫。 如果參數值包含空格，您必須將它括在雙引號 (") 中。 環境值的長度上限為 128 個字元。|  
    |**/ 伺服器**|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
    |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="see-also"></a>另請參閱  
 [管理.NET 組件、 憑證和其他資源](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [AddResource 命令： BizTalk 繫結](../core/addresource-command-biztalk-binding.md)   
 [建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)