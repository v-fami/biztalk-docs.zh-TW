---
title: 單一登入： 事件 10543 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46b1ffda-a6c1-408c-acb4-074183d697bc
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf5c026384bf463f6ee0a33045dd1e7b1fca4188
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998441"
---
# <a name="single-sign-on-event-10543"></a><span data-ttu-id="0cebf-102">單一登入： 事件 10543</span><span class="sxs-lookup"><span data-stu-id="0cebf-102">Single Sign-On: Event 10543</span></span>
## <a name="details"></a><span data-ttu-id="0cebf-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0cebf-103">Details</span></span>  

|                 |                                                                                                                                                        |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="0cebf-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0cebf-104">Product Name</span></span>   |                                                               <span data-ttu-id="0cebf-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="0cebf-105">Enterprise Single Sign-On</span></span>                                                                |
| <span data-ttu-id="0cebf-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="0cebf-106">Product Version</span></span> |                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                               |
|    <span data-ttu-id="0cebf-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0cebf-107">Event ID</span></span>     |                                                                         <span data-ttu-id="0cebf-108">10543</span><span class="sxs-lookup"><span data-stu-id="0cebf-108">10543</span></span>                                                                          |
|  <span data-ttu-id="0cebf-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="0cebf-109">Event Source</span></span>   |                                                                         <span data-ttu-id="0cebf-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="0cebf-110">ENTSSO</span></span>                                                                         |
|    <span data-ttu-id="0cebf-111">元件</span><span class="sxs-lookup"><span data-stu-id="0cebf-111">Component</span></span>    |                                                                           <span data-ttu-id="0cebf-112">CO</span><span class="sxs-lookup"><span data-stu-id="0cebf-112">CO</span></span>                                                                           |
|  <span data-ttu-id="0cebf-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0cebf-113">Symbolic Name</span></span>  |                                                           <span data-ttu-id="0cebf-114">SSO_WARN_ORIGINAL_TICKET_VALIDATED</span><span class="sxs-lookup"><span data-stu-id="0cebf-114">SSO_WARN_ORIGINAL_TICKET_VALIDATED</span></span>                                                           |
|  <span data-ttu-id="0cebf-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0cebf-115">Message Text</span></span>   | <span data-ttu-id="0cebf-116">核發此票證時需要驗證。</span><span class="sxs-lookup"><span data-stu-id="0cebf-116">The ticket was issued with validation required.</span></span> <span data-ttu-id="0cebf-117">即無法兌換此應用程式不含 validated.%r</span><span class="sxs-lookup"><span data-stu-id="0cebf-117">It cannot be redeemed for this application without being validated.%r</span></span><br /><br /> <span data-ttu-id="0cebf-118">應用程式名稱： %1</span><span class="sxs-lookup"><span data-stu-id="0cebf-118">Application Name: %1</span></span> |

## <a name="explanation"></a><span data-ttu-id="0cebf-119">說明</span><span class="sxs-lookup"><span data-stu-id="0cebf-119">Explanation</span></span>  
 <span data-ttu-id="0cebf-120">這個警告事件表示應用程式票證核發需要驗證。</span><span class="sxs-lookup"><span data-stu-id="0cebf-120">This Warning event indicates that an application ticket was issued with validation required.</span></span> <span data-ttu-id="0cebf-121">不驗證就無法贖回票證。</span><span class="sxs-lookup"><span data-stu-id="0cebf-121">Tickets cannot be redeemed without being validated.</span></span> <span data-ttu-id="0cebf-122">驗證票證位於每個分支機構應用程式為基礎。</span><span class="sxs-lookup"><span data-stu-id="0cebf-122">Validation of the ticket is on a per affiliate application basis.</span></span>  

## <a name="user-action"></a><span data-ttu-id="0cebf-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0cebf-123">User Action</span></span>  
 <span data-ttu-id="0cebf-124">若要解決這個警告，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="0cebf-124">To resolve this warning, do the following:</span></span>  

- <span data-ttu-id="0cebf-125">如果您使用企業單一登入，請確定您的訊息會流經只能透過受信任的主機。</span><span class="sxs-lookup"><span data-stu-id="0cebf-125">If you are using Enterprise Single Sign-On, ensure that your message is flowing only through trusted hosts.</span></span> <span data-ttu-id="0cebf-126">這會減少訊息中的資料遭竄改的風險。</span><span class="sxs-lookup"><span data-stu-id="0cebf-126">This will reduce the risk of tampering with the data in the message.</span></span>  

- <span data-ttu-id="0cebf-127">如果您的案例允許，請關閉此應用程式的驗證。</span><span class="sxs-lookup"><span data-stu-id="0cebf-127">If your scenario allows it, turn off validation for this application.</span></span> <span data-ttu-id="0cebf-128">驗證是可以在系統或只是此特定應用程式關閉的管理選項。</span><span class="sxs-lookup"><span data-stu-id="0cebf-128">Validation is an administration option which can be turned off for the system or just for this particular application.</span></span>  

  <span data-ttu-id="0cebf-129">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="0cebf-129">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="0cebf-130">SSO 票證</span><span class="sxs-lookup"><span data-stu-id="0cebf-130">SSO Tickets</span></span>](../core/sso-tickets.md)  

- [<span data-ttu-id="0cebf-131">如何列出分支機構應用程式屬性</span><span class="sxs-lookup"><span data-stu-id="0cebf-131">How to List the Properties of an Affiliate Application</span></span>](../core/how-to-list-the-properties-of-an-affiliate-application.md)  

- [<span data-ttu-id="0cebf-132">如何更新分支機構應用程式屬性</span><span class="sxs-lookup"><span data-stu-id="0cebf-132">How to Update the Properties of an Affiliate Application</span></span>](../core/how-to-update-the-properties-of-an-affiliate-application.md)
