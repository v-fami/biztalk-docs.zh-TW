---
title: "篩選器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8dad59d-4a47-4794-bbf9-cba02fe7f0bf
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efa69998b1782f42d7730744fd88534d26a87835
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="filter"></a>篩選
`Filter` 項目包含會評估為 `Expression` 或 `true` 的 `false`，並決定何時應該處理事件或略過事件。  
  
## <a name="format"></a>格式  
  
```  
<ic:Filter>  
</ic:Filter>  
```  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 下列範例會定義篩選，這個篩選會在與事件相關聯之工作流程的使用者金鑰等於 "DocumentUrl" 時評估為 `true`：  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>DocumentUrl</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
## <a name="see-also"></a>另請參閱  
 [攔截器 OnEvent 項目](../core/interceptor-onevent-element.md)