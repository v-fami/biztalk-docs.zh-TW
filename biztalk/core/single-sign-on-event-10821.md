---
title: 單一登入： 事件 10821 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2200011e-3e4f-4fe4-b01f-f3b86cdc96db
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d1b9d5499ac11f29034f0110e0ff0fe6850f66a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988079"
---
# <a name="single-sign-on-event-10821"></a><span data-ttu-id="a1fa8-102">單一登入： 事件 10821</span><span class="sxs-lookup"><span data-stu-id="a1fa8-102">Single Sign-On: Event 10821</span></span>
## <a name="details"></a><span data-ttu-id="a1fa8-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a1fa8-103">Details</span></span>  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="a1fa8-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a1fa8-104">Product Name</span></span>   |                             <span data-ttu-id="a1fa8-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="a1fa8-105">Enterprise Single Sign-On</span></span>                              |
| <span data-ttu-id="a1fa8-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="a1fa8-106">Product Version</span></span> |             [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]             |
|    <span data-ttu-id="a1fa8-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a1fa8-107">Event ID</span></span>     |                                       <span data-ttu-id="a1fa8-108">10821</span><span class="sxs-lookup"><span data-stu-id="a1fa8-108">10821</span></span>                                        |
|  <span data-ttu-id="a1fa8-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="a1fa8-109">Event Source</span></span>   |                                       <span data-ttu-id="a1fa8-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="a1fa8-110">ENTSSO</span></span>                                       |
|    <span data-ttu-id="a1fa8-111">元件</span><span class="sxs-lookup"><span data-stu-id="a1fa8-111">Component</span></span>    |                                        <span data-ttu-id="a1fa8-112">不適用</span><span class="sxs-lookup"><span data-stu-id="a1fa8-112">N/A</span></span>                                         |
|  <span data-ttu-id="a1fa8-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a1fa8-113">Symbolic Name</span></span>  |                     <span data-ttu-id="a1fa8-114">ENTSSO_E_ADAPTER_ASSIGNED_TO_GROUP_ADAPTER</span><span class="sxs-lookup"><span data-stu-id="a1fa8-114">ENTSSO_E_ADAPTER_ASSIGNED_TO_GROUP_ADAPTER</span></span>                     |
|  <span data-ttu-id="a1fa8-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a1fa8-115">Message Text</span></span>   | <span data-ttu-id="a1fa8-116">無法刪除配接器，因為它目前指派給群組配接器。</span><span class="sxs-lookup"><span data-stu-id="a1fa8-116">The adapter cannot be deleted because it is currently assigned to a group adapter.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="a1fa8-117">說明</span><span class="sxs-lookup"><span data-stu-id="a1fa8-117">Explanation</span></span>  
 <span data-ttu-id="a1fa8-118">無法刪除配接器，因為它目前指派給群組配接器。</span><span class="sxs-lookup"><span data-stu-id="a1fa8-118">The adapter cannot be deleted because it is currently assigned to a group adapter.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a1fa8-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a1fa8-119">User Action</span></span>  
 <span data-ttu-id="a1fa8-120">取消指派配接器，然後將它刪除。</span><span class="sxs-lookup"><span data-stu-id="a1fa8-120">Unassign the adapter and then delete it.</span></span>