---
title: AddResource 命令： COM 元件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 86a4f2fc-bbbe-4b4a-8008-2c79b3ebb6a1
caps.latest.revision: 25
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: febbdc90ce061cd29a191dd15f3bbca9a02bc68e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986375"
---
# <a name="addresource-command-com-component"></a>AddResource 命令：COM 元件
若要將 unmanaged 的 COM 元件新增至 BizTalk 應用程式中，您使用**AddResource**命令，並指定**system.biztalk: com**做為 Type 參數。 執行此命令會將 COM 元件新增至 BizTalk 管理資料庫。 COM 元件也會顯示於 BizTalk 管理主控台，列在加入該元件的應用程式的 [資源] 資料夾中。 當您使用會列出元件的颾魤 ㄛ [ListApp 命令](../core/listapp-command.md)。  
  
> [!NOTE]
>  如果您加入 64 位元的 Unmanaged COM 或 COM+ 元件，而試圖將含有這些 COM 或 COM+ 元件的應用程式安裝於 32 位元電腦，屆時就不會安裝元件。 只能安裝在 64 位元電腦上。  
  
## <a name="usage"></a>使用方式  
 **BTSTask AddResource** [**/ApplicationName:**<em>值</em>] **/Type:System.BizTalk:Com** [**/覆寫**] **/Source:**<em>值</em>[**/Destination:**<em>值</em>] [**/Options:Regsvr32OnInstall**] [**/Server:**<em>值</em>] [**/database:**<em>值</em>]  
  
## <a name="parameters"></a>參數  
  
|參數|必要項|ReplTest1|  
|---------------|--------------|-----------|  
|**/ ApplicationName** (或 **/A**，請參閱 < 備註 >)|否|加入 COM 元件的 BizTalk 應用程式的名稱。 如果名稱包含空格，您必須將它括在雙引號 (") 中。 若未指定應用程式名稱，將使用群組預設的 BizTalk 應用程式。|  
|**/ 鍵入**(或 **/T**，請參閱 < 備註 >)|是|**System.biztalk: com** （此值不區分大小寫）。|  
|**/ 覆寫**(或 **/Ov**，請參閱 < 備註 >)|否|此選項指定更新現有的 COM 元件。 若未指定此選項，且應用程式中現有的 COM 元件與所加入的 COM 元件具有相同的檔案名稱，AddResource 作業將會失敗。|  
|**/Source** (或 **/So**，請參閱 < 備註 >)|是|COM 元件 .dll 檔案的完整路徑 (包含檔案名稱)。 如果路徑包含空格，您必須將它括在雙引號 (") 中。|  
|**/ 目的地**(或 **/De**，請參閱 < 備註 >)|否|從 .msi 檔案安裝應用程式時，COM 元件 .dll 檔案之複製目的位置的完整路徑。 如果不提供，安裝期間就不會將檔案複製到本機檔案系統，以致安裝期間並未將元件寫入 Windows 登錄。 如果路徑包含空格，您必須將它括在雙引號 (") 中。 如果指定了 Regsvr32OnInstallOption，就必須一併指定目的地。|  
|**/ 選項**(或 **/Op**，請參閱 < 備註 >)|否|**Regsvr32OnInstall。** 指定從 .msi 檔案安裝應用程式時，將 COM 元件寫入 Windows 登錄。 如果指定這個選項，您也必須指定目的地。|  
|**/Server** (或 **/Se**，請參閱 < 備註 >)|否|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
|**/ 資料庫**(或 **/Da**，請參閱 < 備註 >)|否|BizTalk 管理資料庫的名稱。 如果不提供，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="sample"></a>範例  
 **BTSTask AddResource /applicationname: myapplication /Type: system.biztalk: com / 覆寫 /Source:"C:\Source Components\COM.dll"/Destination:"C:\New Components\COM.dll"/Options:Regsvr32OnInstall /Server:MyDatabaseServer/資料庫：BizTalkMgmtDb**  
  
## <a name="remarks"></a>備註  
 參數不區分大小寫。 您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。  
  
## <a name="see-also"></a>另請參閱  
 [AddResource 命令](../core/addresource-command.md)   
 [如何將.NET 組件新增至應用程式](../core/how-to-add-a-net-assembly-to-an-application.md)