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
# <a name="btsntsvcexeconfig-file"></a>BTSNTSvc.exe.config 檔
凍結屬性及其預設值都是可設定在[!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)]或 BizTalk 組態檔 （BTSNTSvc.exe.config 或 BTSNTSvc64.exe.config） 中的 XML。 BizTalk 組態檔中的值將先套用。 然後 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] 設定才會套用。 所有包含協調流程的主控件執行個體啟動時，將讀取凍結屬性。  
  
 本主題著重在 BizTalk 組態檔 （BTSNTSvc.exe.config 或 BTSNTSvc64.exe.config）。 不會列出許多凍結屬性。 即使組態檔未明確指定這些屬性及其預設值，仍將套用這些屬性及其預設值。  
  
 若要變更預設值，必須將預設值明確地新增至組態檔。 如需如何變更預設凍結行為的資訊，請參閱[如何修改協調流程節流設定](../core/how-to-modify-orchestration-throttling-settings.md)。 如需協調流程記憶體節流的資訊，請參閱[如何修改協調流程記憶體節流設定](../core/how-to-modify-orchestration-memory-throttling-settings.md)。  
  
 以下是 BTSNTSvc.exe.config 檔案的內容。 此檔案一定會與 BTSNTSvc.exe 檔案位於相同的目錄中，此目錄通常是 C:\Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [使用設定儀表板，以便讓 BizTalk Server 效能調整](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)