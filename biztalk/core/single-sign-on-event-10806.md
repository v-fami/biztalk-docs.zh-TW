---
title: 單一登入： 事件 10806 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 23650d6b-b6a4-4c41-96cd-476e5b0f7f63
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be61b0a48dde7b1c8de9ec716f4f9426c39fa0cd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002695"
---
# <a name="single-sign-on-event-10806"></a><span data-ttu-id="09489-102">單一登入： 事件 10806</span><span class="sxs-lookup"><span data-stu-id="09489-102">Single Sign-On: Event 10806</span></span>
## <a name="details"></a><span data-ttu-id="09489-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="09489-103">Details</span></span>  
  
|                 |                                                                                   |
|-----------------|-----------------------------------------------------------------------------------|
|  <span data-ttu-id="09489-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="09489-104">Product Name</span></span>   |                             <span data-ttu-id="09489-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="09489-105">Enterprise Single Sign-On</span></span>                             |
| <span data-ttu-id="09489-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="09489-106">Product Version</span></span> |            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]             |
|    <span data-ttu-id="09489-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="09489-107">Event ID</span></span>     |                                       <span data-ttu-id="09489-108">10806</span><span class="sxs-lookup"><span data-stu-id="09489-108">10806</span></span>                                       |
|  <span data-ttu-id="09489-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="09489-109">Event Source</span></span>   |                                      <span data-ttu-id="09489-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="09489-110">ENTSSO</span></span>                                       |
|    <span data-ttu-id="09489-111">元件</span><span class="sxs-lookup"><span data-stu-id="09489-111">Component</span></span>    |                                        <span data-ttu-id="09489-112">不適用</span><span class="sxs-lookup"><span data-stu-id="09489-112">N/A</span></span>                                        |
|  <span data-ttu-id="09489-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="09489-113">Symbolic Name</span></span>  |                         <span data-ttu-id="09489-114">ENTSSO_E_APP_ASSIGNED_TO_ADAPTER</span><span class="sxs-lookup"><span data-stu-id="09489-114">ENTSSO_E_APP_ASSIGNED_TO_ADAPTER</span></span>                          |
|  <span data-ttu-id="09489-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="09489-115">Message Text</span></span>   | <span data-ttu-id="09489-116">無法刪除應用程式，因為它目前指派給配接器。</span><span class="sxs-lookup"><span data-stu-id="09489-116">The application cannot be deleted because it is currently assigned to an adapter.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="09489-117">說明</span><span class="sxs-lookup"><span data-stu-id="09489-117">Explanation</span></span>  
 <span data-ttu-id="09489-118">指派給配接器時，無法刪除應用程式。</span><span class="sxs-lookup"><span data-stu-id="09489-118">An application cannot be deleted when it is assigned to an adapter.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="09489-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="09489-119">User Action</span></span>  
 <span data-ttu-id="09489-120">取消指派的應用程式從配接器，然後再刪除它。</span><span class="sxs-lookup"><span data-stu-id="09489-120">Unassign the application from the adapter, and then delete it.</span></span>