---
title: 串連 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e21a773d-a9cc-4a6f-b548-46badcd92aab
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4766f65fb0cbe26c8f3c545c38235d83abb283a4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231694"
---
# <a name="concatenate"></a>串連
從堆疊移除前兩個項目，串連這兩個項目，然後將結果推入至堆疊。  
  
## <a name="syntax"></a>語法  
  
```  
  
<ic:Operation Name="Concatenate" />  
```  
  
#### <a name="parameters"></a>參數  
 堆疊上的前兩個項目。  
  
## <a name="pushed-value"></a>推入的值  
 串連作業的字串結果。  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 在下列範例更新運算式中，常數字串"啟動:"與"EventTime"內容屬性的值串連並保存至資料庫資料行 NewOrderCreateTime。  
  
```  
<ic:Update DataItemName="NewOrderCreateTime" Type="NVARCHAR">  
  <ic:Expression>  
    <ic:Operation Name="Constant">  
      <ic:Argument>Start:</ic:Argument>  
    </ic:Operation>  
    <wf:Operation Name="GetContextProperty">  
      <wf:Argument>EventTime</wf:Argument>  
    </wf:Operation>  
    <ic:Operation Name="Concatenate" />  
  </ic:Expression>  
</ic:Update>  
```  
  
## <a name="see-also"></a>另請參閱  
 [攔截器作業](../core/interceptor-operations.md)