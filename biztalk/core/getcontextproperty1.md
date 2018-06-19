---
title: GetContextProperty1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8867c29-63de-4a13-9ef9-8c6ab8ea3443
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 65b7ffffe4b21e3317b920ac50cdc27b12d708d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246262"
---
# <a name="getcontextproperty"></a><span data-ttu-id="bb0e6-102">GetContextProperty</span><span class="sxs-lookup"><span data-stu-id="bb0e6-102">GetContextProperty</span></span>
<span data-ttu-id="bb0e6-103">將要求的內容屬性推入到堆疊上。</span><span class="sxs-lookup"><span data-stu-id="bb0e6-103">Pushes the requested context property onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb0e6-104">語法</span><span class="sxs-lookup"><span data-stu-id="bb0e6-104">Syntax</span></span>  
  
```  
  
<wcf:Operation Name ="GetContextProperty">  
  <wcf:Argument>EventTime</wcf:Argument>  
</wcf:Operation>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb0e6-105">參數</span><span class="sxs-lookup"><span data-stu-id="bb0e6-105">Parameters</span></span>  
 <span data-ttu-id="bb0e6-106">下列其中一種內容屬性名稱：</span><span class="sxs-lookup"><span data-stu-id="bb0e6-106">One of the following context property names:</span></span>  
  
|<span data-ttu-id="bb0e6-107">內容屬性名稱</span><span class="sxs-lookup"><span data-stu-id="bb0e6-107">Context property name</span></span>|<span data-ttu-id="bb0e6-108">說明</span><span class="sxs-lookup"><span data-stu-id="bb0e6-108">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="bb0e6-109">EventTime</span><span class="sxs-lookup"><span data-stu-id="bb0e6-109">EventTime</span></span>|<span data-ttu-id="bb0e6-110">目前的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="bb0e6-110">Current date and time.</span></span>|  
|<span data-ttu-id="bb0e6-111">SessionId</span><span class="sxs-lookup"><span data-stu-id="bb0e6-111">SessionId</span></span>|<span data-ttu-id="bb0e6-112">工作流程工作階段識別碼。</span><span class="sxs-lookup"><span data-stu-id="bb0e6-112">Workflow session id.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="bb0e6-113">內容屬性名稱有區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="bb0e6-113">The context property names are case-sensitive.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="bb0e6-114">推入的值</span><span class="sxs-lookup"><span data-stu-id="bb0e6-114">Pushed Value</span></span>  
 <span data-ttu-id="bb0e6-115">包含所要求內容屬性的字串。</span><span class="sxs-lookup"><span data-stu-id="bb0e6-115">String containing the requested context property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb0e6-116">備註</span><span class="sxs-lookup"><span data-stu-id="bb0e6-116">Remarks</span></span>  
 <span data-ttu-id="bb0e6-117">時間會以 UTC 格式儲存在資料庫內部。</span><span class="sxs-lookup"><span data-stu-id="bb0e6-117">Time is stored in UTC format inside of the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb0e6-118">範例</span><span class="sxs-lookup"><span data-stu-id="bb0e6-118">Example</span></span>  
 <span data-ttu-id="bb0e6-119">在下列範例更新運算式中，核准日期是以擷取目前事件之事件時間方式擷取所得。</span><span class="sxs-lookup"><span data-stu-id="bb0e6-119">In the following sample update expression, the approval date is retrieved by retrieving the event time of the current event.</span></span>  
  
```  
<ic:Update DataItemName ="Approval Date" Type ="DATETIME">  
  <ic:Expression>  
    <wcf:Operation Name ="GetContextProperty">  
      <wcf:Argument>EventTime</wcf:Argument>  
    </wcf:Operation>  
  </ic:Expression>  
</ic:Update>  
```  
  
 <span data-ttu-id="bb0e6-120">這是 `GetContextProperty` 的常見用途。</span><span class="sxs-lookup"><span data-stu-id="bb0e6-120">This is a common use of `GetContextProperty`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb0e6-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb0e6-121">See Also</span></span>  
 [<span data-ttu-id="bb0e6-122">Windows Communication Foundation 中的作業</span><span class="sxs-lookup"><span data-stu-id="bb0e6-122">Operations in Windows Communication Foundation</span></span>](../core/operations-in-windows-communication-foundation.md)