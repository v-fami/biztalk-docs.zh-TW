---
title: 如何部署原則 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5c4ab85a-5a6a-4153-90dc-52e099c0a62c
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c3b07b0a8cebdd3322b49732ef4f32c04cbfede
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249182"
---
# <a name="how-to-deploy-policies"></a>如何部署原則
您可以使用，以程式設計方式部署原則[Microsoft.RuleEngine.RuleSetDeploymentDriver](http://msdn.microsoft.com/library/microsoft.ruleengine.rulesetdeploymentdriver.aspx)類別**Microsoft.RuleEngine.RuleEngineExtensions**命名空間。 下列程式碼範例示範如何使用[Microsoft.RuleEngine.RuleSetDeploymentDriver](http://msdn.microsoft.com/library/microsoft.ruleengine.rulesetdeploymentdriver.aspx)部署名為原則類別**LoanProcessing**:  
  
```  
string policyName = “LoanProcessing”;  
int majorRev = Convert.ToInt16(args[1]);  
int minorRev = Convert.ToInt16(args[2]);  
RuleSetInfo rsi = new RuleSetInfo(policyName,majorRev,minorRev);  
Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver dd;  
dd = new Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver();  
dd.Deploy(rsi);  
```  
  
> [!NOTE]
>  多載建構函式[Microsoft.RuleEngine.RuleSetDeploymentDriver](http://msdn.microsoft.com/library/microsoft.ruleengine.rulesetdeploymentdriver.aspx)類別會做為參數的規則存放區資料庫的名稱。 這可讓您將原則部署至 BizTalk Server 環境未設定使用的資料庫。  
  
## <a name="using-the-getdeploymentdriver-method"></a>使用 GetDeploymentDriver 方法  
 如果您要部署原則到資料庫，您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境設定為使用中，您不必建立**RuleSetDeploymentDriver**程式碼中的物件。 相反地，您可以要求規則引擎來建立**RuleSetDeploymentDriver**物件讓您藉由叫用**GetDeploymentDriver**方法**組態**在類別**rulesetdeploymentdriver**命名空間。 下列程式碼範例示範如何叫用**GetDeploymentDriver**方法：  
  
```  
Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver dd;  
dd = new Microsoft.RuleEngine.Configuration.GetDeploymentDriver();  
```  
  
 **GetDeploymentDriver**方法擷取的值**Hkey_local_machine\software\microsoft\businessrules\3.0**和**DeploymentDriverClass**底下的登錄機碼**HKEY_LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0**，並建立的執行個體**DeploymentDriverClass**。 下列表格顯示這兩個登錄機碼的預設值。  
  
|登錄機碼|值|  
|------------------|-----------|  
|DeploymentDriverAssembly|Microsoft.BizTalk.RuleEngineExtensions|  
|DeploymentDriverClass|Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver|  
  
 **RuleSetDeploymentDriver**類別會實作**IRuleSetDeploymentDriver**介面。 您可以建立實作的類別來開發您自己的原則部署驅動程式**IRuleSetDeploymentDriver**適當的介面和登錄機碼值做為上述的變更。