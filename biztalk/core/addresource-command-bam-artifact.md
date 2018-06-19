---
title: AddResource 命令： BAM 成品 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a9de7a82-9b06-4d50-9678-73140e80d0af
caps.latest.revision: 25
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2753be55fa8cf71b04bbf34d2fdfd8d1190e65e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230398"
---
# <a name="addresource-command-bam-artifact"></a>AddResource 命令：BAM 成品
若要將 BAM 成品新增至 BizTalk 應用程式，您使用**AddResource**命令，並指定**system.biztalk: bam**型別參數。 執行此命令會將 BAM 成品檔案新增至 BizTalk 管理資料庫。 BAM 成品也會顯示在 BizTalk Server 管理主控台中，您要加入它的應用程式的 Resources 資料夾中。 此外，檔案時也將列出您使用[ListApp 命令](../core/listapp-command.md)。  
  
 使用 AddResource 命令加入 BAM 定義時，不會一併部署 BAM 定義。 但是，如果使用「匯入精靈」將含有 BAM 定義的 .msi 檔案匯入應用程式，BAM 定義就會部署至本機電腦。  
  
## <a name="usage"></a>使用方式  
 **BTSTask AddResource** [**/ApplicationName:***值*] **/Type:System.BizTalk:Bam**[**/覆寫**] **/Source:***值*[**/Destination:***值*] [**/Server:** *值*] [**/database:***值*]  
  
## <a name="parameters"></a>參數  
  
|參數|Required|值|  
|---------------|--------------|-----------|  
|**/ ApplicationName** (或 **/A**，請參閱 < 備註 >)|否|加入 BAM 成品的 BizTalk 應用程式的名稱。 如果名稱包含空格，您必須將它括在雙引號 (") 中。 若未指定應用程式名稱，將使用群組預設的 BizTalk 應用程式。|  
|**/ 輸入**(或 **/T**，請參閱 < 備註 >)|是|**System.biztalk: bam** （此值不區分大小寫）。|  
|**/ 覆寫**(或 **/O**，請參閱 < 備註 >)|否|此選項指定更新現有的 BAM 成品。 若未指定此選項，且應用程式中現有的成品與所加入的 BAM 成品同名，AddResource 作業將會失敗。|  
|**/ 來源**(或 **/So**，請參閱 < 備註 >)|是|BAM 成品檔案的完整路徑 (包含檔案名稱)。 如果路徑包含空格，您必須將它括在雙引號 (") 中。|  
|**/ 目的地**(或**De**，請參閱 < 備註 >)|否|從 .msi 檔案安裝應用程式時，BAM 成品檔案之複製目的位置的完整路徑。 如果不提供，安裝期間就不會將檔案複製到本機檔案系統。 如果路徑包含空格，您必須將它括在雙引號 (") 中。|  
|**/ 伺服器**(或 **/Se**，請參閱 < 備註 >)|否|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
|**/ 資料庫**(或 **/Da**，請參閱 < 備註 >)|否|BizTalk 管理資料庫的名稱。 如果不提供，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="sample"></a>範例  
 **BTSTask AddResource /applicationname: myapplication/類型： system.biztalk: bam / 覆寫 /Source:"C:\Source BAMfiles\MyBAMfile.xml"/Destination:"C:\New BAMfiles\MyBAMfile.xml"/Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
## <a name="remarks"></a>備註  
 參數不區分大小寫。 您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。  
  
## <a name="see-also"></a>另請參閱  
 [AddResource 命令](../core/addresource-command.md)   
 [如何將 BAM 成品新增至應用程式](../core/how-to-add-a-bam-artifact-to-an-application.md)