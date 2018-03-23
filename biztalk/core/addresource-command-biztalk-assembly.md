---
title: AddResource 命令： BizTalk 組件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c18607b5-d929-48c9-9fa3-f728a7a80d04
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94cf353abb1e601a14c9e2f081fa2946f1e3ed24
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="addresource-command-biztalk-assembly"></a>AddResource 命令：BizTalk 組件
若要將 BizTalk 組件加入至 BizTalk 應用程式，您使用 **AddResource** 命令並指定 **system.biztalk: biztalkassembly** 做為 Type 參數。 執行此命令會將組件新增至 BizTalk 管理資料庫。 組件也會顯示於 BizTalk Server 管理主控台，列在加入該組件的應用程式的 [資源] 資料夾中。 包含在組件中的成品也會顯示在對應的資料夾裡。 此外，也會列出成品當您使用[ListApp 命令](../core/listapp-command.md)。  
  
 當您使用此命令時，請記住下列重點：  
  
-   如果應用程式中有任何組件，其完整名稱與所加入的組件相同，就必須指定 Overwrite 參數，否則 AddResource 作業將會失敗。 完整名稱是由名稱、公開金鑰 Token、文化特性和版本所組成。 然而，若是其他應用程式相依於該組件，則即使指定 Overwrite 參數，AddResource 作業也將失敗。  
  
-   如果群組中的其他組件具有相同的完整名稱，則即使指定 Overwrite 參數，AddResource 作業也將失敗。  
  
-   如果您要覆寫的組件含有協調流程，執行此命令前必須先停止並取消登錄協調流程。 此外，您也必須停止並取消登錄與協調流程繫結的傳送埠，同時停用接收位置。  
  
-   如果您要加入的組件與未包含在此應用程式中的其他成品具有相依性，AddResource 作業將會失敗。  
  
 如需相依性的詳細資訊，請參閱[相依性和應用程式部署](../core/dependencies-and-application-deployment.md)。  
  
## <a name="usage"></a>使用方式  
 **BTSTask AddResource** [**/ApplicationName:***value*] **/Type:System.BizTalk:BizTalkAssembly** [**/Overwrite**] **/Source:***value* [**/Destination:***value*] [**/Options:GacOnAdd***&#124;***GacOnInstall***&#124;***GacOnImport**] [**/Server:***value*] [**/Database:***value*]  
  
## <a name="parameters"></a>參數  
  
|參數|必要項|Value|  
|---------------|--------------|-----------|  
|**/ ApplicationName** (或 **/A**, ，請參閱 < 備註 >)|否|加入組件之 BizTalk 應用程式的名稱。 如果名稱包含空格，您必須將它括在雙引號 (") 中。 如果沒有指定應用程式名稱，將會使用預設的 BizTalk 應用程式。|  
|**/ 輸入** (或 **/T**, ，請參閱 < 備註 >)|是|**System.biztalk: biztalkassembly** （此值不區分大小寫）。|  
|**/ 覆寫** (或 **/Ov**, ，請參閱 < 備註 >)|否|此選項指定更新現有的組件。 若未指定此選項，且應用程式中現有的組件與所加入的組件具有相同的完整名稱，AddResource 作業將會失敗。 完整名稱對應到組件的本機唯一識別碼 (LUID)。 您也可以使用應用程式中檢視成品的 Luid [ListApp 命令](../core/listapp-command.md)。 如果其他應用程式相依於即將覆寫的組件，則即使指定此參數，AddResource 作業也會失敗。|  
|**/ 來源** (或 **/So**, ，請參閱 < 備註 >)|是|組件檔案的完整路徑 (包含檔案名稱)。 如果路徑包含空格，您必須將它括在雙引號 (") 中。|  
|**/ 目的地** (或 **/De**, ，請參閱 < 備註 >)|否|從 .msi 檔案安裝應用程式時，組件檔案之複製目的位置的完整路徑。 如果不提供，安裝期間就不會將組件檔案複製到本機檔案系統。 如果路徑包含空格，您必須將它括在雙引號 (") 中。 **注意︰**  您可以使用環境變數 %btad_installdir%，BizTalk Server 安裝期間設定，來指定應用程式安裝資料夾。 這樣就能在不同的目的地電腦上，為應用程式的檔案建立完全一致的存放位置。 範例："%BTAD_InstallDir%\MyFiles\Orchestrations.dll"|  
|**/ 選項** (或 **/Op**, ，請參閱 < 備註 >)|否|-   **GacOnAdd**︰ 在 AddResource 作業期間指定的組件安裝至全域組件快取 (GAC) 在本機電腦上。<br />-   **GacOnInstall**︰ 指定從.msi 檔案安裝應用程式時，將組件安裝至 GAC。<br />-   **GacOnImport**︰ 指定匯入應用程式.msi 檔案時，將組件安裝至 GAC。<br /><br /> 您必須以逗點分隔多個選項。|  
|**/ 伺服器** (或 **/Se**, ，請參閱 < 備註 >)|否|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
|**/ 資料庫** (或 **/Da**, ，請參閱 < 備註 >)|否|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="sample"></a>範例  
 **BTSTask AddResource /applicationname: myapplication /Type:System.BizTalk:BizTalkAssembly / 覆寫**  
  
 **/Source:"%BTAD_InstallDir%\Source Assemblies\Orchestrations.dll"/Destination:"%BTAD_InstallDir%\New Assemblies\Orchestrations.dll"/Options:GacOnInstall，GacOnImport /server /Database:BizTalkMgmtDb**  
  
## <a name="remarks"></a>備註  
 參數不區分大小寫。 您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。  
  
## <a name="see-also"></a>另請參閱  
 [AddResource 命令](../core/addresource-command.md)   
 [如何將 BizTalk 組件新增至應用程式](../core/how-to-add-a-biztalk-assembly-to-an-application.md)