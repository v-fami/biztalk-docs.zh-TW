---
title: ExportApp 命令 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6217d0f1-cf39-4520-87c8-8d25b21865af
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 966e53a7c74ce687724a77ea57888a4c61bb2773
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246270"
---
# <a name="exportapp-command"></a>ExportApp 命令
將 BizTalk 應用程式匯出至 .msi 檔案。 若有任何 .msi 檔案位於相同路徑且檔案名稱相同，將會覆寫現有的 .msi 檔案。  
  
 您可以選擇性地使用 ResourceSpec 參數，順便將應用程式中的成品匯出至 .msi 檔案。 您指定當您執行，藉由編輯 XML 檔案匯出哪些成品建立**ListApp**中所述，使用 ResourceSpec 參數，命令[ListApp 命令](../core/listapp-command.md)。 您接著此 XML 檔案的位置在使用 ResourceSpec 的值時執行**ExportApp**命令。 這樣一來，唯有列在該特定 XML 檔案中的成品才會匯出至 .msi 檔案。  
  
> [!NOTE]
>  基於安全性考量，應用程式匯出期間將從應用程式繫結移除密碼。 這些密碼並未從任何已新增至應用程式的繫結檔案中移除。 當您經由 .msi 檔案安裝應用程式後，必須重新設定密碼以使應用程式能夠正常運作。  
>   
>  此外，私密金鑰也將從憑證檔案中移除。  
  
## <a name="usage"></a>使用方式  
 **BTSTask ExportApp** [**/ApplicationName:***值*] **/封裝：***值*[**/ResourceSpec:***值*] [**/GlobalParties**] [**/Server:***值*] [**/資料庫：***值*]  
  
## <a name="parameters"></a>參數  
  
|參數|Required|值|  
|---------------|--------------|-----------|  
|**/ ApplicationName** (或 **/A**，請參閱 < 備註 >)|否|要匯出的 BizTalk 應用程式的名稱。 如果名稱包含空格，您必須將它括在雙引號 (") 中。 若未指定應用程式名稱，將使用群組預設的 BizTalk 應用程式。|  
|**/ 封裝**(或 **/P**，請參閱 < 備註 >)|是|.msi 檔案的完整路徑。 如果路徑包含空格，您必須將它括在引號 (") 中。 範例：Package:"C:\My MSI Files\My.msi"|  
|**/ ResourceSpec** (或 **/R**，請參閱 < 備註 >)|否|資源規格檔案的完整路徑。 如果路徑包含空格，您必須將它括在引號 (") 中。 範例：ResourceSpec:"C:\My Files\MyResourceSpec.xml"|  
|**/ GlobalParties** (或 **/G**，請參閱 < 備註 >)|否|如果有指定，群組的全域合作對象資訊將匯出至 .msi 檔案。|  
|**/ 伺服器**(或 **/S**，請參閱 < 備註 >)|否|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
|**/ 資料庫**(或 **/D**，請參閱 < 備註 >)|否|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="sample"></a>範例  
 **ExportApp /applicationname: myapplication /Package:C:\MSI\MyApplication.msi**  
  
## <a name="remarks"></a>備註  
 參數不區分大小寫。 您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。  
  
## <a name="see-also"></a>另請參閱  
 [BTSTask 命令列參考](../core/btstask-command-line-reference.md)   
 [如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)