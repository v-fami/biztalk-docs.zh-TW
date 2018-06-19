---
title: AddResource 命令： 檔案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e9635e43-af26-48d3-af0e-df245a8955e7
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 92ed0b99c942adbb63fd7ca3bd2e29cc1ba040c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230302"
---
# <a name="addresource-command-file"></a>AddResource 命令：檔案
若要將檔案加入至 BizTalk 應用程式，您使用**AddResource**命令，並指定**system.biztalk: file**型別參數。 執行此命令會將檔案新增至 BizTalk 管理資料庫。 檔案也會顯示於 BizTalk 管理主控台，列在加入該檔案的應用程式的 [資源] 資料夾中。 此外，檔案時也將列出您使用[ListApp 命令](../core/listapp-command.md)。  
  
## <a name="usage"></a>使用方式  
 **BTSTask AddResource** [**/ApplicationName:***值*] **/Type:System.BizTalk:File** [**/覆寫**] **/Source:***值*[**/Destination:***值*] [**/Server:** *值*] [**/database:***值*]  
  
## <a name="parameters"></a>參數  
  
|參數|Required|值|  
|---------------|--------------|-----------|  
|**/ ApplicationName** (或 **/A**，請參閱 < 備註 >)|否|加入檔案的 BizTalk 應用程式的名稱。 如果路徑包含空格，您必須將它括在雙引號 (") 中。 如果沒有指定應用程式名稱，將會使用預設的 BizTalk 應用程式。|  
|**/ 輸入**(或 **/T**，請參閱 < 備註 >)|是|**System.biztalk: file** （此值不區分大小寫）。|  
|**/ 覆寫**(或 **/O**，請參閱 < 備註 >)|否|此選項指定更新現有的檔案。 若未指定此選項，且應用程式中現有的檔案與所加入的檔案同名，AddResource 作業將會失敗。|  
|**/ 來源**(或 **/So**，請參閱 < 備註 >)|是|檔案的完整路徑 (包含檔案名稱)。 如果路徑包含空格，您必須將它括在雙引號 (") 中。|  
|**/ 目的地**(或**De**，請參閱 < 備註 >)|否|從 .msi 檔案安裝應用程式時，檔案之複製目的位置的完整路徑。 如果路徑包含空格，您必須將它括在雙引號 (") 中。 如果不提供，安裝期間就不會將檔案複製到本機檔案系統。|  
|**/ 伺服器**(或 **/Se**，請參閱 < 備註 >)|否|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
|**/ 資料庫**(或 **/Da**，請參閱 < 備註 >)|否|BizTalk 管理資料庫的名稱。 如果不提供，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="sample"></a>範例  
 **BTSTask AddResource /applicationname: myapplication/類型： system.biztalk: file / 覆寫 /Source:"C:\Source Files\File.txt"/Destination:"C:\New Files\File.txt"/Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
## <a name="remarks"></a>備註  
 參數不區分大小寫。 您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。  
  
## <a name="see-also"></a>另請參閱  
 [AddResource 命令](../core/addresource-command.md)   
 [如何將.NET 組件新增至應用程式](../core/how-to-add-a-net-assembly-to-an-application.md)