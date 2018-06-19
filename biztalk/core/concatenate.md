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
# <a name="concatenate"></a><span data-ttu-id="54999-102">串連</span><span class="sxs-lookup"><span data-stu-id="54999-102">Concatenate</span></span>
<span data-ttu-id="54999-103">從堆疊移除前兩個項目，串連這兩個項目，然後將結果推入至堆疊。</span><span class="sxs-lookup"><span data-stu-id="54999-103">Removes the top two items from the stack, concatenates them, and then pushes the result onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54999-104">語法</span><span class="sxs-lookup"><span data-stu-id="54999-104">Syntax</span></span>  
  
```  
  
<ic:Operation Name="Concatenate" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="54999-105">參數</span><span class="sxs-lookup"><span data-stu-id="54999-105">Parameters</span></span>  
 <span data-ttu-id="54999-106">堆疊上的前兩個項目。</span><span class="sxs-lookup"><span data-stu-id="54999-106">Top two items on the stack.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="54999-107">推入的值</span><span class="sxs-lookup"><span data-stu-id="54999-107">Pushed Value</span></span>  
 <span data-ttu-id="54999-108">串連作業的字串結果。</span><span class="sxs-lookup"><span data-stu-id="54999-108">String result of the concatenation operation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54999-109">備註</span><span class="sxs-lookup"><span data-stu-id="54999-109">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="54999-110">範例</span><span class="sxs-lookup"><span data-stu-id="54999-110">Example</span></span>  
 <span data-ttu-id="54999-111">在下列範例更新運算式中，常數字串"啟動:"與"EventTime"內容屬性的值串連並保存至資料庫資料行 NewOrderCreateTime。</span><span class="sxs-lookup"><span data-stu-id="54999-111">In the following example update expression, the constant string "Start:" is concatenated with the value of the "EventTime" context property and persisted to the database column NewOrderCreateTime.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="54999-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54999-112">See Also</span></span>  
 [<span data-ttu-id="54999-113">攔截器作業</span><span class="sxs-lookup"><span data-stu-id="54999-113">Interceptor Operations</span></span>](../core/interceptor-operations.md)