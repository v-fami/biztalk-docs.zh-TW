---
title: ListApp 命令 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5329dd55-4ce7-46d2-8983-90ac33725055
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 868e1606ae994a39fb8b558cdf2f282be12e5ad4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262494"
---
# <a name="listapp-command"></a>ListApp 命令
將 BizTalk 應用程式中所有資源成品的清單列印至主控台，包括每個成品的本機唯一識別碼 (LUID) 和類型。 資源成品是您可以加入 BizTalk 應用程式使用[AddResource 命令](../core/addresource-command.md)，例如組件、 指令碼、 檔案、 原則、 COM 元件、 虛擬目錄、 BAM 成品，或是憑證。 這些資源成品也會顯示在 BizTalk Server 管理主控台的 [資源] 節點下。  
  
 如果此命令指定 ResourceSpec 參數，相同的資訊便會寫入 .xml 檔案中。 您可以使用這個.xml 檔案**ExportApp**命令中所述，匯出至.msi 檔案，應用程式中的成品的子集[ExportApp 命令](../core/exportapp-command.md)。  
  
 對於虛擬目錄，此命令將以 "localhost" 取代 Web 伺服器主機名稱。 當您使用 ExportApp 命令來處理 ResourceSpec 參數所產生的檔案時，如果 Web 伺服器位於遠端電腦，請先手動編輯檔案並將 "localhost" 改成主機名稱加上連接埠編號。 不然的話，虛擬目錄及其內容將不會納入到應用程式的 .msi 檔案中。  
  
 範例：http://MyWebServer:80/MyVirtualDirectory。  
  
## <a name="usage"></a>使用方式  
 **BTSTask ListApp** [**/ApplicationName:***值*] [**/ResourceSpec:***值*] [**/Server:***值*] [**/database:***值*]  
  
## <a name="parameters"></a>參數  
  
|參數|Required|值|  
|---------------|--------------|-----------|  
|**/ ApplicationName** (或 **/A**，請參閱 < 備註 >)|否|列出其成品的 BizTalk 應用程式的名稱。 如果名稱包含空格，您必須將它括在雙引號 (") 中。  如果沒有指定這個參數，將會使用預設的應用程式。|  
|**/ ResourceSpec** (或 **/R**，請參閱 < 備註 >)|否|要以此命令所產生的 .xml 檔案的完整路徑。 該檔案將會列出應用程式中的成品，以及每個成品的 LUID 和類型。 範例： C:\Artifacts\MyArtifacts.xml。 如果路徑包含空格，就必須將它括在雙引號 （"）。 若有任何檔案位於相同路徑且檔案名稱相同，將會覆寫該檔案。|  
|**/ 伺服器**(或 **/S**，請參閱 < 備註 >)|否|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
|**/ 資料庫**(或 **/D**，請參閱 < 備註 >)|否|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="sample"></a>範例  
 **BTSTask ListApp /applicationname: myapplication /ResourceSpec:C:\Artifacts\MyArtifacts.xml**  
  
## <a name="remarks"></a>備註  
 參數不區分大小寫。 您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。  
  
## <a name="see-also"></a>另請參閱  
 [BTSTask 命令列參考](../core/btstask-command-line-reference.md)