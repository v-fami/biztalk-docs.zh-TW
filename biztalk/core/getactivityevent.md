---
title: GetActivityEvent |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fe824c9-4cea-44da-b830-5520d67988e0
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9fb039c0e9946091214a52fbb605753a212c233c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246246"
---
# <a name="getactivityevent"></a>GetActivityEvent
將目前活動事件的名稱推至堆疊上。  
  
## <a name="syntax"></a>語法  
  
```  
  
<wf:Operation Name="GetActivityEvent"/>  
```  
  
#### <a name="parameters"></a>參數  
 無。  
  
## <a name="pushed-value"></a>推入的值  
 包含目前活動事件的字串。  
  
## <a name="remarks"></a>備註  
 工作流程活動可能會在工作流程存留期間，經過好幾種狀態。 Windows Workflow Foundation 的 BAM 攔截器支援 `System.Workflow.ComponentModel.ActivityExecutionStatus` 列舉所定義的大多數執行狀態值，如下表所示。  
  
|執行狀態|說明|  
|----------------------|-----------------|  
|Canceling|代表活動正在取消的狀態中。|  
|Closed|代表活動已結束的狀態。|  
|Compensating|代表活動正在補償的狀態中。|  
|Executing|代表活動正在執行的狀態中。|  
|Faulting|代表活動正在失敗的狀態中。|  
  
> [!NOTE]
>  您不能在同一個 OnEvent 項目中同時使用 `GetActivityEvent` 和 `GetWorkflowEvent`。  
  
## <a name="example"></a>範例  
 下列範例包含一個事件篩選條件運算式，這是設定來尋找 Closed 工作流程中的特定活動，即 FoodAndDringPolicy。 這是使用包括 `GetActivityEvent`、`GetActivityName` 和邏輯運算等運算組合所完成。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [System.Workflow.ComponentModel.ActivityExecutionStatus 列舉](http://go.microsoft.com/fwlink/?LinkId=119570)