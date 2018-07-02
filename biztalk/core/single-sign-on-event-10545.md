---
title: 單一登入： 事件 10545 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 268cb7be-b191-4335-a4cc-7c15d879507c
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a21543359b9a0d59aba3071874b6b01210118a5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969127"
---
# <a name="single-sign-on-event-10545"></a><span data-ttu-id="19d76-102">單一登入： 事件 10545</span><span class="sxs-lookup"><span data-stu-id="19d76-102">Single Sign-On: Event 10545</span></span>
## <a name="details"></a><span data-ttu-id="19d76-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="19d76-103">Details</span></span>  

|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  <span data-ttu-id="19d76-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="19d76-104">Product Name</span></span>   |                 <span data-ttu-id="19d76-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="19d76-105">Enterprise Single Sign-On</span></span>                  |
| <span data-ttu-id="19d76-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="19d76-106">Product Version</span></span> | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    <span data-ttu-id="19d76-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="19d76-107">Event ID</span></span>     |                           <span data-ttu-id="19d76-108">10545</span><span class="sxs-lookup"><span data-stu-id="19d76-108">10545</span></span>                            |
|  <span data-ttu-id="19d76-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="19d76-109">Event Source</span></span>   |                           <span data-ttu-id="19d76-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="19d76-110">ENTSSO</span></span>                           |
|    <span data-ttu-id="19d76-111">元件</span><span class="sxs-lookup"><span data-stu-id="19d76-111">Component</span></span>    |                             <span data-ttu-id="19d76-112">CO</span><span class="sxs-lookup"><span data-stu-id="19d76-112">CO</span></span>                             |
|  <span data-ttu-id="19d76-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="19d76-113">Symbolic Name</span></span>  |             <span data-ttu-id="19d76-114">SSO_WARN_ISSUE_TICKETS_NOT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="19d76-114">SSO_WARN_ISSUE_TICKETS_NOT_ALLOWED</span></span>             |
|  <span data-ttu-id="19d76-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="19d76-115">Message Text</span></span>   |        <span data-ttu-id="19d76-116">未啟用 SSO 系統的票證。</span><span class="sxs-lookup"><span data-stu-id="19d76-116">Tickets are not enabled for the SSO system.</span></span>         |

## <a name="explanation"></a><span data-ttu-id="19d76-117">說明</span><span class="sxs-lookup"><span data-stu-id="19d76-117">Explanation</span></span>  
 <span data-ttu-id="19d76-118">這個警告事件表示 SSO 系統不會啟用票證。</span><span class="sxs-lookup"><span data-stu-id="19d76-118">This Warning event indicates that tickets are not enabled for the SSO System.</span></span> <span data-ttu-id="19d76-119">如果在系統層級停用票證，票證目前無法使用的分支機構應用程式層級是。</span><span class="sxs-lookup"><span data-stu-id="19d76-119">If ticketing is disabled at the system level, ticketing cannot be used at the Affiliate Application level either.</span></span> <span data-ttu-id="19d76-120">可以在系統層級中啟用票證，然後在分支機構應用程式層級中將它停用。</span><span class="sxs-lookup"><span data-stu-id="19d76-120">It is possible to enable tickets at the system level and disable it at the Affiliate Application level.</span></span>  

## <a name="user-action"></a><span data-ttu-id="19d76-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="19d76-121">User Action</span></span>  
 <span data-ttu-id="19d76-122">若要解決這個警告，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="19d76-122">To resolve this warning, do the following:</span></span>  

- <span data-ttu-id="19d76-123">啟用 SSO 系統層級的票證。</span><span class="sxs-lookup"><span data-stu-id="19d76-123">Enable tickets at the SSO System level.</span></span>  

  <span data-ttu-id="19d76-124">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="19d76-124">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="19d76-125">SSO 票證</span><span class="sxs-lookup"><span data-stu-id="19d76-125">SSO Tickets</span></span>](../core/sso-tickets.md)  

- [<span data-ttu-id="19d76-126">如何設定 SSO 票證</span><span class="sxs-lookup"><span data-stu-id="19d76-126">How to Configure the SSO Tickets</span></span>](../core/how-to-configure-the-sso-tickets.md)
