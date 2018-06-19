---
title: 疑難排解 BizTalk Server 移轉 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e6eddc0a-2403-4bcd-9327-23f51ce7d57b
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ddb6d9780a86183de5a09791de44adda5d57dab
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26006055"
---
# <a name="troubleshooting-biztalk-server-migration"></a>疑難排解 BizTalk Server 移轉
本節提供從 BizTalk 應用程式移轉時，發現一般問題的相關資訊的集中式的位置[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]或[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]至 BizTalk Server 2009。  
  
## <a name="known-issues"></a>已知問題  
  
#### <a name="custom-applications-might-not-work-while-upgrading"></a>升級時自訂應用程式可能無法運作  
  
##### <a name="problem"></a>問題  
 升級時[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]或[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]至 BizTalk Server 2009 部分自訂應用程式可能不會運作。  
  
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
  
## <a name="see-also"></a>請參閱  
 [疑難排解](../core/troubleshooting.md)