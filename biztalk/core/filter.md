---
title: 篩選器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8dad59d-4a47-4794-bbf9-cba02fe7f0bf
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efa69998b1782f42d7730744fd88534d26a87835
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22245798"
---
# <a name="filter"></a><span data-ttu-id="0e936-102">篩選</span><span class="sxs-lookup"><span data-stu-id="0e936-102">Filter</span></span>
<span data-ttu-id="0e936-103">`Filter` 項目包含會評估為 `Expression` 或 `true` 的 `false`，並決定何時應該處理事件或略過事件。</span><span class="sxs-lookup"><span data-stu-id="0e936-103">The `Filter` element contains an `Expression` that evaluates to `true` or `false` and determines when an event should be processed or skipped.</span></span>  
  
## <a name="format"></a><span data-ttu-id="0e936-104">格式</span><span class="sxs-lookup"><span data-stu-id="0e936-104">Format</span></span>  
  
```  
<ic:Filter>  
</ic:Filter>  
```  
  
## <a name="remarks"></a><span data-ttu-id="0e936-105">備註</span><span class="sxs-lookup"><span data-stu-id="0e936-105">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e936-106">範例</span><span class="sxs-lookup"><span data-stu-id="0e936-106">Example</span></span>  
 <span data-ttu-id="0e936-107">下列範例會定義篩選，這個篩選會在與事件相關聯之工作流程的使用者金鑰等於 "DocumentUrl" 時評估為 `true`：</span><span class="sxs-lookup"><span data-stu-id="0e936-107">The following example defines a filter that evaluates to `true` when the user key for the workflow associated with the event equals "DocumentUrl":</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0e936-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e936-108">See Also</span></span>  
 [<span data-ttu-id="0e936-109">攔截器 OnEvent 項目</span><span class="sxs-lookup"><span data-stu-id="0e936-109">Interceptor OnEvent Element</span></span>](../core/interceptor-onevent-element.md)