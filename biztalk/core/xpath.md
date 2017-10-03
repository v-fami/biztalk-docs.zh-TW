---
title: "XPath |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 444b5eb9-0c00-4225-918e-b973532c67d0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ee46838596a55512df5d1476f2c3ba34b1f5cb9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="xpath"></a>XPath
推入 XPath 陳述式所指定的值。  
  
## <a name="syntax"></a>語法  
  
```  
  
<wcf:Operation Name="XPath">  
  <wcf:Argument>//po:POID</wcf:Argument>  
</wcf:Operation>  
```  
  
#### <a name="parameters"></a>參數  
 有效的 XPath 陳述式。  
  
## <a name="pushed-value"></a>推入的值  
 執行 XPath 陳述式所得結果的字串值。  
  
## <a name="remarks"></a>備註  
 您必須使用有效的 XPath 陳述式。  
  
 若有多個符合項目，則只會使用第一個符合項目。  
  
## <a name="example"></a>範例  
 下列範例運算式會將常數 "C_" 與目前訊息中的訂單識別碼串連起來，以建構相互關聯值。 訂單識別碼會使用 XPath 作業來擷取。  
  
```  
<ic:CorrelationID>  
  <ic:Expression>  
    <ic:Operation Name="Constant">  
      <ic:Argument>C_</ic:Argument>  
    </ic:Operation>  
    <wcf:Operation Name="XPath">  
      <wcf:Argument>//po:POID</wcf:Argument>  
    </wcf:Operation>  
    <ic:Operation Name="Concatenate" />  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Windows Communication Foundation 中的作業](../core/operations-in-windows-communication-foundation.md)