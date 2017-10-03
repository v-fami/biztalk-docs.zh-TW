---
title: "GetUserDataType |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0605919-a733-4a9d-a725-109346db11a2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5525dba034571acd91d1f3dd99f2b56069f81fc2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="getuserdatatype"></a>GetUserDataType
將目前的使用者資料類型名稱推入到堆疊上。  
  
## <a name="syntax"></a>語法  
  
```  
  
<wf:Operation Name="GetUserDataType" />  
```  
  
#### <a name="parameters"></a>參數  
 無。  
  
## <a name="pushed-value"></a>推入的值  
 字串，包含組件限定格式的目前使用者資料類型。  
  
## <a name="remarks"></a>備註  
 不同於**GetActivityType**，這項作業不會使用組件限定類別名稱格式，相反地，它將推入型別名稱：  
  
```  
MyLibrary.MyObject  
```  
  
> [!NOTE]
>  如果您在比較值時使用組件限定的類別名稱格式做為常數，它一定會評估為 `false`。  
  
## <a name="special-filter-behavior"></a>特殊篩選行為  
 在篩選器內部執行這項作業時，一定也會比對衍生的使用者資料類型。  
  
## <a name="example"></a>範例  
 下列範例包含事件篩選器運算式，此運算式會針對 `true` 執行個體和衍生自 `MyLibrary.MyObject` 的任何類別執行個體評估為 `MyLibrary.MyObject`。  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyLibrary.MyObject</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
  </ic:Expression>  
</ic:Filter>  
```