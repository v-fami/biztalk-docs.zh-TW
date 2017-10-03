---
title: "GetActivityProperty |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2321f1ec-d98d-478f-bb1d-a11a98e60fa5
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a55f0d24da85088fb8f13693c8c71d32bee1bef7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="getactivityproperty"></a>GetActivityProperty
將從與追蹤事件相關的活動所擷取的屬性推至堆疊上。  
  
## <a name="syntax"></a>語法  
  
```  
  
<wf:Operation Name="GetActivityProperty">  
      <wf:Argument>Arg1</wf:Argument>  
</wf:Operation>  
```  
  
#### <a name="parameters"></a>參數  
 屬性的名稱。  
  
## <a name="return-value"></a>傳回值  
 包含屬性值的字串。  
  
## <a name="remarks"></a>備註  
 您可以使用點標記法來限定要擷取的屬性名稱。 以便存取透過屬性所公開的其他物件內的物件。 例如，若要存取訂單之 Address 執行個體的 City 屬性，請使用 "purchaseOrder.Address.City"。  
  
 屬性名稱會先區分大小寫，然後不區分大小寫。 當您的 WF 應用程式中有兩個以上只有大小寫不同的活動屬性時，這點很重要。 例如，如果工作流程應用程式中已定義屬性 "myWorkflow" 和 "MyWorkflow"，而且您要尋找 "MyWorkflow"，透過區分大小寫比對，會找到相符的第二個屬性。 如果您指定 "MYWORKFLOW"，在區分大小寫的比對嘗試失敗之後，會透過不區分大小寫比對，找到相符的 "myWorkflow"。  
  
 如果您有兩個活動屬性只能由不同的案例，例如:"myProperty"和"MyProperty"。  
  
> [!NOTE]
>  NULL 屬性值會導致 NullReferenceException 擲回到工作流程執行個體。  
  
## <a name="example"></a>範例  
 在下列範例中，更新運算式會藉由使用 `GetActivityProperty`，保存活動屬性 "MyProperty"。  
  
```  
<ic:Update DataItemName="TextData" Type="NVARCHAR">  
  <ic:Expression>  
    <wf:Operation Name="GetActivityProperty">  
      <wf:Argument>MyProperty</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:Update>  
```