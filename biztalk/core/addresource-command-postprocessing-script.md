---
title: AddResource 命令： 後置處理指令碼 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7d6d1622-1c90-4059-903e-68dcab829744
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 434083206fb27646c90e4f1881d3099a995ffb0b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230862"
---
# <a name="addresource-command-postprocessing-script"></a>AddResource 命令：後置處理指令碼
若要將後置處理指令碼加入至 BizTalk 應用程式，您使用**AddResource**命令，並指定**system.biztalk: postprocessingscript**型別參數。 執行此命令會將指令碼檔案新增至 BizTalk 管理資料庫。 指令碼檔案也會顯示於 BizTalk 管理主控台，列在加入該指令碼檔案的應用程式的 [資源] 資料夾中。 此外，檔案時也將列出您使用[ListApp 命令](../core/listapp-command.md)。  
  
 後置處理指令碼是在應用程式匯入或安裝後，或在應用程式解除安裝前，從 .msi 檔案執行的。 您也可以使用 BTSTask 加入前置處理指令碼，如中所述，執行應用程式匯入或安裝前，或解除安裝之後， [AddResource 命令： 前置處理指令碼](../core/addresource-command-preprocessing-script.md)。 如需有關前置處理和後置處理指令碼的詳細資訊，請參閱[使用前置和後置處理指令碼，以自訂應用程式部署](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)。  
  
## <a name="usage"></a>使用方式  
 **BTSTask AddResource** [**/ApplicationName:***值*] **/Type:System.BizTalk:PostProcessingScript**[**/Overwrite**]**/Source:***值*[**/Destination:***值*] [**/Server:** *值*] [**/database:***值*] [**/Property:Args ="***引數清單***"**]  
  
## <a name="parameters"></a>參數  
  
|參數|Required|值|  
|---------------|--------------|-----------|  
|**/ ApplicationName** (或 **/A**，請參閱 < 備註 >)|否|加入指令碼之 BizTalk 應用程式的名稱。 如果名稱包含空格，您必須將它括在雙引號 (") 中。 若未指定應用程式名稱，將使用群組預設的 BizTalk 應用程式。|  
|**/ 輸入**(或 **/T**，請參閱 < 備註 >)|是|**System.biztalk: postprocessingscript** （此值不區分大小寫）。|  
|**/ 覆寫**(或 **/O**，請參閱 < 備註 >)|否|此選項指定更新現有的指令碼。 若未指定此選項，且應用程式中現有的指令碼檔案與所加入的指令碼檔案同名，加入作業將會失敗。|  
|**/ 來源**(或 **/So**，請參閱 < 備註 >)|是|指令碼檔案的完整路徑 (包含檔案名稱)。 如果路徑包含空格，您必須將它括在雙引號 (") 中。|  
|**/ 目的地**(或 **/De**，請參閱 < 備註 >)|否|從 .msi 檔案安裝應用程式時，指令碼檔案之複製目的位置的完整路徑。 如果不提供，安裝期間就不會將檔案複製到本機檔案系統。 如果這個指令碼預定會在應用程式解除安裝期間執行，您應該指定目的地；否則，指令碼不會放在本機檔案系統中，並且無法在解除安裝期間執行。 如果路徑包含空格，您必須將它括在雙引號 (") 中。|  
|**/ 伺服器**(或 **/Se**，請參閱 < 備註 >)|否|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
|**/ 資料庫**(或 **/Da**，請參閱 < 備註 >)|否|BizTalk 管理資料庫的名稱。 如果不提供，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
|**/ 屬性**(或 **/P**，請參閱 < 備註 >)|否|零個或多個資源屬性，可在叫用指令碼時做為引數傳遞給指令碼。|  
  
## <a name="sample"></a>範例  
 **BTSTask AddResource /applicationname: myapplication/類型： system.biztalk: postprocessingscript / 覆寫 /Source:"C:\Source Scripts\MyScript.vbs"/Destination:"C:\New Scripts\MyScript.vbs"/Server:MyDatabaseServer/資料庫：BizTalkMgmtDb /Property:Args ="引數 1 引數 2"**  
  
## <a name="remarks"></a>備註  
 參數不區分大小寫。 您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。  
  
 指令碼檔案支援下列副檔名：.com、.exe、.bat、.cmd、.vbs、.vbe、.js、.jse、.wsf、.wsh。  
  
## <a name="see-also"></a>另請參閱  
 [AddResource 命令](../core/addresource-command.md)   
 [如何新增前置或後置處理指令碼至應用程式](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md)