---
title: "將 GetActivityType |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65a5aae3-9688-4c49-a78e-1d9c1cc85fea
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67e6f31331907e20e810c11e82002fb08b89abe4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="getactivitytype"></a>GetActivityType
將目前活動類型的名稱推至堆疊上。  
  
## <a name="syntax"></a>語法  
  
```  
  
<wf:Operation Name="GetActivityType" />  
```  
  
#### <a name="parameters"></a>參數  
 無。  
  
## <a name="pushed-value"></a>推入的值  
 字串，包含具有組件限定類別名稱格式的目前活動類型。  
  
## <a name="remarks"></a>備註  
 `GetActivityType` 作業會擷取目前活動類型並以組件限定的類別名稱格式將其置於堆疊上：  
  
```  
TopNamespace.SubNameSpace.ContainingClass+NestedClass, MyAssembly, Version=1.3.0.0, Culture=neutral, PublicKeyToken=b17a5c561934e08, processorArchitecture=MSIL  
```  
  
 進行比較時，您可以視需要指定類型，以滿足特定搜尋需求。 例如，您可能會將 GetActivityType 的結果與以下常數比較：  
  
 TopNamespace.SubNameSpace.ContainingClass+NestedClass, MyAssembly, Version=1.3.0.0  
  
 這比組件限定的類別名稱格式的限制要少。  
  
## <a name="special-filter-behavior"></a>特殊篩選行為  
 在篩選器內部執行這項作業時，一定也會比對衍生的活動。  
  
## <a name="example"></a>範例  
 下列範例包含事件篩選器運算式，此運算式會針對 `true` 執行個體和衍生自 `System.Workflow.ComponentModel.Activity` 的任何類別執行個體評估為 `System.Workflow.ComponentModel.Activity`。  
  
```  
<ic:Expression>  
  <wf:Operation Name="GetActivityType" />  
  <ic:Operation Name="Constant">  
    <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
  </ic:Operation>  
  <ic:Operation Name="Equals" />  
</ic:Expression>  
```