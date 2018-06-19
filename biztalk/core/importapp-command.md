---
title: ImportApp 命令 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8ee5a78-1e8f-4290-b70a-36f2f888a1d6
caps.latest.revision: 28
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4200b5559ddfc12597c95d0e924a0159665f5f0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257870"
---
# <a name="importapp-command"></a>ImportApp 命令
將 .msi 檔案中所包含的成品匯入 BizTalk 應用程式中。 如果應用程式不存在，會予以建立。  
  
 若您曾在應用程式中加入繫結檔案，以針對特定的部署環境進行自訂，則匯入應用程式時即可使用 /Environment 參數指定應用程式的目標部署環境。 如需背景資訊，請參閱[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。 如需新增繫結檔案的指示，請參閱[AddResource 命令： BizTalk 繫結](../core/addresource-command-biztalk-binding.md)。  
  
> [!NOTE]
>  匯入作業的持續時間一旦超過 3600 秒就會逾時。 如果您嘗試匯入某個 .msi 檔案而發生作業逾時，請重新匯出應用程式並分批選取所要匯出的部分成品，以將應用程式的內容分成多個 .msi 檔案。 如需詳細資訊，請參閱[如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)。  
  
 如果匯入失敗，BTSTask 就會傳回顯示錯誤數目。 作業期間執行的大多數動作都會回復，唯獨下列情況例外：  
  
-   自訂指令碼執行的動作不會回復。 您可以使用 Delete 環境變數撰寫可回復動作的指令碼。  
  
-   安裝在全域組件快取 (GAC) 中的組件不會被移除。  
  
-   Windows 登錄中的增修項目不會被移除。  
  
 如果匯入成功，BTSTask 就會傳回"0"。  
  
## <a name="usage"></a>使用方式  
 **BTSTask 的 ImportApp /Package:** *值*[**/Environment:***值*] [**/ApplicationName:** *值*] [**/覆寫**] [**/Server:***值*] [**/database:***值*]  
  
## <a name="parameters"></a>參數  
  
|參數|Required|值|  
|---------------|--------------|-----------|  
|**/ 封裝**(或 **/P**，請參閱 < 備註 >)|是|.msi 檔案的完整路徑。 如果路徑包含空格，您必須將它括在雙引號 (") 中。 範例："C:\My MSI Files\MyApplication.msi"|  
|**/ 環境**(或 **/E**，請參閱 < 備註 >)|否|所套用之繫結檔案的目標部署環境，例如 Test。 此值係針對已加入應用程式中的繫結檔案指定其目標部署環境。 如果沒有指定，將會套用所有未指定部署環境的繫結。|  
|**/ ApplicationName** (或 **/A**，請參閱 < 備註 >)|否|要從 .msi 檔案匯入成品的 BizTalk 應用程式的名稱。 如果名稱包含空格，您必須將它括在雙引號 (") 中。 如果沒有指定，將會使用預設的應用程式。 如果指定的應用程式不存在，會自動建立應用程式。|  
|**/ 覆寫**(或 **/O**，請參閱 < 備註 >)|否|此選項指定以 .msi 檔案中，本機唯一識別碼 (LUID) 相同的成品覆寫應用程式中的成品。 您也可以使用應用程式中檢視之成品的 Luid [ListApp 命令](../core/listapp-command.md)。 若未指定此選項，且應用程式中有一或多個成品與 .msi 檔案中的成品具有相同的 LUID，匯入就會失敗。|  
|**/ 伺服器**(或 **/S**，請參閱 < 備註 >)|否|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
|**/ 資料庫**(或 **/D**，請參閱 < 備註 >)|否|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="sample"></a>範例  
 **BTSTask 的 ImportApp /Package:C:\MSI\MyApplication.msi /Environment:Test /applicationname: myapplication / 覆寫**  
  
## <a name="remarks"></a>備註  
 參數不區分大小寫。 您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。  
  
## <a name="see-also"></a>另請參閱  
 [BTSTask 命令列參考](../core/btstask-command-line-reference.md)   
 [如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)