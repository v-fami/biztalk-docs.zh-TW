---
title: RemoveResource 命令 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8e2c6046-43d4-4ac1-a1b1-3795b4e44038
caps.latest.revision: 29
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d091c46ea25cbb2489264316239b6763d841a47e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269374"
---
# <a name="removeresource-command"></a>RemoveResource 命令
從 BizTalk 管理資料庫移除 (刪除) 成品。 執行此命令並不會將全域組件快取 (GAC)、檔案系統、憑證存放區、Internet Information Services 或 Windows 登錄等位置上已有的成品移除。 此命令既不會從 BAM 主要匯入資料庫移除 BAM 定義，也不會從規則引擎資料庫移除原則。 若您執行此命令以移除繫結檔案，繫結仍將原封不動；此舉只會移除繫結檔案而已。  
  
 您可以使用此命令移除下列成品類型：  
  
-   .NET 組件 (System.BizTalk:Assembly)  
  
-   BAM 定義 (System.BizTalk:Bam)  
  
-   BizTalk 組件 (System.BizTalk:BizTalkAssembly)  
  
-   BizTalk 繫結檔案 (System.BizTalk:BizTalkBinding)  
  
-   安全性憑證 (System.BizTalk:Certificate)  
  
-   COM 元件 (System.BizTalk:Com)  
  
-   臨機操作檔案 (System.BizTalk:File)  
  
-   後置處理指令碼 (System.BizTalk:PostProcessingScript)  
  
-   前置處理指令碼 (System.BizTalk:PreProcessingScript)  
  
-   原則或規則 (System.BizTalk:Rules)  
  
-   虛擬目錄 (System.BizTalk:WebDirectory)  
  
 在下列情況中，移除作業將會失敗：  
  
-   試圖移除的 BizTalk 組件正由其他組件所參考。  
  
-   試圖移除的 BizTalk 組件中含有傳送埠或接收埠正在使用的管線。  
  
-   試圖移除的 BizTalk 組件中含有傳送埠正在使用的對應。  
  
-   試圖移除的 BizTalk 組件中含有不在取消登錄狀態，或其執行個體擱置的協調流程。  
  
## <a name="usage"></a>使用方式  
 **BTSTask RemoveResource /ApplicationName:** *值* **/Luid:** *值*[**/Server:** *值*] [**/database:***值*]  
  
## <a name="parameters"></a>參數  
  
|參數|Required|Description|  
|---------------|--------------|-----------------|  
|**/ ApplicationName** (或 **/A**，請參閱 < 備註 >)|是|含有所要刪除之資源成品的 BizTalk 應用程式名稱。 如果名稱包含空格，您必須將它括在雙引號 (") 中。|  
|**/ Luid** (或 **/L**，請參閱 < 備註 >)|是|成品的本機唯一識別碼 (LUID)。 您可以使用來取得 LUID [ListApp 命令](../core/listapp-command.md)。|  
|**/ 伺服器**(或 **/S**，請參閱 < 備註 >)|否|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
|**/ 資料庫**(或 **/D**，請參閱 < 備註 >)|否|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="sample"></a>範例  
 **BTSTask RemoveResource /applicationname: myapplication /Luid:"MyApp.Orchestrations，版本 = 1.0.0.0，Culture = neutral，PublicKeyToken = 0123456789ABCDEF"**  
  
## <a name="remarks"></a>備註  
 參數不區分大小寫。 您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。  
  
## <a name="see-also"></a>另請參閱  
 [BTSTask 命令列參考](../core/btstask-command-line-reference.md)   
 [如何從應用程式移除成品](../core/how-to-remove-an-artifact-from-an-application.md)