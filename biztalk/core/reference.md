---
title: 參考 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b916c55a-c84c-4008-8927-f8e584c36fe9
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3e32145e2340a4d86a6893db3e9209b79c2b5e7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268598"
---
# <a name="reference"></a>參考
**參考**項目可用來將一或多個關聯性加入至 BAM 活動。 當您想要將指標如主索引鍵、識別碼或 URL 附加到相關訊息時，這十分有用。 例如，您可以在訂單活動中儲存出貨批次的參考。  
  
## <a name="format"></a>格式  
 `Reference`元素同時支援**資料**和**LongData**子項目包含一個運算式來指定要附加到 BAM 活動的資料。 您可以使用的任何組合**資料**和**LongData**以符合追蹤需求。  
  
### <a name="attributes"></a>屬性  
  
|屬性名稱|Description|  
|--------------------|-----------------|  
|名稱|將附加到 BAM 活動的關係名稱。|  
|類型|任意字串，指定將附加到 BAM 活動的關係類型。 支援任意字串和下列預先定義的 BAM 類型：<br /><br /> -BizTalkService<br />-MessageID<br />活動<br />-DocumentUrl<br />-執行個體識別碼<br /><br /> 如需有關預先定義的 BAM 參考類型的詳細資訊，請參閱[參考屬性](http://go.microsoft.com/fwlink/?LinkId=119601)。|  
  
### <a name="child-elements"></a>子元素  
  
|執行狀態|Description|  
|----------------------|-----------------|  
|data|指定如何擷取將附加到 BAM 活動的字串資料 (最多 128 個字元)。|  
|LongData|指定如何擷取將附加到 BAM 活動的任意長度字串資料。|  
  
> [!NOTE]
>  A`Reference`項目可以結合一或多個**資料**和**LongData**視需要的項目子系。  
  
## <a name="remarks"></a>備註  
 Reference 運算式中不允許執行下列常見的運算：  
  
-   And  
  
-   等於  
  
## <a name="example"></a>範例  
 下列範例會使用 `GetUserData`，為工作流程建立 "DocumentUrl" 類型的 "Related Document" 參考。 因為使用者資料預期少於 1024 字元長度，所以會使用 `Data` 項目以取得 `Expression` 項目。  
  
```  
<ic:Reference Name="Related Document" Type="DocumentUrl">  
  <ic:Data>  
    <ic:Expression>  
      <wf:Operation Name="GetUserData" />  
    </ic:Expression>  
  </ic:Data>  
</ic:Reference>  
```  
  
 **參考**項目支援的混合`Data`和`LongData`項目。 下列範例會從 WCF 服務擷取訂單中的 Country Name 和 Note 欄位，並寫入至 "Long and Short Data" 關係做為 "MyType" 類型。 因為 Note 欄位支援 1024 個字元以上，所以運算式會包含在 `LongData` 項目中。  
  
```  
<ic:Reference Name="Long and Short Data" Type="MyType">  
  <ic:Data>  
    <ic:Expression>  
      <ic:Operation Name="Constant">  
        <ic:Argument>Country: </ic:Argument>  
      </ic:Operation>  
      <wcf:Operation Name="XPath">  
        <wcf:Argument>//s:Body//po:Country</wcf:Argument>  
      </wcf:Operation>  
       <ic:Operation Name="Concatenate" />  
    </ic:Expression>  
  </ic:Data>  
  <ic:LongData>  
    <ic:Expression>  
      <ic:Operation Name="Constant">  
        <ic:Argument>Note: </ic:Argument>  
      </ic:Operation>  
      <wcf:Operation Name="XPath">  
        <wcf:Argument>//s:Body//po:Note</wcf:Argument>  
      </wcf:Operation>  
      <ic:Operation Name="Concatenate" />  
    </ic:Expression>  
  </ic:LongData>  
</ic:Reference>  
```  
  
## <a name="see-also"></a>另請參閱  
 [攔截器 OnEvent 項目](../core/interceptor-onevent-element.md)   
 [EventStream.AddRelatedActivity 方法](http://go.microsoft.com/fwlink/?LinkId=119602)