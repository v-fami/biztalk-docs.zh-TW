---
title: "攔截器 BamActivity 項目 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6dee61b4-83cd-4a22-b8a6-1c1a7ea3648b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd43869922e46187c8b2e06155d525e428edd905
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="interceptor-bamactivity-element"></a>攔截器 BamActivity 項目
**BamActivity**項目會定義單一 BAM 活動。  
  
## <a name="format"></a>格式  
 `BamActivity`元素包含**名稱**屬性，而且包含一或多個`OnEvent`項目。  
  
```  
<ic:BamActivity Name="PurchaseOrder">  
  <!-- One or more OnEvent elements -->  
</ic:BamActivity>   
```  
  
### <a name="attributes"></a>屬性  
  
|屬性名稱|Description|  
|--------------------|-----------------|  
|名稱|BAM 活動的使用者定義名稱。|  
  
## <a name="example"></a>範例  
 下面例子包含的是具有單一 OnEvent 之 "MyOrderWorkflow" 的示範 BamActivity。  
  
```  
<ic:BamActivity Name="MyOrderWorkflow">  
  <ic:OnEvent Name="MyActivityEvent"  Source="OrderWorkflow">  
    …  
  </ic:OnEvent>  
</ic:BamActivity>  
```  
  
## <a name="see-also"></a>另請參閱  
 [攔截器 EventSource 項目](../core/interceptor-eventsource-element.md)   
 [攔截器 OnEvent 項目](../core/interceptor-onevent-element.md)