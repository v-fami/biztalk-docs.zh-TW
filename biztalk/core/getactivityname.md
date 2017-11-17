---
title: "GetActivityName |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 479552fa-1535-4f3d-90ff-4615f14c88b1
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 55e8f35746f5f4ed1bbbe10a4d45300895340869
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="getactivityname"></a><span data-ttu-id="9562d-102">GetActivityName</span><span class="sxs-lookup"><span data-stu-id="9562d-102">GetActivityName</span></span>
<span data-ttu-id="9562d-103">將目前活動的名稱推入到堆疊上。</span><span class="sxs-lookup"><span data-stu-id="9562d-103">Pushes the name of the current activity onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9562d-104">語法</span><span class="sxs-lookup"><span data-stu-id="9562d-104">Syntax</span></span>  
  
```  
  
<wf:Operation Name="GetActivityName"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9562d-105">參數</span><span class="sxs-lookup"><span data-stu-id="9562d-105">Parameters</span></span>  
 <span data-ttu-id="9562d-106">無。</span><span class="sxs-lookup"><span data-stu-id="9562d-106">None.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="9562d-107">推入的值</span><span class="sxs-lookup"><span data-stu-id="9562d-107">Pushed Value</span></span>  
 <span data-ttu-id="9562d-108">包含目前活動名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="9562d-108">String containing the current activity name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9562d-109">備註</span><span class="sxs-lookup"><span data-stu-id="9562d-109">Remarks</span></span>  
 <span data-ttu-id="9562d-110">Windows Workflow Foundation 是根據開發人員設定的一系列活動來執行其工作。</span><span class="sxs-lookup"><span data-stu-id="9562d-110">Windows Workflow Foundation performs its work as a series of activities configured by the developer.</span></span> <span data-ttu-id="9562d-111">每一項活動在工作流程內都指派有唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="9562d-111">Each of these activities is assigned a unique name within the workflow.</span></span> <span data-ttu-id="9562d-112">您可以根據唯一名稱進行篩選，來攔截特定活動的資料。</span><span class="sxs-lookup"><span data-stu-id="9562d-112">You can intercept data for a specific activity by filtering based on its unique name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9562d-113">範例</span><span class="sxs-lookup"><span data-stu-id="9562d-113">Example</span></span>  
 <span data-ttu-id="9562d-114">下列範例包含一個事件篩選運算式，這是設定來尋找已關閉工作流程中的特定活動，即 FoodAndDrinksPolicy。</span><span class="sxs-lookup"><span data-stu-id="9562d-114">The following sample contains an event filter expression configured to find a specific activity—FoodAndDrinksPolicy—in a Closed workflow.</span></span> <span data-ttu-id="9562d-115">這是使用包括 `GetActivityName`、`GetActivityEvent` 和邏輯運算等運算組合所完成。</span><span class="sxs-lookup"><span data-stu-id="9562d-115">This is done by using a combination of operations including `GetActivityName`, `GetActivityEvent`, and logical operations.</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>FoodAndDrinksPolicy</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <wf:Operation Name="GetActivityEvent"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <ic:Operation Name="And"/>  
  </ic:Expression>  
</ic:Filter>  
```  
  
 <span data-ttu-id="9562d-116">這種篩選模式常見於 Windows Workflow Foundation 攔截器組態檔。</span><span class="sxs-lookup"><span data-stu-id="9562d-116">This filter pattern is common with Windows Workflow Foundation interceptor configuration files.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9562d-117">引數不需要引號，除非您很明確地要比對包含引號的字串。</span><span class="sxs-lookup"><span data-stu-id="9562d-117">Arguments do not require quotation marks unless you are explicitly trying to match a string that contains quotation marks.</span></span>