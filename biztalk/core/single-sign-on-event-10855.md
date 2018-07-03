---
title: 單一登入： 事件 10855 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba244f8e-bc61-475f-913c-475ebf1c69ee
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c2d5914cc119a68c109b883c888b3898bc7db07e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986447"
---
# <a name="single-sign-on-event-10855"></a><span data-ttu-id="6a0e4-102">單一登入： 事件 10855</span><span class="sxs-lookup"><span data-stu-id="6a0e4-102">Single Sign-On: Event 10855</span></span>

|                 |                                                                        |
|-----------------|------------------------------------------------------------------------|
|  <span data-ttu-id="6a0e4-103">產品名稱</span><span class="sxs-lookup"><span data-stu-id="6a0e4-103">Product Name</span></span>   |                       <span data-ttu-id="6a0e4-104">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="6a0e4-104">Enterprise Single Sign-On</span></span>                        |
| <span data-ttu-id="6a0e4-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="6a0e4-105">Product Version</span></span> |       [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]       |
|    <span data-ttu-id="6a0e4-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="6a0e4-106">Event ID</span></span>     |                                 <span data-ttu-id="6a0e4-107">10855</span><span class="sxs-lookup"><span data-stu-id="6a0e4-107">10855</span></span>                                  |
|  <span data-ttu-id="6a0e4-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="6a0e4-108">Event Source</span></span>   |                                 <span data-ttu-id="6a0e4-109">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="6a0e4-109">ENTSSO</span></span>                                 |
|    <span data-ttu-id="6a0e4-110">元件</span><span class="sxs-lookup"><span data-stu-id="6a0e4-110">Component</span></span>    |                                  <span data-ttu-id="6a0e4-111">不適用</span><span class="sxs-lookup"><span data-stu-id="6a0e4-111">N/A</span></span>                                   |
|  <span data-ttu-id="6a0e4-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="6a0e4-112">Symbolic Name</span></span>  |                    <span data-ttu-id="6a0e4-113">ENTSSO_E_PASSWORD_FILTER_FAILED</span><span class="sxs-lookup"><span data-stu-id="6a0e4-113">ENTSSO_E_PASSWORD_FILTER_FAILED</span></span>                     |
|  <span data-ttu-id="6a0e4-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="6a0e4-114">Message Text</span></span>   | <span data-ttu-id="6a0e4-115">無法傳回認證，因為密碼篩選失敗。</span><span class="sxs-lookup"><span data-stu-id="6a0e4-115">The credentials cannot be returned because the password filter failed.</span></span> |

## <a name="explanation"></a><span data-ttu-id="6a0e4-116">說明</span><span class="sxs-lookup"><span data-stu-id="6a0e4-116">Explanation</span></span>  
 <span data-ttu-id="6a0e4-117">密碼篩選器不是有效的。</span><span class="sxs-lookup"><span data-stu-id="6a0e4-117">The password filter is not valid.</span></span> <span data-ttu-id="6a0e4-118">這最可能的原因是，篩選手動建立，但不建議這麼做。</span><span class="sxs-lookup"><span data-stu-id="6a0e4-118">The most likely cause of this is that the filter was created manually, which is not recommended.</span></span>  

## <a name="user-action"></a><span data-ttu-id="6a0e4-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="6a0e4-119">User Action</span></span>  
 <span data-ttu-id="6a0e4-120">建立密碼篩選器一次使用 建立篩選器精靈。</span><span class="sxs-lookup"><span data-stu-id="6a0e4-120">Create the password filter again using the Create Filter wizard.</span></span>