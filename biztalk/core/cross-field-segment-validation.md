---
title: "交叉驗證欄位區段 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e757b4f-71fe-44d5-9580-c8b1c8eb2366
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efd3a0b5f68ded39fbf5cc88a4ba8aac6725602e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="cross-field-segment-validation"></a>交叉驗證欄位區段
EDI 接收管線和 EDI 傳送管線，可以對 X12 編碼訊息中的交易集資料元素執行欄位/區段交互驗證。 這種驗證就稱為 X12 中的關係條件。 欄位交互驗證是以註解表示，因此與 EDI 驗證相關。  
  
> [!NOTE]
>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 不支援 EDIFACT 相依性規則。  
  
 對於 X12 編碼訊息，您可以將訊息結構描述中的 X12ConditionDesignator_Check 旗標設為 "Yes"，便可啟用這項驗證功能。 這個旗標位在結構描述 “appinfo” 區段的註解中。 這個旗標預設是設為 "No"，表示 X12 結構描述的欄位/區段交互驗證尚未啟用。 若是 HIPAA 結構描述，預設是設為 “Yes”，表示欄位/區段交互驗證已啟用。  
  
> [!NOTE]
>  欄位/區段交互驗證完全不同於 EDI 資料元素驗證和擴充 (BTS-XSD) 驗證。 EDI 資料元素驗證和/或擴充驗證可以在不執行欄位/區段交互驗證情況下執行，而欄位/區段交互驗證可以在不執行 EDI 資料元素驗證和/或擴充驗證的情況下執行。  
  
 X12 的選用性包括「強制性」(M)、「選擇性」(O) 和「關係性」(R) (欄位交互驗證)。 若是選擇「強制性」，表示至少要指定綜合類型中的一個元件資料元素做為值。  
  
## <a name="x12-optionality"></a>X12 選用性  
 在 X12 中，關係性選用性的欄位/區段交互驗證包括列為結構描述中規則的一系列檢查。 每個規則由下列項目中\<xs:annotation\>項目：  
  
```  
<b:Rule subjects="X12ConditionDesignatorX_<relational_condition>"…>  
```  
  
 在「規則」項目中的關係條件，表示該規則將驗證的內容。 這個項目包括欄位交互驗證將針對其執行的主旨清單。 下面節點中含有這些主旨：  
  
```  
<b:Subject name="<subject>"/>  
```  
  
 下表將列出這些 X12 關係條件：  
  
|子類別|關係條件|Description|  
|-----------------------|--------------------------|-----------------|  
|Paired|X12ConditionDesignatorX_Paired|如果有存在指定於關係條件中的任何一個主旨項目，表示一定會存在所有已指定的主旨項目。|  
|Required|X12ConditionDesignatorX_Required|至少一定會存在一個已指定於關係條件中的主旨項目。|  
|Exclusion|X12ConditionDesignatorX_Exclusion|可能會存在最多一個已指定於關係條件中的主旨項目。|  
|條件式|X12ConditionDesignatorX_Conditional|如果有存在指定於關係條件中的第一個主旨項目，表示一定會存在其他所有的主旨項目。 未指定成為此條件中第一個項目的任何或全部的項目，不需要等到第一個項目存在就可存在。 在此條件中的項目順序，不一定要與資料區段中的資料元素順序相同。|  
|List Conditional|X12ConditionDesignatorX_List Conditional|如果有存在指定於關係條件中的第一個主旨項目，表示至少會存在其餘的一個主旨項目。 未指定成為此條件中第一個項目的任何或全部的項目，不需要等到第一個項目存在就可存在。 在此條件中的項目順序，不一定要與資料區段中的資料元素順序相同。|  
  
## <a name="see-also"></a>請參閱  
 [EDI 訊息驗證](../core/edi-message-validation.md)