---
title: "GetContextProperty1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8867c29-63de-4a13-9ef9-8c6ab8ea3443
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 65b7ffffe4b21e3317b920ac50cdc27b12d708d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="getcontextproperty"></a>GetContextProperty
將要求的內容屬性推入到堆疊上。  
  
## <a name="syntax"></a>語法  
  
```  
  
<wcf:Operation Name ="GetContextProperty">  
  <wcf:Argument>EventTime</wcf:Argument>  
</wcf:Operation>  
```  
  
#### <a name="parameters"></a>參數  
 下列其中一種內容屬性名稱：  
  
|內容屬性名稱|說明|  
|---------------------------|-----------------|  
|EventTime|目前的日期和時間。|  
|SessionId|工作流程工作階段識別碼。|  
  
> [!NOTE]
>  內容屬性名稱有區分大小寫。  
  
## <a name="pushed-value"></a>推入的值  
 包含所要求內容屬性的字串。  
  
## <a name="remarks"></a>備註  
 時間會以 UTC 格式儲存在資料庫內部。  
  
## <a name="example"></a>範例  
 在下列範例更新運算式中，核准日期是以擷取目前事件之事件時間方式擷取所得。  
  
```  
<ic:Update DataItemName ="Approval Date" Type ="DATETIME">  
  <ic:Expression>  
    <wcf:Operation Name ="GetContextProperty">  
      <wcf:Argument>EventTime</wcf:Argument>  
    </wcf:Operation>  
  </ic:Expression>  
</ic:Update>  
```  
  
 這是 `GetContextProperty` 的常見用途。  
  
## <a name="see-also"></a>另請參閱  
 [Windows Communication Foundation 中的作業](../core/operations-in-windows-communication-foundation.md)