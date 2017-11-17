---
title: "如何部署原則 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c4ab85a-5a6a-4153-90dc-52e099c0a62c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c3b07b0a8cebdd3322b49732ef4f32c04cbfede
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-deploy-policies"></a><span data-ttu-id="61310-102">如何部署原則</span><span class="sxs-lookup"><span data-stu-id="61310-102">How to Deploy Policies</span></span>
<span data-ttu-id="61310-103">您可以使用，以程式設計方式部署原則[Microsoft.RuleEngine.RuleSetDeploymentDriver](http://msdn.microsoft.com/library/microsoft.ruleengine.rulesetdeploymentdriver.aspx)類別**Microsoft.RuleEngine.RuleEngineExtensions**命名空間。</span><span class="sxs-lookup"><span data-stu-id="61310-103">You can deploy policies programmatically by using the [Microsoft.RuleEngine.RuleSetDeploymentDriver](http://msdn.microsoft.com/library/microsoft.ruleengine.rulesetdeploymentdriver.aspx) class in the **Microsoft.RuleEngine.RuleEngineExtensions** namespace.</span></span> <span data-ttu-id="61310-104">下列程式碼範例示範如何使用[Microsoft.RuleEngine.RuleSetDeploymentDriver](http://msdn.microsoft.com/library/microsoft.ruleengine.rulesetdeploymentdriver.aspx)部署名為原則類別**LoanProcessing**:</span><span class="sxs-lookup"><span data-stu-id="61310-104">The following sample code demonstrates how to use the [Microsoft.RuleEngine.RuleSetDeploymentDriver](http://msdn.microsoft.com/library/microsoft.ruleengine.rulesetdeploymentdriver.aspx) class to deploy a policy named **LoanProcessing**:</span></span>  
  
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
>  <span data-ttu-id="61310-105">多載建構函式[Microsoft.RuleEngine.RuleSetDeploymentDriver](http://msdn.microsoft.com/library/microsoft.ruleengine.rulesetdeploymentdriver.aspx)類別會做為參數的規則存放區資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="61310-105">The overloaded constructors of the [Microsoft.RuleEngine.RuleSetDeploymentDriver](http://msdn.microsoft.com/library/microsoft.ruleengine.rulesetdeploymentdriver.aspx) class take the names of the rule store database as a parameter.</span></span> <span data-ttu-id="61310-106">這可讓您將原則部署至 BizTalk Server 環境未設定使用的資料庫。</span><span class="sxs-lookup"><span data-stu-id="61310-106">This allows you to deploy policies to a database that your BizTalk Server environment is not configured to use.</span></span>  
  
## <a name="using-the-getdeploymentdriver-method"></a><span data-ttu-id="61310-107">使用 GetDeploymentDriver 方法</span><span class="sxs-lookup"><span data-stu-id="61310-107">Using the GetDeploymentDriver Method</span></span>  
 <span data-ttu-id="61310-108">如果您要部署原則到資料庫，您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境設定為使用中，您不必建立**RuleSetDeploymentDriver**程式碼中的物件。</span><span class="sxs-lookup"><span data-stu-id="61310-108">If you are deploying policies to the database that your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment is configured to use, you do not have to create the **RuleSetDeploymentDriver** object in the code.</span></span> <span data-ttu-id="61310-109">相反地，您可以要求規則引擎來建立**RuleSetDeploymentDriver**物件讓您藉由叫用**GetDeploymentDriver**方法**組態**在類別**rulesetdeploymentdriver**命名空間。</span><span class="sxs-lookup"><span data-stu-id="61310-109">Instead, you can request the rule engine to create a **RuleSetDeploymentDriver** object for you by invoking the **GetDeploymentDriver** method of the **Configuration** class in the **System.RuleEngine** namespace.</span></span> <span data-ttu-id="61310-110">下列程式碼範例示範如何叫用**GetDeploymentDriver**方法：</span><span class="sxs-lookup"><span data-stu-id="61310-110">The following sample code demonstrates how to invoke the **GetDeploymentDriver** method:</span></span>  
  
```  
Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver dd;  
dd = new Microsoft.RuleEngine.Configuration.GetDeploymentDriver();  
```  
  
 <span data-ttu-id="61310-111">**GetDeploymentDriver**方法擷取的值**Hkey_local_machine\software\microsoft\businessrules\3.0**和**DeploymentDriverClass**底下的登錄機碼**HKEY_LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0**，並建立的執行個體**DeploymentDriverClass**。</span><span class="sxs-lookup"><span data-stu-id="61310-111">The **GetDeploymentDriver** method retrieves the values of the **DeploymentDriverAssembly** and **DeploymentDriverClass** registry keys under **HKEY_LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0**, and creates an instance of **DeploymentDriverClass**.</span></span> <span data-ttu-id="61310-112">下列表格顯示這兩個登錄機碼的預設值。</span><span class="sxs-lookup"><span data-stu-id="61310-112">The following table shows the default values of these two registry keys.</span></span>  
  
|<span data-ttu-id="61310-113">登錄機碼</span><span class="sxs-lookup"><span data-stu-id="61310-113">Registry key</span></span>|<span data-ttu-id="61310-114">值</span><span class="sxs-lookup"><span data-stu-id="61310-114">Value</span></span>|  
|------------------|-----------|  
|<span data-ttu-id="61310-115">DeploymentDriverAssembly</span><span class="sxs-lookup"><span data-stu-id="61310-115">DeploymentDriverAssembly</span></span>|<span data-ttu-id="61310-116">Microsoft.BizTalk.RuleEngineExtensions</span><span class="sxs-lookup"><span data-stu-id="61310-116">Microsoft.BizTalk.RuleEngineExtensions</span></span>|  
|<span data-ttu-id="61310-117">DeploymentDriverClass</span><span class="sxs-lookup"><span data-stu-id="61310-117">DeploymentDriverClass</span></span>|<span data-ttu-id="61310-118">Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver</span><span class="sxs-lookup"><span data-stu-id="61310-118">Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver</span></span>|  
  
 <span data-ttu-id="61310-119">**RuleSetDeploymentDriver**類別會實作**IRuleSetDeploymentDriver**介面。</span><span class="sxs-lookup"><span data-stu-id="61310-119">The **RuleSetDeploymentDriver** class implements the **IRuleSetDeploymentDriver** interface.</span></span> <span data-ttu-id="61310-120">您可以建立實作的類別來開發您自己的原則部署驅動程式**IRuleSetDeploymentDriver**適當的介面和登錄機碼值做為上述的變更。</span><span class="sxs-lookup"><span data-stu-id="61310-120">You can develop your own policy deployment driver by creating a class that implements the **IRuleSetDeploymentDriver** interface and change the values for the registry keys described above as appropriate.</span></span>