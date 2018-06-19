---
title: XPath |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 444b5eb9-0c00-4225-918e-b973532c67d0
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ee46838596a55512df5d1476f2c3ba34b1f5cb9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289646"
---
# <a name="xpath"></a><span data-ttu-id="8c089-102">XPath</span><span class="sxs-lookup"><span data-stu-id="8c089-102">XPath</span></span>
<span data-ttu-id="8c089-103">推入 XPath 陳述式所指定的值。</span><span class="sxs-lookup"><span data-stu-id="8c089-103">Pushes the value indicated by an XPath statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c089-104">語法</span><span class="sxs-lookup"><span data-stu-id="8c089-104">Syntax</span></span>  
  
```  
  
<wcf:Operation Name="XPath">  
  <wcf:Argument>//po:POID</wcf:Argument>  
</wcf:Operation>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c089-105">參數</span><span class="sxs-lookup"><span data-stu-id="8c089-105">Parameters</span></span>  
 <span data-ttu-id="8c089-106">有效的 XPath 陳述式。</span><span class="sxs-lookup"><span data-stu-id="8c089-106">Valid XPath statement.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="8c089-107">推入的值</span><span class="sxs-lookup"><span data-stu-id="8c089-107">Pushed Value</span></span>  
 <span data-ttu-id="8c089-108">執行 XPath 陳述式所得結果的字串值。</span><span class="sxs-lookup"><span data-stu-id="8c089-108">String value of the result found by executing the XPath statement.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c089-109">備註</span><span class="sxs-lookup"><span data-stu-id="8c089-109">Remarks</span></span>  
 <span data-ttu-id="8c089-110">您必須使用有效的 XPath 陳述式。</span><span class="sxs-lookup"><span data-stu-id="8c089-110">You must use a valid XPath statement.</span></span>  
  
 <span data-ttu-id="8c089-111">若有多個符合項目，則只會使用第一個符合項目。</span><span class="sxs-lookup"><span data-stu-id="8c089-111">In the case of multiple matches, only the first match is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c089-112">範例</span><span class="sxs-lookup"><span data-stu-id="8c089-112">Example</span></span>  
 <span data-ttu-id="8c089-113">下列範例運算式會將常數 "C_" 與目前訊息中的訂單識別碼串連起來，以建構相互關聯值。</span><span class="sxs-lookup"><span data-stu-id="8c089-113">The following example expression constructs a correlation value by concatenating a constant "C_" with the purchase order ID from the current message.</span></span> <span data-ttu-id="8c089-114">訂單識別碼會使用 XPath 作業來擷取。</span><span class="sxs-lookup"><span data-stu-id="8c089-114">The purchase order ID is retrieved by using the XPath operation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8c089-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c089-115">See Also</span></span>  
 [<span data-ttu-id="8c089-116">Windows Communication Foundation 中的作業</span><span class="sxs-lookup"><span data-stu-id="8c089-116">Operations in Windows Communication Foundation</span></span>](../core/operations-in-windows-communication-foundation.md)