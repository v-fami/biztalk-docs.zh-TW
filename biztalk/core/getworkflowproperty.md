---
title: "GetWorkflowProperty |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9d3029e-3267-46bc-ba2e-1c6fa1f2e931
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 505fc41ce544cdf16e3826116514ba1991ba012e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="getworkflowproperty"></a>GetWorkflowProperty
將擷取自工作流程之根活動的屬性推至堆疊上。  
  
## <a name="syntax"></a>語法  
  
```  
  
<wf:Operation Name="GetWorkflowProperty">  
      <wf:Argument>Arg1</wf:Argument>  
</wf:Operation>  
```  
  
#### <a name="parameters"></a>參數  
 屬性的名稱。  
  
## <a name="pushed-value"></a>推入的值  
 包含屬性值的字串。  
  
## <a name="remarks"></a>備註  
 這項作業只適用於「更新」。  
  
 您可以使用點標記法來限定要擷取的屬性名稱。 以便存取透過屬性所公開的其他物件內的物件。 例如，若要存取訂單之 Address 執行個體的 City 屬性，請使用 "purchaseOrder.Address.City"。  
  
 屬性名稱會先區分大小寫，然後不區分大小寫。 當您的 WF 應用程式中有兩個以上只有大小寫不同的活動屬性時，這點很重要。 例如，如果工作流程應用程式中已定義屬性 "myWorkflow" 和 "MyWorkflow"，而且您要尋找 "MyWorkflow"，透過區分大小寫比對，會找到相符的第二個屬性。 如果您指定 "MYWORKFLOW"，在不區分大小寫的比對嘗試失敗之後，會透過區分大小寫比對，找到相符的 "myWorkflow"。  
  
> [!NOTE]
>  NULL 屬性值會導致 NullReferenceException 擲回到工作流程執行個體。  
  
## <a name="example"></a>範例  
 下列範例將會使用更新運算式，保存應用 `GetWorkflowProperty` 從訂單取得的工作流程屬性 "City"。  
  
```  
<ic:Update DataItemName="City" Type="NVARCHAR">  
  <ic:Expression>  
    <wf:Operation Name="GetWorkflowProperty">  
      <wf:Argument>po.Info.City</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:Update>  
```