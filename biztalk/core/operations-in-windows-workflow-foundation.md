---
title: Windows Workflow Foundation 中的作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a048dfc0-26b2-4f20-9d2f-c52f1ab19ac3
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 057154a2e64541b00c704be7078ef27ba596de20
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007599"
---
# <a name="operations-in-windows-workflow-foundation"></a>Windows Workflow Foundation 內的作業
本章節包含 BAM WF 攔截器所支援的自訂作業。  
  
## <a name="determining-where-operations-are-allowed"></a>決定允許作業的位置  
 BAM WF 攔截器所提供的自訂作業，可依相關聯的 Windows Workflow Foundation 追蹤點類型分類：  
  
- 活動  
  
- 工作流程  
  
- 使用者  
  
  BAM WF 攔截器會使用這些類別將追蹤點類型指派給每個**OnEvent**。 則會根據這項指派作業中發現的型別**OnEvent**篩選和資料擷取和操作區段。 例如，如果**OnEvent**包含**更新**使用的項目**GetUserData** ，就屬於使用者追蹤點類型，因為活動和工作流程事件不支援這項作業。 如需追蹤點的詳細資訊，請參閱在 System.Workflow.Runtime.Tracking [ http://go.microsoft.com/fwlink/?LinkId=80242 ](http://go.microsoft.com/fwlink/?LinkId=80242)。  
  
> [!NOTE]
>  工作流程追蹤點無法從工作流程擷取資料。  
  
 同時在篩選條件運算式內和篩選條件運算式之間，以及 `OnEvent` 元素內的資料擷取和操作區段內執行的作業必須相容。 下表顯示哪些作業可用於各追蹤點類型的篩選條件運算式。  
  
|篩選條件運算式作業|對活動追蹤點有效嗎？|對工作流程追蹤點有效嗎？|對使用者追蹤點有效嗎？|  
|---------------------------------|-------------------------------------|-------------------------------------|---------------------------------|  
|等於|是|是|是|  
|And|是|是|是|  
|串連|否|否|否|  
|常數|是|是|是|  
|GetActivityEvent|是|否|否|  
|GetActivityName|是|否|是|  
|GetActivityProperty|是|否|是|  
|GetActivityType|是|否|是|  
|GetContextProperty|否|否|否|  
|GetUserData|否|否|否|  
|GetUserDataType|否|否|是|  
|GetUserKey|否|否|是|  
|GetWorkflowEvent|否|是|否|  
|GetWorkflowProperty|否|否|否|  
  
 如果您混合不相容的作業，部署攔截器組態檔時，就會收到錯誤。 比方說，如果您同時使用`GetActivityEvent`並`GetWorkflowEvent`內篩選條件，或在篩選和資料擷取或操作事件 (例如**CorrelationID**)，您會收到錯誤。  
  
 下表摘要敘述資料擷取或操作中每項活動類型支援的作業。  
  
|資料擷取或操作作業|對活動追蹤點有效嗎？|對工作流程追蹤點有效嗎？|對使用者追蹤點有效嗎？|  
|-----------------------------------------------|-------------------------------------|-------------------------------------|---------------------------------|  
|等於|是|是|是|  
|And|是|是|是|  
|串連|是|是|是|  
|常數|是|是|是|  
|GetActivityEvent|是|否|否|  
|GetActivityName|是|否|是|  
|GetActivityProperty|是|否|是|  
|GetActivityType|是|否|是|  
|GetContextProperty|是|是|是|  
|GetUserData|否|否|是|  
|GetUserDataType|否|否|是|  
|GetUserKey|否|否|是|  
|GetWorkflowEvent|否|是|否|  
|GetWorkflowProperty|是|否|是|  
  
> [!NOTE]
>  單一之間的一對一對應**OnEvent**和單一追蹤點。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [GetActivityEvent](../core/getactivityevent.md)  
  
-   [GetActivityName](../core/getactivityname.md)  
  
-   [GetActivityProperty](../core/getactivityproperty.md)  
  
-   [GetActivityType](../core/getactivitytype.md)  
  
-   [GetContextProperty](../core/getcontextproperty2.md)  
  
-   [GetUserData](../core/getuserdata.md)  
  
-   [GetUserDataType](../core/getuserdatatype.md)  
  
-   [GetUserKey](../core/getuserkey.md)  
  
-   [GetWorkflowEvent](../core/getworkflowevent.md)  
  
-   [GetWorkflowProperty](../core/getworkflowproperty.md)  
  
## <a name="see-also"></a>另請參閱  
 [BAM WF 攔截器](../core/bam-wf-interceptor.md)