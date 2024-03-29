---
title: 其他一般檔案屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c88ad2f-b5a8-46e6-b1b8-61ce6ba910d1
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 56db18d93eda3c5ddaaefcf58b73e0870cbb332c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013311"
---
# <a name="additional-flat-file-properties"></a>其他一般檔案屬性

## <a name="hidden-properties"></a>隱藏的屬性
下表列出「結構描述編輯器」中未顯示的其他一般檔案節點屬性。 若要使用這些屬性，需要在文字編輯器中手動編輯結構描述檔案。  

|屬性|值|預設值|描述|  
|--------------|------------|-------------------|-----------------|  
|suppress_empty_nodes|**[True]** 或 **[False]**|**false**|指示在剖析器產生 XML 執行個體資料後是否移除空的 XML 節點。|  
|generate_empty_nodes|**[True]** 或 **[False]**|**true**|為存在 XML 執行個體資料中的記錄產生空節點。|  
|parser_optimization|**速度**或**複雜度**|**速度**|使速度最佳化可降低剖析時間，但代價是必須處理一些不明確的資料。 使複雜度最佳化可處理範圍較廣的模稜兩可狀況，但會犧牲速度。|  
|lookahead_depth|任何正整數；零 (0) 表示無限先行剖析。|3|比對資料的先行剖析深度。|  
|allow_early_termination|**[True]** 或 **[False]**|**false**|指出是否可提早終止位置記錄 (**，則為 true**)，或必須包含所有記錄欄位的資料 (**false**)。|  
|early_terminate_optional_fields|**[True]** 或 **[False]**|**false**|讓選擇性尾端欄位提早終止 (**，則為 true**)。 如果在 BizTalk 編輯器中開啟現有的結構描述，如果沒有此註解，此註解會將它設為預設值 (**false**)。 **注意：** early_terminate_optional_fields 註解才會生效，如果在 allow_early_termination 設定為"true"。|  

 所有這些屬性是的特性 **/annotation/appinfo/schemaInfo**項目。  

 當**parser_optimization**設為**複雜度**，有相同的群組或記錄中的許多選擇性節點時，您可能必須針對結構描述驗證失敗。 您可能需要設定**lookahead_depth**為零 (0) 以避免驗證錯誤。  

## <a name="see-also"></a>另請參閱  
- [節點屬性](../core/node-properties.md)   
- **一般檔案結構描述的增補節點屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
