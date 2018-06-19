---
title: 使用 GetOperationName |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f858269c-d412-43e3-85e1-398afa9375ab
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04e22020add39840b0d2fe4c2fd88156321a18c7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246134"
---
# <a name="getoperationname"></a><span data-ttu-id="69b3a-102">GetOperationName</span><span class="sxs-lookup"><span data-stu-id="69b3a-102">GetOperationName</span></span>
<span data-ttu-id="69b3a-103">將目前作業的名稱推入到堆疊上。</span><span class="sxs-lookup"><span data-stu-id="69b3a-103">Pushes the name of the current operation onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69b3a-104">語法</span><span class="sxs-lookup"><span data-stu-id="69b3a-104">Syntax</span></span>  
  
```  
  
<wcf:Operation Name="GetOperationName" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69b3a-105">參數</span><span class="sxs-lookup"><span data-stu-id="69b3a-105">Parameters</span></span>  
 <span data-ttu-id="69b3a-106">無。</span><span class="sxs-lookup"><span data-stu-id="69b3a-106">None.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="69b3a-107">推入的值</span><span class="sxs-lookup"><span data-stu-id="69b3a-107">Pushed Value</span></span>  
 <span data-ttu-id="69b3a-108">包含目前作業之名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="69b3a-108">String containing the name of the current operation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69b3a-109">備註</span><span class="sxs-lookup"><span data-stu-id="69b3a-109">Remarks</span></span>  
 <span data-ttu-id="69b3a-110">當使用 GetOperationName 時，請確定將作業名稱比照為應用程式所叫用的作業名稱。</span><span class="sxs-lookup"><span data-stu-id="69b3a-110">When using GetOperationName, make sure you compare the operation name as it is invoked by your application.</span></span> <span data-ttu-id="69b3a-111">例如，如果您使用服務合約上的名稱屬性 (Attribute) 來指派自訂名稱，用戶端便會以方法的自訂名稱來產生其預設 Proxy。</span><span class="sxs-lookup"><span data-stu-id="69b3a-111">For example, if you use the name attribute on a service contract to assign a custom name, the client will have its default proxy generated with the custom name for the method.</span></span> <span data-ttu-id="69b3a-112">然而，伺服器應用程式將會使用對應之作業的實際方法名稱，而不是在名稱屬性中指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="69b3a-112">However, the server application will use the actual method names for the corresponding operations and not the one specified in the name attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69b3a-113">範例</span><span class="sxs-lookup"><span data-stu-id="69b3a-113">Example</span></span>  
 <span data-ttu-id="69b3a-114">下列範例會使用 `GetOperationName`，建置可篩選名為 "AuthorizePayment" 之作業的運算式。</span><span class="sxs-lookup"><span data-stu-id="69b3a-114">In the following sample, `GetOperationName` is used to build an expression that filters for the operation named "AuthorizePayment".</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wcf:Operation Name="GetOperationName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>AuthorizePayment</ic:Argument>  
    </ic:Operation>  
  </ic:Expression>  
</ic:Filter>  
```  
  
## <a name="see-also"></a><span data-ttu-id="69b3a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69b3a-115">See Also</span></span>  
 [<span data-ttu-id="69b3a-116">Windows Communication Foundation 中的作業</span><span class="sxs-lookup"><span data-stu-id="69b3a-116">Operations in Windows Communication Foundation</span></span>](../core/operations-in-windows-communication-foundation.md)