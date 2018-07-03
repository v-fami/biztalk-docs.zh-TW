---
title: AddResource 命令： 虛擬目錄 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 446be3b3-31da-4f03-81b5-3a75c8da6558
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 364926e00f8d29fbce567a21d09265dee98a4e0f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993143"
---
# <a name="addresource-command-virtual-directory"></a>AddResource 命令：虛擬目錄
若要將網站或 Web 服務的虛擬目錄新增至 BizTalk 應用程式中，您使用**AddResource**命令，並指定**system.biztalk: webdirectory**做為 Type 參數。 執行此命令會將虛擬目錄新增至 BizTalk 管理資料庫。 虛擬目錄也會顯示於 BizTalk Server 管理主控台，列在加入該虛擬目錄的應用程式的 [資源] 資料夾中。 此外，虛擬目錄會列出當您使用[ListApp 命令](../core/listapp-command.md)。  
  
> [!IMPORTANT]
>  如果您要加入之虛擬目錄的 URL 包含 https，指定 URL 時必須改用 http 代替 https。 若是使用 https，虛擬目錄加入作業將會失敗。 雖然您在 URL 中使用 http 來加入，Internet Information Services Metabase 仍會沿用 URL 的 https 設定使之生效，因此虛擬目錄將可正常運作。  
  
> [!NOTE]
>  如果您所加入的虛擬目錄來自 64 位元版的 Web 服務，而您試圖將含有該虛擬目錄的應用程式安裝於 32 位元電腦，屆時將不會安裝該虛擬目錄。 它會安裝在 64 位元的電腦上。  
  
## <a name="usage"></a>使用方式  
 **BTSTask AddResource** [/**ApplicationName:**<em>值</em>] **/Type:System.BizTalk:WebDirectory**[**/覆寫**]**/Source:**<em>值</em>[**/Destination:**<em>值</em>] [**/Server:** <em>值</em>] [**/database:**<em>值</em>]  
  
## <a name="parameters"></a>參數  
  
|                   參數                   | 必要項 |                                                                                                                                                                                                                                                         ReplTest1                                                                                                                                                                                                                                                          |
|-----------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **/ ApplicationName** (或 **/A**，請參閱 < 備註 >) |    否    |                                                                                                                                加入虛擬目錄的 BizTalk 應用程式名稱。 如果名稱包含空格，您必須將它括在雙引號 (") 中。 若未指定應用程式名稱，將使用群組預設的 BizTalk 應用程式。                                                                                                                                 |
|      **/ 鍵入**(或 **/T**，請參閱 < 備註 >)       |   是    |                                                                                                                                                                                                                          **System.biztalk: webdirectory** （此值不區分大小寫）。                                                                                                                                                                                                                           |
|    **/ 覆寫**(或 **/O**，請參閱 < 備註 >)    |    否    |                                                                                                                                               更新現有虛擬目錄的選項。 若未指定此選項，且應用程式中現有的虛擬目錄與所加入的虛擬目錄同名，AddResource 作業將會失敗。                                                                                                                                                |
|     **/Source** (或 **/S**，請參閱 < 備註 >)      |   是    |                                                                                                                                                                                                 來源虛擬目錄的完整 URI。<br /><br /> 範例:<br /><br /> http://MyHost:80/MyPath/MyVirtualDirectory                                                                                                                                                                                                 |
|  **/ 目的地**(或 **/De**，請參閱 < 備註 >)   |    否    |                                                                                                                                                    從 .msi 檔案安裝應用程式時，指派給虛擬目錄的 URI。 若未指定此參數，將使用 Source 參數的值並以 localhost 做為主控件。                                                                                                                                                    |
|     **/Server** (或 **/S**，請參閱 < 備註 >)      |    否    | 裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。 |
|    **/ 資料庫**(或 **/Da**，請參閱 < 備註 >)    |    否    |                                                                                                                                                                                     BizTalk 管理資料庫的名稱。 如果不提供，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。                                                                                                                                                                                     |
  
## <a name="sample"></a>範例  
 **BTSTask AddResource /applicationname: myapplication /Type: system.biztalk: webdirectory / 覆寫 /Source:<http://Host1:90/MyVirtualDirectory> /Destination:<http://Host2:90/MyVirtualDirectory> /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
## <a name="remarks"></a>備註  
 參數不區分大小寫。 您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。  
  
## <a name="see-also"></a>另請參閱  
 [AddResource 命令](../core/addresource-command.md)   
 [如何將.NET 組件新增至應用程式](../core/how-to-add-a-net-assembly-to-an-application.md)