---
title: "疑難排解 BizTalk Server 移轉 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6eddc0a-2403-4bcd-9327-23f51ce7d57b
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1dcdb53c7123b4ffaa2294db080e1efc4fb4eb65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-biztalk-server-migration"></a>疑難排解 BizTalk Server 移轉
本節針對將 BizTalk 應用程式從 [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] 或 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009 移轉至 [!INCLUDE[prague](../includes/prague-md.md)] 時發生的常見問題，集中提供相關的資訊。  
  
## <a name="known-issues"></a>已知問題  
  
#### <a name="custom-applications-might-not-work-while-upgrading"></a>升級時自訂應用程式可能無法運作  
  
##### <a name="problem"></a>問題  
 從 [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] 或 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009 升級到 [!INCLUDE[prague](../includes/prague-md.md)] 時，部分自訂應用程式可能無法運作。  
  
##### <a name="cause"></a>原因  
 所有 BizTalk Managed 程式碼元件都在 CLR 4.0 上執行。 因為這些元件都是針對 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 來編譯，它們需要組態檔才能在 CLR 4.0 中執行。  
  
##### <a name="solution"></a>方案  
 若要解決此問題，請更新組態檔。  
  
```  
<configuration>  
<startup useLegacyV2RuntimeActivationPolicy="true">  
<supportedRuntime version="v4.0" />  
</startup>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解](../core/troubleshooting.md)