---
title: "BTSNTSvc.exe.config 檔案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2bb89a7-4fff-4ccf-a0a7-20ca610f2ddf
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7fae2fc49487597380e6c5d04a946b1078daeeb
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="btsntsvcexeconfig-file"></a><span data-ttu-id="0d2df-102">BTSNTSvc.exe.config 檔</span><span class="sxs-lookup"><span data-stu-id="0d2df-102">BTSNTSvc.exe.config File</span></span>
<span data-ttu-id="0d2df-103">凍結屬性及其預設值都是可設定在[!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)]或 BizTalk 組態檔 （BTSNTSvc.exe.config 或 BTSNTSvc64.exe.config） 中的 XML。</span><span class="sxs-lookup"><span data-stu-id="0d2df-103">Dehydration properties and their default values are configurable in [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] or as XML in the BizTalk configuration file (BTSNTSvc.exe.config or BTSNTSvc64.exe.config).</span></span> <span data-ttu-id="0d2df-104">BizTalk 組態檔中的值將先套用。</span><span class="sxs-lookup"><span data-stu-id="0d2df-104">The values in the BizTalk configuration file are applied first.</span></span> <span data-ttu-id="0d2df-105">然後 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] 設定才會套用。</span><span class="sxs-lookup"><span data-stu-id="0d2df-105">Then, the [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] settings are applied.</span></span> <span data-ttu-id="0d2df-106">所有包含協調流程的主控件執行個體啟動時，將讀取凍結屬性。</span><span class="sxs-lookup"><span data-stu-id="0d2df-106">The dehydration properties are read when all host instances containing an orchestration start.</span></span>  
  
 <span data-ttu-id="0d2df-107">本主題著重在 BizTalk 組態檔 （BTSNTSvc.exe.config 或 BTSNTSvc64.exe.config）。</span><span class="sxs-lookup"><span data-stu-id="0d2df-107">This topic focuses on the BizTalk configuration file (BTSNTSvc.exe.config or BTSNTSvc64.exe.config).</span></span> <span data-ttu-id="0d2df-108">不會列出許多凍結屬性。</span><span class="sxs-lookup"><span data-stu-id="0d2df-108">Many dehydration properties are not listed.</span></span> <span data-ttu-id="0d2df-109">即使組態檔未明確指定這些屬性及其預設值，仍將套用這些屬性及其預設值。</span><span class="sxs-lookup"><span data-stu-id="0d2df-109">These properties and their default values are still applied, even if they are not explicitly specified in the configuration file.</span></span>  
  
 <span data-ttu-id="0d2df-110">若要變更預設值，必須將預設值明確地新增至組態檔。</span><span class="sxs-lookup"><span data-stu-id="0d2df-110">To change the default values, you must explicitly add them to your configuration file.</span></span> <span data-ttu-id="0d2df-111">如需如何變更預設凍結行為的資訊，請參閱[如何修改協調流程節流設定](../core/how-to-modify-orchestration-throttling-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="0d2df-111">For information about how to change the default dehydration behavior, see [How to Modify Orchestration Throttling Settings](../core/how-to-modify-orchestration-throttling-settings.md).</span></span> <span data-ttu-id="0d2df-112">如需協調流程記憶體節流的資訊，請參閱[如何修改協調流程記憶體節流設定](../core/how-to-modify-orchestration-memory-throttling-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="0d2df-112">For information about orchestration memory throttling, see [How to Modify Orchestration Memory Throttling Settings](../core/how-to-modify-orchestration-memory-throttling-settings.md).</span></span>  
  
 <span data-ttu-id="0d2df-113">以下是 BTSNTSvc.exe.config 檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="0d2df-113">Following is the contents of the BTSNTSvc.exe.config file.</span></span> <span data-ttu-id="0d2df-114">這個檔案位於永遠與 BTSNTSvc.exe 檔案，通常是 C:\Program Files\Microsoft BizTalk Server 相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="0d2df-114">This file is always located in the same directory as the BTSNTSvc.exe file, which is usually C:\Program Files\Microsoft BizTalk Server.</span></span>  
  
```  
<?xml version="1.0" ?>  
<configuration>  
       <configSections>  
              <section name="xlangs" type="Microsoft.XLANGs.BizTalk.CrossProcess.XmlSerializationConfigurationSectionHandler, Microsoft.XLANGs.BizTalk.CrossProcess" />  
       </configSections>  
       <runtime>  
              <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
                     <probing privatePath="BizTalk Assemblies;Developer Tools;Tracking" />  
              </assemblyBinding>  
       </runtime>  
       <xlangs>  
              <Configuration>  
                     <Dehydration MaxThreshold="1800" MinThreshold="1" ConstantThreshold="-1">  
                            <VirtualMemoryThrottlingCriteria OptimalUsage="900" MaximalUsage="1300" IsActive="true" />  
                            <PrivateMemoryThrottlingCriteria OptimalUsage="50" MaximalUsage="350" IsActive="true" />  
                            <PhysicalMemoryThrottlingCriteria OptimalUsage="50" MaximalUsage="350" IsActive="false" />  
                     </Dehydration>  
              </Configuration>  
       </xlangs>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d2df-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="0d2df-115">See Also</span></span>  
 [<span data-ttu-id="0d2df-116">針對 BizTalk Server 效能調整使用設定儀表板</span><span class="sxs-lookup"><span data-stu-id="0d2df-116">Using Settings Dashboard for BizTalk Server Performance Tuning</span></span>](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)