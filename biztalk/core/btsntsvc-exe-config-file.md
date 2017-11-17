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
ms.openlocfilehash: 303924e2aaf8304388a18d2ffe70d99fdc69acd3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="btsntsvcexeconfig-file"></a><span data-ttu-id="a4c12-102">BTSNTSvc.exe.config 檔</span><span class="sxs-lookup"><span data-stu-id="a4c12-102">BTSNTSvc.exe.config File</span></span>
<span data-ttu-id="a4c12-103">凍結屬性及其預設值都是可設定在[!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)]或 BizTalk 組態檔 （BTSNTSvc.exe.config 或 BTSNTSvc64.exe.config） 中的 XML。</span><span class="sxs-lookup"><span data-stu-id="a4c12-103">Dehydration properties and their default values are configurable in [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] or as XML in the BizTalk configuration file (BTSNTSvc.exe.config or BTSNTSvc64.exe.config).</span></span> <span data-ttu-id="a4c12-104">BizTalk 組態檔中的值將先套用。</span><span class="sxs-lookup"><span data-stu-id="a4c12-104">The values in the BizTalk configuration file are applied first.</span></span> <span data-ttu-id="a4c12-105">然後 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] 設定才會套用。</span><span class="sxs-lookup"><span data-stu-id="a4c12-105">Then, the [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] settings are applied.</span></span> <span data-ttu-id="a4c12-106">所有包含協調流程的主控件執行個體啟動時，將讀取凍結屬性。</span><span class="sxs-lookup"><span data-stu-id="a4c12-106">The dehydration properties are read when all host instances containing an orchestration start.</span></span>  
  
 <span data-ttu-id="a4c12-107">本主題著重在 BizTalk 組態檔 （BTSNTSvc.exe.config 或 BTSNTSvc64.exe.config）。</span><span class="sxs-lookup"><span data-stu-id="a4c12-107">This topic focuses on the BizTalk configuration file (BTSNTSvc.exe.config or BTSNTSvc64.exe.config).</span></span> <span data-ttu-id="a4c12-108">不會列出許多凍結屬性。</span><span class="sxs-lookup"><span data-stu-id="a4c12-108">Many dehydration properties are not listed.</span></span> <span data-ttu-id="a4c12-109">即使組態檔未明確指定這些屬性及其預設值，仍將套用這些屬性及其預設值。</span><span class="sxs-lookup"><span data-stu-id="a4c12-109">These properties and their default values are still applied, even if they are not explicitly specified in the configuration file.</span></span>  
  
 <span data-ttu-id="a4c12-110">若要變更預設值，必須將預設值明確地新增至組態檔。</span><span class="sxs-lookup"><span data-stu-id="a4c12-110">To change the default values, you must explicitly add them to your configuration file.</span></span> <span data-ttu-id="a4c12-111">如需如何變更預設凍結行為的資訊，請參閱[如何修改協調流程節流設定](../core/how-to-modify-orchestration-throttling-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="a4c12-111">For information about how to change the default dehydration behavior, see [How to Modify Orchestration Throttling Settings](../core/how-to-modify-orchestration-throttling-settings.md).</span></span> <span data-ttu-id="a4c12-112">如需協調流程記憶體節流的資訊，請參閱[如何修改協調流程記憶體節流設定](../core/how-to-modify-orchestration-memory-throttling-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="a4c12-112">For information about orchestration memory throttling, see [How to Modify Orchestration Memory Throttling Settings](../core/how-to-modify-orchestration-memory-throttling-settings.md).</span></span>  
  
 <span data-ttu-id="a4c12-113">以下是 BTSNTSvc.exe.config 檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="a4c12-113">Following is the contents of the BTSNTSvc.exe.config file.</span></span> <span data-ttu-id="a4c12-114">此檔案一定會與 BTSNTSvc.exe 檔案位於相同的目錄中，此目錄通常是 C:\Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a4c12-114">This file is always located in the same directory as the BTSNTSvc.exe file, which is usually C:\Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a4c12-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4c12-115">See Also</span></span>  
 [<span data-ttu-id="a4c12-116">使用設定儀表板，以便讓 BizTalk Server 效能調整</span><span class="sxs-lookup"><span data-stu-id="a4c12-116">Using Settings Dashboard for BizTalk Server Performance Tuning</span></span>](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)