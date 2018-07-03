---
title: AddResource 命令：.NET 組件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef6ec298-35fe-4845-9549-685993d2c659
caps.latest.revision: 25
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2723eb8cf3cff6e90554507b65a2a02c6f8ed1a9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999751"
---
# <a name="addresource-command-net-assembly"></a>AddResource 命令：.NET 組件
若要將.NET 組件 （其中包含 managed 的 COM 或 COM + 元件） 新增至 BizTalk 應用程式中，您使用**AddResource**命令，並指定**system.biztalk: assembly**做為 Type 參數。 執行此命令會將組件新增至 BizTalk 管理資料庫。 組件也會顯示於 BizTalk 管理主控台，列在加入該組件的應用程式的 [資源] 資料夾中。 此外，組件會列出當您使用[ListApp 命令](../core/listapp-command.md)。  
  
 如果組件與應用程式中現有的組件具有相同的完整名稱，您可以指定 Overwrite 參數。 完整名稱是由名稱、公開金鑰 Token、文化特性和版本所組成。 在此情況下會覆寫現有的組件。 如需有關相依性的詳細資訊，請參閱[相依性和應用程式部署](../core/dependencies-and-application-deployment.md)。  
  
## <a name="usage"></a>使用方式  
 **BTSTask AddResource** [**/ApplicationName:**<em>值</em>] **/Type:System.BizTalk:Assembly**[**/覆寫**]**/Source:**<em>值</em>[**/Destination:**<em>值</em>] [**/Options:GacOnAdd**<em>&#124;</em> **GacOnInstall**<em>&#124;</em>**GacOnImport**&#124;**RegasmOnInstall** &#124; **RegsvcsOnInstall**] [**/Server:**<em>值</em>] [**/database:** <em>值</em>]  
  
## <a name="parameters"></a>參數  
  
|參數|必要項|ReplTest1|  
|---------------|--------------|-----------|  
|**/ ApplicationName** (或 **/A**，請參閱 < 備註 >)|否|加入組件之 BizTalk 應用程式的名稱。 如果名稱包含空格，您必須將它括在雙引號 (") 中。 若未指定應用程式名稱，將使用群組預設的 BizTalk 應用程式。|  
|**/ 鍵入**(或 **/T**，請參閱 < 備註 >)|是|**System.biztalk: assembly** （此值不區分大小寫）。|  
|**/ 覆寫**(或 **/Ov**，請參閱 < 備註 >)|否|此選項指定更新現有的組件。 若未指定此選項，且應用程式中現有的組件與所加入的組件具有相同的完整名稱，AddResource 作業將會失敗。 完整名稱是由組件名稱、版本、文化特性和公開金鑰 Token 所組成。 在 BizTalk Server 管理主控台內，這項資訊顯示於應用程式 [資源] 資料夾的 [名稱] 欄位上。|  
|**/Source** (或 **/So**，請參閱 < 備註 >)|是|組件檔案的完整路徑 (包含檔案名稱)。 如果路徑包含空格，您必須將它括在雙引號 (") 中。|  
|**/ 目的地**(或 **/De**，請參閱 < 備註 >)|否|從 .msi 檔案安裝應用程式時，組件檔案之複製目的位置的完整路徑。 如果不提供，安裝期間就不會將組件檔案複製到本機檔案系統。 如果路徑包含空格，您必須將它括在雙引號 (") 中。 如果指定 RegasmOnInstall 或 RegsvcsOnInstall 選項，您也必須指定目的地。 **注意：** 您可以使用 %btad_installdir%環境變數來指定應用程式安裝資料夾。 這樣就能在不同的目的地電腦上，為應用程式的檔案建立完全一致的存放位置。 範例："%BTAD_InstallDir%\MyAssemblies\Orchestrations.dll"|  
|**/ 選項**(或 **/Op**，請參閱 < 備註 >)|否|-   **GacOnAdd**： 在 AddResource 作業期間，在本機電腦上安裝至全域組件快取 (GAC) 組件。<br />-   **GacOnInstall**： 從.msi 檔案安裝應用程式時，會將組件安裝到 GAC。<br />-   **GacOnImport**： 將組件安裝到 GAC，匯入應用程式.msi 檔案時。<br />-   **RegasmOnInstall**： 將 managed 的 COM 組件新增至 Windows 登錄中，從.msi 檔案安裝應用程式。 如果指定這個選項，您也必須指定目的地。<br />-   **RegsvcsOnInstall**： 從.msi 檔案安裝應用程式時，將 managed 的 COM + 組件寫入 Windows 登錄。 如果指定這個選項，您也必須指定目的地。<br /><br /> 您必須以逗點分隔多個選項。 逗點和值之間不能有空格。|  
|**/Server** (或 **/Se**，請參閱 < 備註 >)|否|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
|**/ 資料庫**(或 **/Da**，請參閱 < 備註 >)|否|BizTalk 管理資料庫的名稱。 如果不提供，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="sample"></a>範例  
 **BTSTask AddResource /applicationname: myapplication /Type: system.biztalk: assembly / 覆寫 /Source:"%BTAD_InstallDir%\Source Assemblies\MyAssembly.dll"/Destination:"%BTAD_InstallDir%\New Assemblies\MyAssembly.dll"/Options:GacOnAdd，RegasmOnInstall /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
## <a name="remarks"></a>備註  
 參數不區分大小寫。 您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。  
  
## <a name="see-also"></a>另請參閱  
 [AddResource 命令](../core/addresource-command.md)   
 [如何將.NET 組件新增至應用程式](../core/how-to-add-a-net-assembly-to-an-application.md)