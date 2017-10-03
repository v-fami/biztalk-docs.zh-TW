---
title: "GetContextProperty2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2554a210-cfb4-4b63-9afa-ffe2a853ba7b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f834bf1271f6706c332123d8b1835e0bd730f069
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="getcontextproperty"></a>GetContextProperty
將要求的內容屬性推入到堆疊上。  
  
## <a name="syntax"></a>語法  
  
```  
  
<wf:Operation Name="GetContextProperty">  
  <wf:Argument>ContextPropertyName</wf:Argument>  
</wf:Operation>  
```  
  
#### <a name="parameters"></a>參數  
 下列其中一種內容屬性名稱：  
  
|內容屬性名稱|說明|  
|---------------------------|-----------------|  
|EventTime|目前的日期和時間。|  
|InstanceId|工作流程執行個體識別碼。|  
  
> [!NOTE]
>  內容屬性名稱有區分大小寫。  
  
## <a name="pushed-value"></a>推入的值  
 包含所要求內容屬性的字串。  
  
## <a name="remarks"></a>備註  
 時間會以 UTC 格式儲存在資料庫內部。  
  
## <a name="example"></a>範例  
 在下列範例中，提取運算式**InstanceId**在 correlationID 區塊內用來設定相互關聯識別碼。  
  
```  
<ic:CorrelationID>  
  <ic:Expression>  
    <wf:Operation Name="GetContextProperty">  
      <wf:Argument>InstanceId</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
 這是 `GetContextProperty` 的常見用途。