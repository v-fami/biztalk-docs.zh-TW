---
title: GetActivityName |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 479552fa-1535-4f3d-90ff-4615f14c88b1
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 55e8f35746f5f4ed1bbbe10a4d45300895340869
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246342"
---
# <a name="getactivityname"></a>GetActivityName
將目前活動的名稱推入到堆疊上。  
  
## <a name="syntax"></a>語法  
  
```  
  
<wf:Operation Name="GetActivityName"/>  
```  
  
#### <a name="parameters"></a>參數  
 無。  
  
## <a name="pushed-value"></a>推入的值  
 包含目前活動名稱的字串。  
  
## <a name="remarks"></a>備註  
 Windows Workflow Foundation 是根據開發人員設定的一系列活動來執行其工作。 每一項活動在工作流程內都指派有唯一名稱。 您可以根據唯一名稱進行篩選，來攔截特定活動的資料。  
  
## <a name="example"></a>範例  
 下列範例包含一個事件篩選運算式，這是設定來尋找已關閉工作流程中的特定活動，即 FoodAndDrinksPolicy。 這是使用包括 `GetActivityName`、`GetActivityEvent` 和邏輯運算等運算組合所完成。  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>FoodAndDrinksPolicy</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <wf:Operation Name="GetActivityEvent"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <ic:Operation Name="And"/>  
  </ic:Expression>  
</ic:Filter>  
```  
  
 這種篩選模式常見於 Windows Workflow Foundation 攔截器組態檔。  
  
> [!NOTE]
>  引數不需要引號，除非您很明確地要比對包含引號的字串。