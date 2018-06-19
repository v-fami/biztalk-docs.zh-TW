---
title: GetEndpointName |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5a06850-ff6d-4fe4-9834-61d14b117391
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e7e7a310c222cead89efd23e3f8202ade9eb47ab
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25968756"
---
# <a name="getendpointname"></a><span data-ttu-id="d0bfb-102">GetEndpointName</span><span class="sxs-lookup"><span data-stu-id="d0bfb-102">GetEndpointName</span></span>
<span data-ttu-id="d0bfb-103">將目前攔截端點的名稱推至堆疊上。</span><span class="sxs-lookup"><span data-stu-id="d0bfb-103">Pushes the name of the current interception endpoint onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0bfb-104">語法</span><span class="sxs-lookup"><span data-stu-id="d0bfb-104">Syntax</span></span>  
  
```  
  
<wcf:Operation Name="GetEndpointName" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d0bfb-105">參數</span><span class="sxs-lookup"><span data-stu-id="d0bfb-105">Parameters</span></span>  
 <span data-ttu-id="d0bfb-106">無。</span><span class="sxs-lookup"><span data-stu-id="d0bfb-106">None.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="d0bfb-107">推入的值</span><span class="sxs-lookup"><span data-stu-id="d0bfb-107">Pushed Value</span></span>  
 <span data-ttu-id="d0bfb-108">包含目前攔截端點名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="d0bfb-108">String containing the current interception endpoint name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0bfb-109">備註</span><span class="sxs-lookup"><span data-stu-id="d0bfb-109">Remarks</span></span>  
 <span data-ttu-id="d0bfb-110">請務必注意，對於 App.config 檔案中指定的相同端點名稱，用戶端和伺服器應用程式會傳回不同的名稱。</span><span class="sxs-lookup"><span data-stu-id="d0bfb-110">It is important to note that the client and server applications will return different names for the same endpoint name specified in the App.config files.</span></span>  
  
 <span data-ttu-id="d0bfb-111">在用戶端應用程式方面，GetEndPointName 作業擷取的端點名稱是後面接著底線和合約名稱的繫結名稱。</span><span class="sxs-lookup"><span data-stu-id="d0bfb-111">For client applications, the endpoint name retrieved by the GetEndPointName operation is the binding name followed by an underscore and the contract name.</span></span>  
  
 <span data-ttu-id="d0bfb-112">例如，如果 ServiceEndpoint 上的 [名稱] 屬性未設定，但有設定繫結，名稱會設定為\<*繫結*\>_\<*合約*\>.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-112">For example, if the Name property on ServiceEndpoint is not set but the binding is set, the name will be set to \<*binding*\>_\<*contract*\>.</span></span>  
  
 <span data-ttu-id="d0bfb-113">如果未設定的名稱和繫結，將 [名稱] 屬性設定為\<*合約*\>。</span><span class="sxs-lookup"><span data-stu-id="d0bfb-113">If the name and binding are not set, the Name property will be set to \<*contract*\>.</span></span>  
  
 <span data-ttu-id="d0bfb-114">在服務方面，擷取到的名稱會是指定於 App.config 檔案中的端點名稱。</span><span class="sxs-lookup"><span data-stu-id="d0bfb-114">For the service, the name retrieved is the endpoint name specified in the App.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0bfb-115">範例</span><span class="sxs-lookup"><span data-stu-id="d0bfb-115">Example</span></span>  
 <span data-ttu-id="d0bfb-116">下列範例篩選條件運算式會針對 PurchaseOrder_EP 端點的 ServiceRequest 合約呼叫點，定義其接收作業的攔截。</span><span class="sxs-lookup"><span data-stu-id="d0bfb-116">The following example filter expression defines an interception for the Receive operation for the ServiceRequest contract call point for the PurchaseOrder_EP endpoint.</span></span> <span data-ttu-id="d0bfb-117">這個作業會依照下列邏輯步驟完成：</span><span class="sxs-lookup"><span data-stu-id="d0bfb-117">This is done in the following logical steps:</span></span>  
  
1.  <span data-ttu-id="d0bfb-118">以目前的作業名稱來比較 "Receive"，並將結果 (true 或 false) 推至堆疊上。</span><span class="sxs-lookup"><span data-stu-id="d0bfb-118">Compare the current operation name to "Receive" and push the result (true or false) onto the stack.</span></span>  
  
2.  <span data-ttu-id="d0bfb-119">以目前的服務合約呼叫點來比較 "ServiceRequest"，並將結果 (true 或 false) 推至堆疊上。</span><span class="sxs-lookup"><span data-stu-id="d0bfb-119">Compare the current service contract call point to "ServiceRequest" and push the result (true or false) onto the stack.</span></span> <span data-ttu-id="d0bfb-120">堆疊上現在有兩個布林值。</span><span class="sxs-lookup"><span data-stu-id="d0bfb-120">There are now two Boolean values on the stack.</span></span>  
  
3.  <span data-ttu-id="d0bfb-121">比較使用布林值的上述步驟的結果**和**作業並將結果推至堆疊上的。</span><span class="sxs-lookup"><span data-stu-id="d0bfb-121">Compare the results of the preceding steps using a Boolean **And** operation and push the result on the stack.</span></span> <span data-ttu-id="d0bfb-122">最後堆疊上只會出現一個布林值。</span><span class="sxs-lookup"><span data-stu-id="d0bfb-122">This leaves one Boolean value on the stack.</span></span>  
  
4.  <span data-ttu-id="d0bfb-123">以目前的端點來比較 "PurchaseOrder_EP"，並將結果 (true 或 false) 推至堆疊上。</span><span class="sxs-lookup"><span data-stu-id="d0bfb-123">Compare the current endpoint to "PurchaseOrder_EP" and push the result (true or false) onto the stack.</span></span> <span data-ttu-id="d0bfb-124">堆疊上現在有兩個布林值。</span><span class="sxs-lookup"><span data-stu-id="d0bfb-124">There are now two Boolean values on the stack.</span></span>  
  
5.  <span data-ttu-id="d0bfb-125">最後，比較兩個布林值，使用布林值在堆疊上的**和**作業並將結果推至堆疊。</span><span class="sxs-lookup"><span data-stu-id="d0bfb-125">Finally, compare the two Boolean values on the stack using a Boolean **And** operation and push the result onto the stack.</span></span> <span data-ttu-id="d0bfb-126">這個運算會以某個布林值來檢查端點比較的結果，如果作業名稱和合約呼叫點相符則為 true，否則為 false。</span><span class="sxs-lookup"><span data-stu-id="d0bfb-126">This checks the result of the endpoint comparison against a Boolean value, which is true if the operation name and contract call point successfully matched, and which is false otherwise.</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wcf:Operation Name="GetOperationName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>Receive</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wcf:Operation Name="GetServiceContractCallPoint" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>ServiceRequest</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wcf:Operation Name="GetEndpointName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>PurchaseOrder_EP</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0bfb-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="d0bfb-127">See Also</span></span>  
 [<span data-ttu-id="d0bfb-128">Windows Communication Foundation 中的作業</span><span class="sxs-lookup"><span data-stu-id="d0bfb-128">Operations in Windows Communication Foundation</span></span>](../core/operations-in-windows-communication-foundation.md)