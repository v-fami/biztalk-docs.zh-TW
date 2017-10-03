---
title: "ContinuationToken |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d4911fc-c6fb-4628-9177-bd723d4d8ebc
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54cf9b9326661925f2d55bacd2fb22d02f565f89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="continuationtoken"></a>ContinuationToken
接續 Token 是用來讓 BAM 基礎結構內的異質資訊相互關聯。 請參考建構下列類型訊息的商務程序：  
  
-   由訂單編號識別的訂單  
  
-   由銷售訂單編號識別的銷售訂單  
  
-   由送貨單編號識別的送貨單  
  
 在這個過程中，有三個重要的識別項： 採購單識別碼、 銷售訂單識別碼和傳送順序識別碼。 這三個識別碼每一個都表示原始訂單存留期間的一個重要事件，但是彼此之間無法直接關聯。 若要追蹤與訂單相關的事件，就必須識別訊息之間常見的資訊，以協助 BAM 追蹤基礎結構正確地將這些事件相互關聯。  
  
## <a name="format"></a>格式  
 接續 Token 是由運算式項目和一或多項運算所組成：  
  
```  
<ic:ContinuationToken>  
  <ic:Expression>  
    <!-- Operations -->  
  </ic:Expression>  
</ic:ContinuationToken>  
```  
  
## <a name="remarks"></a>備註  
 ContinuationToken 運算式中不允許執行下列常見的運算：  
  
-   And  
  
-   等於  
  
 [WF/WCF 中「運算」章節的標頭應有類似的圖表和其他圖表 (如有需要)]  
  
## <a name="example"></a>範例  
 此範例中會使用 `GetWorkflowProperty` 從工作流程擷取 WF 程序的接續 Token。 在此，開發人員決定在工作流程中使用自訂程式碼支援接續，可能是因為判斷接續 Token 的程序涉及兩或三個以上的運算式，且可能倚賴外部資料。  
  
```  
<ic:ContinuationToken>  
  <ic:Expression>  
    <wf:Operation Name="GetWorkflowProperty">  
      <wf:Argument>ContinuationToken</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:ContinuationToken>  
```  
  
 您可以選擇在新的 WF 或 WCF 應用程式中提供類似的功能，或者如果使用運算式作業建立 Token 十分容易，則可避免撰寫額外的程式碼。  
  
 下列範例會使用建立 WCF 程序的接續 token **XPath**從目前訊息擷取信用卡號碼作業和**常數**和**串連**作業前面加上要擷取的數字的字串"CID_":  
  
```  
<ic:ContinuationToken>  
  <ic:Expression>  
    <ic:Operation Name="Constant">  
      <ic:Argument>CID_</ic:Argument>  
    </ic:Operation>  
    <wcf:Operation Name="XPath">  
      <wcf:Argument>//Purchase/Payment/CreditCardNumber</wcf:Argument>  
    </wcf:Operation>  
    <ic:Operation Name="Concatenate" />  
  </ic:Expression>  
</ic:ContinuationToken>  
```  
  
## <a name="see-also"></a>另請參閱  
 [攔截器 OnEvent 項目](../core/interceptor-onevent-element.md)