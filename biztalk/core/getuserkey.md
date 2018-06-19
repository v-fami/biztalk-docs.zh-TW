---
title: GetUserKey |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9353a7f0-9bbd-4cfa-92e6-ed2b86e3a88e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0701ff1df912cc113205bad573b6cebc0f02a13a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246118"
---
# <a name="getuserkey"></a><span data-ttu-id="6590f-102">GetUserKey</span><span class="sxs-lookup"><span data-stu-id="6590f-102">GetUserKey</span></span>
<span data-ttu-id="6590f-103">將目前的使用者金鑰推入到堆疊上。</span><span class="sxs-lookup"><span data-stu-id="6590f-103">Pushes the current user key onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6590f-104">語法</span><span class="sxs-lookup"><span data-stu-id="6590f-104">Syntax</span></span>  
  
```  
  
<wf:Operation Name="GetUserKey" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6590f-105">參數</span><span class="sxs-lookup"><span data-stu-id="6590f-105">Parameters</span></span>  
 <span data-ttu-id="6590f-106">無。</span><span class="sxs-lookup"><span data-stu-id="6590f-106">None.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="6590f-107">推入的值</span><span class="sxs-lookup"><span data-stu-id="6590f-107">Pushed Value</span></span>  
 <span data-ttu-id="6590f-108">包含目前使用者金鑰的字串。</span><span class="sxs-lookup"><span data-stu-id="6590f-108">String containing the current user key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6590f-109">備註</span><span class="sxs-lookup"><span data-stu-id="6590f-109">Remarks</span></span>  
 <span data-ttu-id="6590f-110">此作業只在使用者追蹤點內有效。</span><span class="sxs-lookup"><span data-stu-id="6590f-110">This operation is valid only in user track points.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6590f-111">範例</span><span class="sxs-lookup"><span data-stu-id="6590f-111">Example</span></span>  
 <span data-ttu-id="6590f-112">下列範例包含的事件篩選器運算式，會在使用者金鑰等於 "DocumentUrl" 時評估為 `true`。</span><span class="sxs-lookup"><span data-stu-id="6590f-112">The following sample contains an event filter expression that will evaluate to `true` when the user key is equal to "DocumentUrl".</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>DocumentUrl</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
  </ic:Expression>  
</ic:Filter>  
```