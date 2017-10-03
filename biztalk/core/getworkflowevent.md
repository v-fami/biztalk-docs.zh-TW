---
title: "GetWorkflowEvent |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2534e0b8-26df-4554-b0df-742014deb64d
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8dc753bd45452af6ab586a11f216bc65f9539fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="getworkflowevent"></a>GetWorkflowEvent
將目前工作流程事件的名稱推至堆疊上。  
  
## <a name="syntax"></a>語法  
  
```  
  
<wf:Operation Name="GetWorkflowEvent" />  
```  
  
#### <a name="parameters"></a>參數  
 無。  
  
## <a name="pushed-value"></a>推入的值  
 包含目前工作流程事件的字串。  
  
## <a name="remarks"></a>備註  
 工作流程執行個體可能會在其執行過程期間，經過好幾種狀態。 例如，工作流程執行個體可能呈現閒置或是擱置的狀態。 每當工作流程執行個體變更狀態時，就會發出工作流程狀態事件給執行階段追蹤基礎結構。 Windows Workflow Foundation 的 BAM 攔截器支援 `System.Workflow.Runtime.Tracking.TrackingWorkflowEvent` 列舉所定義的大多數事件，如下表所示。  
  
|活動事件|Description|  
|--------------------|-----------------|  
|已變更|工作流程執行個體上已發生工作流程變更。|  
|已完成|工作流程執行個體已完成。|  
|建立日期|工作流程執行個體已建立。|  
|Exception|發生未處理的例外狀況。|  
|Idle|工作流程執行個體閒置中。|  
|已載入|工作流程執行個體已載入記憶體中。|  
|已保存|工作流程執行個體已保存。|  
|繼續|先前擱置的工作流程執行個體已繼續執行。|  
|Started|工作流程執行個體已啟動。|  
|已暫停|工作流程執行個體已擱置。|  
|已終止|工作流程執行個體已終止。|  
|已卸載|工作流程執行個體已從記憶體中卸載。|  
  
> [!NOTE]
>  您不能在同一個 OnEvent 項目中同時使用 `GetWorkflowEvent` 和 `GetActivityEvent`。  
  
## <a name="example"></a>範例  
 下列範例包含設定為找出特定活動的篩選條件 —"FoodAndDrinksPolicy"，工作流程中。 範例中的篩選條件是設定用來在結束的工作流程中尋找名為 "FoodAndDrinksPolicy" 的活動。 這是藉由比較 `GetWorkflowEvent` 的傳回值和常數 "Created" 而達成的。  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetWorkflowEvent" />   
      <ic:Operation Name="Constant">  
        <ic:Argument>Created</ic:Argument>   
      </ic:Operation>  
    <ic:Operation Name="Equals" />   
  </ic:Expression>  
</ic:Filter>  
```  
  
 在追蹤工作流程的存留期間，以及偵測工作流程的例外狀況或其他問題時，這項作業就很有用。  
  
## <a name="see-also"></a>另請參閱  
 [System.Workflow.Runtime.Tracking.TrackingWorkflowEvent 列舉](http://go.microsoft.com/fwlink/?LinkId=119568)