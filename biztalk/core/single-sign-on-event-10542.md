---
title: 單一登入： 事件 10542 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8e12444-b47c-4919-85b6-85c8e33b8342
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be63569d76bf7c0cfb14cb10bda27b6da52a3efc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979375"
---
# <a name="single-sign-on-event-10542"></a><span data-ttu-id="4b16f-102">單一登入： 事件 10542</span><span class="sxs-lookup"><span data-stu-id="4b16f-102">Single Sign-On: Event 10542</span></span>
## <a name="details"></a><span data-ttu-id="4b16f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4b16f-103">Details</span></span>  

|                 |                                                                                                             |
|-----------------|-------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="4b16f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="4b16f-104">Product Name</span></span>   |                                          <span data-ttu-id="4b16f-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="4b16f-105">Enterprise Single Sign-On</span></span>                                          |
| <span data-ttu-id="4b16f-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="4b16f-106">Product Version</span></span> |                         [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                          |
|    <span data-ttu-id="4b16f-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="4b16f-107">Event ID</span></span>     |                                                    <span data-ttu-id="4b16f-108">10542</span><span class="sxs-lookup"><span data-stu-id="4b16f-108">10542</span></span>                                                    |
|  <span data-ttu-id="4b16f-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="4b16f-109">Event Source</span></span>   |                                                   <span data-ttu-id="4b16f-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="4b16f-110">ENTSSO</span></span>                                                    |
|    <span data-ttu-id="4b16f-111">元件</span><span class="sxs-lookup"><span data-stu-id="4b16f-111">Component</span></span>    |                                                     <span data-ttu-id="4b16f-112">CO</span><span class="sxs-lookup"><span data-stu-id="4b16f-112">CO</span></span>                                                      |
|  <span data-ttu-id="4b16f-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="4b16f-113">Symbolic Name</span></span>  |                                       <span data-ttu-id="4b16f-114">SSO_WARN_APP_TICKETS_VALIDATED</span><span class="sxs-lookup"><span data-stu-id="4b16f-114">SSO_WARN_APP_TICKETS_VALIDATED</span></span>                                        |
|  <span data-ttu-id="4b16f-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="4b16f-115">Message Text</span></span>   | <span data-ttu-id="4b16f-116">無法為此應用程式贖回票證，而不需要 validated.%r</span><span class="sxs-lookup"><span data-stu-id="4b16f-116">Tickets cannot be redeemed for this application without being validated.%r</span></span><br /><br /> <span data-ttu-id="4b16f-117">應用程式名稱： %1</span><span class="sxs-lookup"><span data-stu-id="4b16f-117">Application Name: %1</span></span> |

## <a name="explanation"></a><span data-ttu-id="4b16f-118">說明</span><span class="sxs-lookup"><span data-stu-id="4b16f-118">Explanation</span></span>  
 <span data-ttu-id="4b16f-119">這個警告事件表示，應用程式就無法贖回票證而不需經過。</span><span class="sxs-lookup"><span data-stu-id="4b16f-119">This Warning event indicates that application tickets cannot be redeemed without being validated.</span></span> <span data-ttu-id="4b16f-120">當兌換的票證應用程式是它們可以 validated 或 not validated。</span><span class="sxs-lookup"><span data-stu-id="4b16f-120">When application tickets are redeemed they can be validated or not validated.</span></span> <span data-ttu-id="4b16f-121">驗證會提高安全性，藉由比較的 BizTalk 訊息中的使用者名稱所發行的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="4b16f-121">Validation improves security by comparing the name of the user who issued the ticket with the name of the user in the BizTalk message.</span></span> <span data-ttu-id="4b16f-122">如果名稱不相同驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="4b16f-122">If the names are not the same then validation fails.</span></span> <span data-ttu-id="4b16f-123">BizTalk 訊息流程透過不受信任的主控件，BizTalk 訊息中的使用者名稱會變成不受信任的主機。</span><span class="sxs-lookup"><span data-stu-id="4b16f-123">When a BizTalk message flows through an un-trusted host, the name of the user in the BizTalk message is changed to that of the un-trusted host.</span></span> <span data-ttu-id="4b16f-124">驗證可確保 BizTalk 訊息的信任主機僅流經。</span><span class="sxs-lookup"><span data-stu-id="4b16f-124">Validation ensures that the BizTalk message has only flowed through trusted hosts.</span></span> <span data-ttu-id="4b16f-125">系統層級的應用程式 （因為 SSO 系統 選項設定），驗證是必要的但沒有驗證資訊由呼叫端提供，則此訊息表示特別。</span><span class="sxs-lookup"><span data-stu-id="4b16f-125">This message means specifically that validation is required at the application system level (due to an SSO system option setting), but no validation information was provided by the caller.</span></span>  

## <a name="user-action"></a><span data-ttu-id="4b16f-126">使用者動作</span><span class="sxs-lookup"><span data-stu-id="4b16f-126">User Action</span></span>  
 <span data-ttu-id="4b16f-127">若要解決這個警告，請執行下列一或多個動作：</span><span class="sxs-lookup"><span data-stu-id="4b16f-127">To resolve this warning, do one or more of the following:</span></span>  

- <span data-ttu-id="4b16f-128">如果您使用 BizTalk Server，請確定您的訊息會流經只能透過受信任的主機。</span><span class="sxs-lookup"><span data-stu-id="4b16f-128">If you are using BizTalk Server, ensure that your message is flowing only through trusted hosts.</span></span> <span data-ttu-id="4b16f-129">這會減少訊息中的資料遭竄改的風險。</span><span class="sxs-lookup"><span data-stu-id="4b16f-129">This will reduce the risk of tampering with the data in the message.</span></span>  

- <span data-ttu-id="4b16f-130">如果您的案例允許，請關閉此應用程式的驗證。</span><span class="sxs-lookup"><span data-stu-id="4b16f-130">If your scenario allows it, turn off validation for this application.</span></span> <span data-ttu-id="4b16f-131">驗證是可以在系統或只是此特定應用程式關閉的管理選項。</span><span class="sxs-lookup"><span data-stu-id="4b16f-131">Validation is an administration option which can be turned off for the system or just for this particular application.</span></span>  

  <span data-ttu-id="4b16f-132">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="4b16f-132">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="4b16f-133">SSO 票證</span><span class="sxs-lookup"><span data-stu-id="4b16f-133">SSO Tickets</span></span>](../core/sso-tickets.md)  

- [<span data-ttu-id="4b16f-134">如何列出分支機構應用程式屬性</span><span class="sxs-lookup"><span data-stu-id="4b16f-134">How to List the Properties of an Affiliate Application</span></span>](../core/how-to-list-the-properties-of-an-affiliate-application.md)  

- [<span data-ttu-id="4b16f-135">如何更新分支機構應用程式屬性</span><span class="sxs-lookup"><span data-stu-id="4b16f-135">How to Update the Properties of an Affiliate Application</span></span>](../core/how-to-update-the-properties-of-an-affiliate-application.md)
