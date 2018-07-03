---
title: 單一登入： 事件 10830 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd149be1-0a4f-4d39-9b0e-35202dc140cb
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 28bd8c50fecf5fec1f9e1ed6c6414ed4d852f877
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37019092"
---
# <a name="single-sign-on-event-10830"></a><span data-ttu-id="e622e-102">單一登入： 事件 10830</span><span class="sxs-lookup"><span data-stu-id="e622e-102">Single Sign-On: Event 10830</span></span>
## <a name="details"></a><span data-ttu-id="e622e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e622e-103">Details</span></span>  
  
|                 |                                                                          |
|-----------------|--------------------------------------------------------------------------|
|  <span data-ttu-id="e622e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e622e-104">Product Name</span></span>   |                        <span data-ttu-id="e622e-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="e622e-105">Enterprise Single Sign-On</span></span>                         |
| <span data-ttu-id="e622e-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="e622e-106">Product Version</span></span> |        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]        |
|    <span data-ttu-id="e622e-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e622e-107">Event ID</span></span>     |                                  <span data-ttu-id="e622e-108">10830</span><span class="sxs-lookup"><span data-stu-id="e622e-108">10830</span></span>                                   |
|  <span data-ttu-id="e622e-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="e622e-109">Event Source</span></span>   |                                  <span data-ttu-id="e622e-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="e622e-110">ENTSSO</span></span>                                  |
|    <span data-ttu-id="e622e-111">元件</span><span class="sxs-lookup"><span data-stu-id="e622e-111">Component</span></span>    |                                   <span data-ttu-id="e622e-112">不適用</span><span class="sxs-lookup"><span data-stu-id="e622e-112">N/A</span></span>                                    |
|  <span data-ttu-id="e622e-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e622e-113">Symbolic Name</span></span>  |                  <span data-ttu-id="e622e-114">ENTSSO_E_PSADMIN_ADAPTER_SAME_COMPUTER</span><span class="sxs-lookup"><span data-stu-id="e622e-114">ENTSSO_E_PSADMIN_ADAPTER_SAME_COMPUTER</span></span>                  |
|  <span data-ttu-id="e622e-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e622e-115">Message Text</span></span>   | <span data-ttu-id="e622e-116">指定的配接器必須是群組配接器的同一部電腦上。</span><span class="sxs-lookup"><span data-stu-id="e622e-116">The specified adapter must be on the same computer as the group adapter.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="e622e-117">說明</span><span class="sxs-lookup"><span data-stu-id="e622e-117">Explanation</span></span>  
 <span data-ttu-id="e622e-118">群組配接器中的每個介面卡必須設定與群組配接器的電腦名稱相同。</span><span class="sxs-lookup"><span data-stu-id="e622e-118">Each adapter in a group adapter must be configured with the same computer name as the group adapter.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e622e-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e622e-119">User Action</span></span>  
 <span data-ttu-id="e622e-120">如需詳細資訊，請參閱[密碼同步處理](../core/password-synchronization2.md)</span><span class="sxs-lookup"><span data-stu-id="e622e-120">For more information, see [Password Synchronization](../core/password-synchronization2.md)</span></span>  
  
 <span data-ttu-id="e622e-121">執行個體時提供 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="e622e-121">.</span></span>