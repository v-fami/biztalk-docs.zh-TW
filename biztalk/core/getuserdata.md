---
title: GetUserData |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c243555b-109f-47e3-8084-ab13a8e22ac5
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57bc0ffcefc00e9fae20c7b2c8449c21c549b377
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246382"
---
# <a name="getuserdata"></a><span data-ttu-id="a34db-102">GetUserData</span><span class="sxs-lookup"><span data-stu-id="a34db-102">GetUserData</span></span>
<span data-ttu-id="a34db-103">將目前的使用者資料推到堆疊上。</span><span class="sxs-lookup"><span data-stu-id="a34db-103">Pushes the current user data onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a34db-104">語法</span><span class="sxs-lookup"><span data-stu-id="a34db-104">Syntax</span></span>  
  
```  
  
<wf:Operation Name="GetUserData" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a34db-105">參數</span><span class="sxs-lookup"><span data-stu-id="a34db-105">Parameters</span></span>  
 <span data-ttu-id="a34db-106">無。</span><span class="sxs-lookup"><span data-stu-id="a34db-106">None.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="a34db-107">推入的值</span><span class="sxs-lookup"><span data-stu-id="a34db-107">Pushed Value</span></span>  
 <span data-ttu-id="a34db-108">包含目前使用者資料的字串。</span><span class="sxs-lookup"><span data-stu-id="a34db-108">String containing the current user data.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a34db-109">備註</span><span class="sxs-lookup"><span data-stu-id="a34db-109">Remarks</span></span>  
 <span data-ttu-id="a34db-110">這個作業在篩選內部無效。</span><span class="sxs-lookup"><span data-stu-id="a34db-110">This operation is not valid inside of a filter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a34db-111">範例</span><span class="sxs-lookup"><span data-stu-id="a34db-111">Example</span></span>  
 <span data-ttu-id="a34db-112">下列範例會使用 `GetUserData` 作業，包含資料項目 "UserData" 的更新運算式。</span><span class="sxs-lookup"><span data-stu-id="a34db-112">The following sample contains an update expression for the data item "UserData" using the `GetUserData` operation.</span></span>  
  
```  
<ic:Update DataItemName="UserData" Type="NVARCHAR">  
  <ic:Expression>  
    <wf:Operation Name="GetUserData" />  
  </ic:Expression>  
</ic:Update>  
```