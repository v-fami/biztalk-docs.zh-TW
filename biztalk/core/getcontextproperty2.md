---
title: GetContextProperty2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2554a210-cfb4-4b63-9afa-ffe2a853ba7b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f834bf1271f6706c332123d8b1835e0bd730f069
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246142"
---
# <a name="getcontextproperty"></a><span data-ttu-id="528dc-102">GetContextProperty</span><span class="sxs-lookup"><span data-stu-id="528dc-102">GetContextProperty</span></span>
<span data-ttu-id="528dc-103">將要求的內容屬性推入到堆疊上。</span><span class="sxs-lookup"><span data-stu-id="528dc-103">Pushes the requested context property onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="528dc-104">語法</span><span class="sxs-lookup"><span data-stu-id="528dc-104">Syntax</span></span>  
  
```  
  
<wf:Operation Name="GetContextProperty">  
  <wf:Argument>ContextPropertyName</wf:Argument>  
</wf:Operation>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="528dc-105">參數</span><span class="sxs-lookup"><span data-stu-id="528dc-105">Parameters</span></span>  
 <span data-ttu-id="528dc-106">下列其中一種內容屬性名稱：</span><span class="sxs-lookup"><span data-stu-id="528dc-106">One of the following context property names:</span></span>  
  
|<span data-ttu-id="528dc-107">內容屬性名稱</span><span class="sxs-lookup"><span data-stu-id="528dc-107">Context property name</span></span>|<span data-ttu-id="528dc-108">說明</span><span class="sxs-lookup"><span data-stu-id="528dc-108">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="528dc-109">EventTime</span><span class="sxs-lookup"><span data-stu-id="528dc-109">EventTime</span></span>|<span data-ttu-id="528dc-110">目前的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="528dc-110">Current date and time.</span></span>|  
|<span data-ttu-id="528dc-111">InstanceId</span><span class="sxs-lookup"><span data-stu-id="528dc-111">InstanceId</span></span>|<span data-ttu-id="528dc-112">工作流程執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="528dc-112">Workflow instance ID.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="528dc-113">內容屬性名稱有區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="528dc-113">The context property names are case-sensitive.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="528dc-114">推入的值</span><span class="sxs-lookup"><span data-stu-id="528dc-114">Pushed Value</span></span>  
 <span data-ttu-id="528dc-115">包含所要求內容屬性的字串。</span><span class="sxs-lookup"><span data-stu-id="528dc-115">String containing the requested context property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="528dc-116">備註</span><span class="sxs-lookup"><span data-stu-id="528dc-116">Remarks</span></span>  
 <span data-ttu-id="528dc-117">時間會以 UTC 格式儲存在資料庫內部。</span><span class="sxs-lookup"><span data-stu-id="528dc-117">Time is stored in UTC format inside of the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="528dc-118">範例</span><span class="sxs-lookup"><span data-stu-id="528dc-118">Example</span></span>  
 <span data-ttu-id="528dc-119">在下列範例中，提取運算式**InstanceId**在 correlationID 區塊內用來設定相互關聯識別碼。</span><span class="sxs-lookup"><span data-stu-id="528dc-119">In the following sample, an expression for pulling the **InstanceId** is used inside of a correlationID block to set the correlation ID.</span></span>  
  
```  
<ic:CorrelationID>  
  <ic:Expression>  
    <wf:Operation Name="GetContextProperty">  
      <wf:Argument>InstanceId</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
 <span data-ttu-id="528dc-120">這是 `GetContextProperty` 的常見用途。</span><span class="sxs-lookup"><span data-stu-id="528dc-120">This is a common use of `GetContextProperty`.</span></span>