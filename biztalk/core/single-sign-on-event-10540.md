---
title: 單一登入： 事件 10540 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ce91ff30-3d68-4c5f-a955-5c426e94d917
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b1bcd7cc64a79634aa7868791d7e74e92cd1c4a3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990943"
---
# <a name="single-sign-on-event-10540"></a><span data-ttu-id="c0a90-102">單一登入： 事件 10540</span><span class="sxs-lookup"><span data-stu-id="c0a90-102">Single Sign-On: Event 10540</span></span>
## <a name="details"></a><span data-ttu-id="c0a90-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c0a90-103">Details</span></span>  

|                 |                                                                                  |
|-----------------|----------------------------------------------------------------------------------|
|  <span data-ttu-id="c0a90-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c0a90-104">Product Name</span></span>   |                            <span data-ttu-id="c0a90-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="c0a90-105">Enterprise Single Sign-On</span></span>                             |
| <span data-ttu-id="c0a90-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="c0a90-106">Product Version</span></span> |            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]            |
|    <span data-ttu-id="c0a90-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c0a90-107">Event ID</span></span>     |                                      <span data-ttu-id="c0a90-108">10540</span><span class="sxs-lookup"><span data-stu-id="c0a90-108">10540</span></span>                                       |
|  <span data-ttu-id="c0a90-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="c0a90-109">Event Source</span></span>   |                                      <span data-ttu-id="c0a90-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="c0a90-110">ENTSSO</span></span>                                      |
|    <span data-ttu-id="c0a90-111">元件</span><span class="sxs-lookup"><span data-stu-id="c0a90-111">Component</span></span>    |                                        <span data-ttu-id="c0a90-112">CO</span><span class="sxs-lookup"><span data-stu-id="c0a90-112">CO</span></span>                                        |
|  <span data-ttu-id="c0a90-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c0a90-113">Symbolic Name</span></span>  |                         <span data-ttu-id="c0a90-114">SSO_WARN_APP_TICKETS_NOT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="c0a90-114">SSO_WARN_APP_TICKETS_NOT_ALLOWED</span></span>                         |
|  <span data-ttu-id="c0a90-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c0a90-115">Message Text</span></span>   | <span data-ttu-id="c0a90-116">未啟用此 application.%r 的票證</span><span class="sxs-lookup"><span data-stu-id="c0a90-116">Tickets are not enabled for this application.%r</span></span><br /><br /> <span data-ttu-id="c0a90-117">應用程式名稱： %1</span><span class="sxs-lookup"><span data-stu-id="c0a90-117">Application Name: %1</span></span> |

## <a name="explanation"></a><span data-ttu-id="c0a90-118">說明</span><span class="sxs-lookup"><span data-stu-id="c0a90-118">Explanation</span></span>  
 <span data-ttu-id="c0a90-119">這個警告事件指出 「 票證 」 功能，尚未啟用此應用程式。</span><span class="sxs-lookup"><span data-stu-id="c0a90-119">This Warning event indicates that the tickets feature has not been enabled for this application.</span></span> <span data-ttu-id="c0a90-120">使用 SSO 票證是每個 SSO 應用程式的選擇性功能。</span><span class="sxs-lookup"><span data-stu-id="c0a90-120">The use of SSO tickets is an optional feature for each SSO application.</span></span>  

## <a name="user-action"></a><span data-ttu-id="c0a90-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c0a90-121">User Action</span></span>  
 <span data-ttu-id="c0a90-122">若要解決這個警告，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c0a90-122">To resolve this warning, do the following:</span></span>  

- <span data-ttu-id="c0a90-123">請連絡您的應用程式系統管理員啟用此 SSO 應用程式的票證。</span><span class="sxs-lookup"><span data-stu-id="c0a90-123">Contact your Application Administrator to enable tickets for this SSO application.</span></span> <span data-ttu-id="c0a90-124">這可以使用 SSO 管理工具 （GUI 或命令列）。</span><span class="sxs-lookup"><span data-stu-id="c0a90-124">This can be done using the SSO administration tools (GUI or command line).</span></span>  

  <span data-ttu-id="c0a90-125">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="c0a90-125">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="c0a90-126">SSO 票證</span><span class="sxs-lookup"><span data-stu-id="c0a90-126">SSO Tickets</span></span>](../core/sso-tickets.md)  

- [<span data-ttu-id="c0a90-127">如何列出分支機構應用程式屬性</span><span class="sxs-lookup"><span data-stu-id="c0a90-127">How to List the Properties of an Affiliate Application</span></span>](../core/how-to-list-the-properties-of-an-affiliate-application.md)  

- [<span data-ttu-id="c0a90-128">如何更新分支機構應用程式屬性</span><span class="sxs-lookup"><span data-stu-id="c0a90-128">How to Update the Properties of an Affiliate Application</span></span>](../core/how-to-update-the-properties-of-an-affiliate-application.md)
