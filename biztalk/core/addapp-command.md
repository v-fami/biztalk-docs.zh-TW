---
title: AddApp 命令 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 445784f1-505b-4259-a3f4-6f0d61578b1c
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a6b91faa406181db3e4195bf57baeb086a0b69e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22229998"
---
# <a name="addapp-command"></a>AddApp 命令
在 BizTalk 管理資料庫中建立新的 BizTalk 應用程式。 您可以在 BizTalk Server 管理主控台的 [應用程式] 節點下檢視應用程式。 您可以將成品新增至應用程式使用 AddResource 命令中所述[AddResource 命令](../core/addresource-command.md)。  
  
## <a name="usage"></a>使用方式  
 **BTSTask AddApp /ApplicationName:** *值*[**/Description:***值*] [**/預設**] [**/伺服器：***值*] [**/database:***值*]  
  
## <a name="parameters"></a>參數  
  
|參數|Required|值|  
|---------------|--------------|-----------|  
|**/ ApplicationName** (或 **/A**，請參閱 < 備註 >)|是|若要加入的 BizTalk 應用程式的名稱。 如果應用程式名稱包含空格，則它必須括在雙引號 （"）。|  
|**/ 預設**(或 **/Def**，請參閱 < 備註 >)|否|如果有指定，新應用程式將成為 BizTalk 群組預設的應用程式。|  
|**/ 描述**(或 **/Des**，請參閱 < 備註 >)|否|應用程式的說明。 必須括在雙引號 (") 中。|  
|**/ 伺服器**(或 **/S**，請參閱 < 備註 >)|否|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
|**/ 資料庫**(或 **/Da**，請參閱 < 備註 >)|否|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="sample"></a>範例  
 **AddApp /applicationname: myapplication /Description: 「 我的 BizTalk 應用程式 」**  
  
## <a name="remarks"></a>備註  
 參數不區分大小寫。 您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。  
  
## <a name="see-also"></a>另請參閱  
 [BTSTask 命令列參考](../core/btstask-command-line-reference.md)   
 [如何建立應用程式](../core/how-to-create-an-application.md)