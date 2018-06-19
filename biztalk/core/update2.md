---
title: 更新程式 2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 770c9ebb-df3a-428f-be18-b36535352f8d
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4376cae94e91f462974c626a57170b80b0117ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22286758"
---
# <a name="update"></a>Update
`Update` 項目可用來從事件中擷取資料，並將該資料匯入相關的 BAM 活動。  
  
## <a name="format"></a>格式  
 若要使用`Update`項目，您必須提供資料行名稱和型別和**運算式**包含一或多個項目**作業**評估成單一字串值的項目。  
  
```  
<ic:Update DataItemName="Name" Type="Type">  
  <ic:Expression>  
    <!-- one or more Operation elements -->  
  </ic:Expression>  
</ic:Update>  
```  
  
### <a name="attributes"></a>屬性  
  
|屬性名稱|Description|  
|--------------------|-----------------|  
|ColumnName|BAM 活動檢查點名稱。 這是會跟著已擷取資料更新的檢查點。|  
|類型|此檢查點的 BAM 資料型別必須是下列其中一種：<br /><br /> -NVARCHAR<br />日期時間<br />-INT<br />浮點數|  
  
## <a name="remarks"></a>備註  
 下面列出 `Update` 運算式不支援的運算：  
  
-   And  
  
-   等於  
  
## <a name="example"></a>範例  
 在下列範例中， **GetContextProperty** WF 作業用來擷取**EventTime**屬性。 這個值會儲存為**DATETIME** "StartOrderProcessing"資料項目的 BAM 活動的型別。  
  
```  
<ic:Update DataItemName="StartOrderProcessing" Type="DATETIME">  
  <ic:Expression>  
    <wf:Operation Name="GetContextProperty">  
      <wf:Argument>EventTime</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:Update>  
```  
  
## <a name="see-also"></a>另請參閱  
 [攔截器 OnEvent 項目](../core/interceptor-onevent-element.md)