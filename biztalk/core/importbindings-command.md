---
title: ImportBindings 命令 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6b8dd1ee-1719-4cd1-b503-b004f312daeb
caps.latest.revision: 25
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 576f9055e7b70ab43cc150f208f8c55789f28da8
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
ms.locfileid: "22257998"
---
# <a name="importbindings-command"></a>ImportBindings 命令
從 XML 格式的繫結檔案匯入繫結至 BizTalk 應用程式或群組。 繫結可能已從匯出的組件、 應用程式或群組中所述[匯出繫結](../core/exporting-bindings6.md)。 根據繫結是從何處匯出而定，ApplicationName 和 GroupLevel 參數的影響將有所不同。 如需詳細資訊，請參閱此主題稍後的「備註」。  
  
> [!NOTE]
>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中產生的繫結檔案均未指定應用程式。 這些檔案將匯入到預設的應用程式。  
  
## <a name="usage"></a>使用方式  
 **BTSTask ImportBindings-來源**:*值* [**-GroupLevel** & #124; **-ApplicationName**:*值*] [**-伺服器**:*值*] [**-資料庫**:*值*] [**-ImportTrackingSettings**:*值*] [**-ExcludeParties**]
  
## <a name="parameters"></a>參數  
  
|參數|必要項|Value|  
|---------------|--------------|-----------|  
|**-來源** (或 **-所以**, ，請參閱 < 備註 >)|必要項|要匯入的繫結檔案完整路徑 (包含檔案名稱)。 路徑如果包含空格，必須括在引號 (") 中。|  
|**-GroupLevel** (或 **-G**, ，請參閱 < 備註 >)|選擇性|此選項指定將繫結檔案匯入到目前的群組。 如果指定此參數，就不能指定 /ApplicationName。|  
|**-ApplicationName** (或 **-**, ，請參閱 < 備註 >)|選擇性|要匯入繫結的 BizTalk 應用程式名稱。 如果名稱包含空格，您必須將它括在雙引號 (") 中。 應用程式必須存在，否則匯入作業將會失敗。 如果沒有指定這個參數，將會使用預設的 BizTalk 應用程式。 如果指定此參數，就不能指定 /GroupLevel。|  
|**伺服器** (或 **-Se**, ，請參閱 < 備註 >)|選擇性|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
|**-資料庫** (或 **-D**, ，請參閱 < 備註 >)|選擇性|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
| **-ImportTrackingSettings** | 選擇性 | 新開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]。 <br /><br />這會覆寫全域追蹤設定匯入選項。 "True"值表示允許追蹤設定匯的入。 False 不允許追蹤設定匯入。 |
| **-ExcludeParties** | 選擇性 | 新開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]。 <br /><br />如果指定，就會從繫結檔案中排除的合作對象資訊。 |
  
## <a name="sample"></a>範例  
 下列命令將繫結匯入到預設的 BizTalk 群組中名為 MyApplication 的應用程式。  
  
`BTSTask ImportBindings -ApplicationName:MyApplication -Source:C:\Bindings\Binding1.xml`
  
 下列命令將繫結匯入到 SQL Server 執行個體 MY_Server 上執行的 BizTalk 管理資料庫中定義的群組。  
  
 `BTSTask ImportBindings -GroupLevel -Server:MY_Server -Database:BiztalkMgmtDb -Source:C:\Bindings\Binding1.xml`
  
## <a name="remarks"></a>備註  
 參數不區分大小寫。 您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。  
  
 繫結原先可能是從組件、應用程式或群組匯出的。 根據繫結是從何處匯出而定，ApplicationName 和 GroupLevel 參數的影響將有所不同，如下表所示。  
  
|繫結的來源|使用 ApplicationName 參數的影響|使用 GroupLevel 參數的影響|  
|----------------------------|-----------------------------------------------|------------------------------------------|  
|從組件匯出繫結|ApplicationName 所指定的應用程式中必須有個組件，其名稱與匯出繫結檔案的來源組件相同。 否則，匯入作業會失敗。|目前的群組中必須有個組件和應用程式，兩者的名稱分別與匯出繫結檔案的來源組件及應用程式相同。 否則，匯入作業會失敗。|  
|從應用程式匯出繫結|匯出繫結檔案的來源應用程式，其名稱必須與 ApplicationName 所指定的應用程式相同。 否則，匯入作業會失敗。|匯出繫結檔案的來源應用程式，其名稱必須與即將匯入繫結的群組中的某個應用程式相同。 否則，匯入作業會失敗。|  
|從群組匯出繫結|匯出繫結檔案的來源群組中必須有個應用程式，其名稱與 ApplicationName 所指定的應用程式相同。 否則，匯入作業會失敗。|會針對對應的應用程式來匯入繫結。 也就是說，匯出繫結的來源群組中，特定應用程式的繫結將會匯入到目前群組中同名的應用程式內。|  
  
## <a name="see-also"></a>另請參閱  
 [BTSTask 命令列參考](../core/btstask-command-line-reference.md)   
 [如何將繫結匯入到 BizTalk 群組](../core/how-to-import-bindings-into-a-biztalk-group.md)   
 [如何將繫結匯入到 BizTalk 應用程式](../core/how-to-import-bindings-into-a-biztalk-application.md)