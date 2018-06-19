---
title: AutoGenerateCorrelationToken |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a24357c9-34e5-4caa-b41c-19551cfe81f9
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e396fd0b2c6153a5252d336b9af9c22bf9421fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230254"
---
# <a name="autogeneratecorrelationtoken"></a><span data-ttu-id="0cefb-102">AutoGenerateCorrelationToken</span><span class="sxs-lookup"><span data-stu-id="0cefb-102">AutoGenerateCorrelationToken</span></span>
<span data-ttu-id="0cefb-103">自動產生相互關聯 Token 並將它置於堆疊上。</span><span class="sxs-lookup"><span data-stu-id="0cefb-103">Automatically generates a correlation token and places it onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cefb-104">語法</span><span class="sxs-lookup"><span data-stu-id="0cefb-104">Syntax</span></span>  
  
```  
  
<wcf:Operation Name="AutoGenerateCorrelationToken" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0cefb-105">參數</span><span class="sxs-lookup"><span data-stu-id="0cefb-105">Parameters</span></span>  
 <span data-ttu-id="0cefb-106">無。</span><span class="sxs-lookup"><span data-stu-id="0cefb-106">None.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="0cefb-107">推入的值</span><span class="sxs-lookup"><span data-stu-id="0cefb-107">Pushed Value</span></span>  
 <span data-ttu-id="0cefb-108">包含相互關聯 Token 的字串。</span><span class="sxs-lookup"><span data-stu-id="0cefb-108">String containing the correlation token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cefb-109">備註</span><span class="sxs-lookup"><span data-stu-id="0cefb-109">Remarks</span></span>  
 <span data-ttu-id="0cefb-110">訊息中並未存在相互關聯 Token 時可以使用此作業，但您仍想要將要求和回覆中的資訊相互關聯。</span><span class="sxs-lookup"><span data-stu-id="0cefb-110">This operation can be used when there is no correlation token present in the message but you still want to correlate the information from a request and a reply.</span></span> <span data-ttu-id="0cefb-111">此作業可以用來在用戶端或服務端將特定要求/回覆相互關聯。</span><span class="sxs-lookup"><span data-stu-id="0cefb-111">It can be used to correlate a particular request/reply on either the client or the service side.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0cefb-112">如果想將用戶端和服務 (接續) 之要求和回覆所收集的資料相互關聯，就必須使用您訊息中的資料元素或元素。</span><span class="sxs-lookup"><span data-stu-id="0cefb-112">If you want to correlate the data gathered by the request and the reply for both the client and the service (a continuation), you will need to use a data element or elements from your message.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cefb-113">範例</span><span class="sxs-lookup"><span data-stu-id="0cefb-113">Example</span></span>  
 <span data-ttu-id="0cefb-114">下列範例相互關聯運算式依賴 `AutoGenerateCorrelationToken` 來產生相互關聯 Token。</span><span class="sxs-lookup"><span data-stu-id="0cefb-114">The following example correlation expression relies on the `AutoGenerateCorrelationToken` to generate a correlation token.</span></span>  
  
```  
<ic:CorrelationID>  
  <ic:Expression>            
    <wcf:Operation Name="AutoGenerateCorrelationToken"/>  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0cefb-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cefb-115">See Also</span></span>  
 [<span data-ttu-id="0cefb-116">Windows Communication Foundation 中的作業</span><span class="sxs-lookup"><span data-stu-id="0cefb-116">Operations in Windows Communication Foundation</span></span>](../core/operations-in-windows-communication-foundation.md)