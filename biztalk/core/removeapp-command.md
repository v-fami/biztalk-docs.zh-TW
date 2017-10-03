---
title: "RemoveApp 命令 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 323290ae-8498-4ad6-9b06-a1d54640250e
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9808b43ba07434793403d175885694f67530dae0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="removeapp-command"></a>RemoveApp 命令
從 BizTalk 管理資料庫移除 (刪除) BizTalk 應用程式，以及包含在該應用程式中的所有成品。 這並不會解除安裝應用程式。 如需有關執行此操作的指示，請參閱[如何解除安裝 BizTalk 應用程式](../core/how-to-uninstall-a-biztalk-application.md)。  
  
 在下列情況中，移除作業將會失敗：  
  
-   **無法停止應用程式。** 如需停止應用程式的指示，請參閱[如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)。 **ApplicationManager** sdk > 範例的安裝中*\<範例路徑 >\\*Admin\ExplorerOM\ 目錄說明如何以程式設計方式啟動或停止[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式。  
  
-   **其他應用程式包含應用程式的參考。** 如果其他應用程式含有對此即將移除之應用程式的參考，您必須先從其他應用程式移除這些參考。 如需指示，請參閱[如何移除另一個應用程式的參考](../core/how-to-remove-a-reference-to-another-application.md)。  
  
-   **應用程式包含另一個應用程式中的傳送埠是成員的傳送埠群組。** 您必須取消登錄該成員傳送埠，然後才能刪除應用程式。 如需指示，請參閱[如何取消登錄傳送埠或傳送埠群組](../core/how-to-unenlist-a-send-port-or-send-port-group.md)。  
  
-   **應用程式包含合作對象所參考的傳送埠。** 您可以刪除該合作對象所做的參考，或將傳送埠移至其他應用程式。 如需執行這些工作的指示，請參閱[如何檢視或編輯合作對象](http://msdn.microsoft.com/library/42e6f3a0-8f7d-4f6c-ab05-a1fab7bf46ca)或[如何將成品移至不同的應用程式](../core/how-to-move-an-artifact-to-a-different-application.md)。  
  
-   **是預設應用程式。** 如果您要將其刪除，必須先指定其他應用程式做為預設應用程式。 如需指示，請參閱[如何變更預設的應用程式](../core/how-to-change-the-default-application.md)。  
  
-   **應用程式中的協調流程已登錄 」，「 已啟動，或已擱置的執行個體。** 如需協調流程的詳細資訊，請參閱[管理協調流程](../core/managing-orchestrations.md)。  
  
> [!NOTE]
>  如果應用程式包含處於已部署狀態的原則，原則不會從規則引擎資料庫移除，而且會繼續顯示在 原則 資料夾中\<所有成品 > 應用程式的 BizTalk 管理 節點主控台。 如果您將該原則加入至其他應用程式，原則仍會維持在已部署狀態。  
  
## <a name="usage"></a>使用方式  
 **BTSTask RemoveApp /ApplicationName:** *值*[**/Server:***值*] [**/database:** *值*]  
  
## <a name="parameters"></a>參數  
  
|參數|Required|Description|  
|---------------|--------------|-----------------|  
|**/ ApplicationName** (或**/A**，請參閱 < 備註 >)|是|要刪除的 BizTalk 應用程式的名稱。 如果名稱包含空格，您必須將它括在雙引號 (") 中。|  
|**/ 伺服器**(或**/S**，請參閱 < 備註 >)|否|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
|**/ 資料庫**(或**/D**，請參閱 < 備註 >)|否|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="sample"></a>範例  
 **BTSTask RemoveApp /applicationname: myapplication**  
  
## <a name="remarks"></a>備註  
 參數不區分大小寫。 您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。  
  
## <a name="see-also"></a>另請參閱  
 [BTSTask 命令列參考](../core/btstask-command-line-reference.md)   
 [解除部署 BizTalk 應用程式](../core/undeploying-biztalk-applications.md)