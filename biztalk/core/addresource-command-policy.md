---
title: AddResource 命令： 原則 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f5effcbe-bf53-4741-8d5e-227620d4d84d
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43b90d74a177d11b478aff3302aa31306188cbcd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993655"
---
# <a name="addresource-command-policy"></a>AddResource 命令：原則
若要將原則新增至 BizTalk 應用程式中，您使用**AddResource**命令，並指定**system.biztalk: rules**做為 Type 參數。 執行此命令會將原則新增至 BizTalk 管理資料庫。 原則也會顯示於 BizTalk Server 管理主控台，列在加入該原則的應用程式的 [原則] 資料夾中。 此外，原則會列出當您使用[ListApp 命令](../core/listapp-command.md)。  
  
 若要成功執行此命令，原則必須存在於規則引擎資料庫中。 如需原則匯入 「 規則引擎 」 資料庫的指示，請參閱 <<c0> [ 如何匯入原則](../core/how-to-import-a-policy.md)。 當您使用 AddResource 命令加入原則時，會自動一併加入該原則所使用的任何詞彙。  
  
## <a name="usage"></a>使用方式  
 **BTSTask AddResource** [**/ApplicationName:**<em>值</em>] **/Type:System.BizTalk:Rules** [**/覆寫**] **/Name:**<em>值</em>**/Version:**<em>值</em>[**/Server:**<em>值</em>] [**/Database:**<em>值</em>]  
  
## <a name="parameters"></a>參數  
  
|參數|必要項|ReplTest1|  
|---------------|--------------|-----------|  
|**/ ApplicationName** (或 **/A**，請參閱 < 備註 >)|否|加入原則的 BizTalk 應用程式的名稱。 如果名稱包含空格，您必須將它括在雙引號 (") 中。 若未指定應用程式名稱，將使用群組預設的 BizTalk 應用程式。|  
|**/ 鍵入**(或 **/T**，請參閱 < 備註 >)|是|**System.biztalk: rules** （此值不區分大小寫）。|  
|**/ 覆寫**(或 **/O**，請參閱 < 備註 >)|否|此選項指定更新現有的原則。 若未指定此選項，且應用程式中現有的原則與所加入的原則同名，AddResource 作業將會失敗。|  
|**/ 名稱**(或 **/N**，請參閱 < 備註 >)|是|此原則的名稱。|  
|**/Version** (或 **/V**，請參閱 < 備註 >)|是|原則的版本號碼，格式為「數字.數字」。<br /><br /> 範例： 1.0|  
|**/Server** (或 **/S**，請參閱 < 備註 >)|否|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
|**/ 資料庫**(或 **/D**，請參閱 < 備註 >)|否|BizTalk 管理資料庫的名稱。 如果不提供，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="sample"></a>範例  
 **BTSTask AddResource /applicationname: myapplication /Type: system.biztalk: rules / 覆寫 /Name:MyPolicy /Version:1.0 /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
## <a name="remarks"></a>備註  
 如果已部署 MyPolicy，上述命令將會傳回：  
  
 錯誤： 無法新增資源。  
  
 1 資源的驗證失敗。  
  
 無法覆寫版本 1.0 的規則原則 "MyPolicy"，因為已在產品中。  
  
 參數不區分大小寫。 您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。  
  
## <a name="see-also"></a>另請參閱  
 [AddResource 命令](../core/addresource-command.md)   
 [如何將原則新增至應用程式](../core/how-to-add-a-policy-to-an-application.md)