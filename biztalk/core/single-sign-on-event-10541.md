---
title: 單一登入： 事件 10541 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7e206158-5652-453c-91ac-9a75ab02809a
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46f3b34c5e57b4fe10a50f684143cc10476e4eaa
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991015"
---
# <a name="single-sign-on-event-10541"></a><span data-ttu-id="66040-102">單一登入： 事件 10541</span><span class="sxs-lookup"><span data-stu-id="66040-102">Single Sign-On: Event 10541</span></span>
## <a name="details"></a><span data-ttu-id="66040-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="66040-103">Details</span></span>  

|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  <span data-ttu-id="66040-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="66040-104">Product Name</span></span>   |                 <span data-ttu-id="66040-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="66040-105">Enterprise Single Sign-On</span></span>                  |
| <span data-ttu-id="66040-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="66040-106">Product Version</span></span> | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    <span data-ttu-id="66040-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="66040-107">Event ID</span></span>     |                           <span data-ttu-id="66040-108">10541</span><span class="sxs-lookup"><span data-stu-id="66040-108">10541</span></span>                            |
|  <span data-ttu-id="66040-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="66040-109">Event Source</span></span>   |                           <span data-ttu-id="66040-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="66040-110">ENTSSO</span></span>                           |
|    <span data-ttu-id="66040-111">元件</span><span class="sxs-lookup"><span data-stu-id="66040-111">Component</span></span>    |                             <span data-ttu-id="66040-112">CO</span><span class="sxs-lookup"><span data-stu-id="66040-112">CO</span></span>                             |
|  <span data-ttu-id="66040-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="66040-113">Symbolic Name</span></span>  |               <span data-ttu-id="66040-114">SSO_WARN_SSO_TICKETS_VALIDATED</span><span class="sxs-lookup"><span data-stu-id="66040-114">SSO_WARN_SSO_TICKETS_VALIDATED</span></span>               |
|  <span data-ttu-id="66040-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="66040-115">Message Text</span></span>   |    <span data-ttu-id="66040-116">不驗證就無法贖回票證。</span><span class="sxs-lookup"><span data-stu-id="66040-116">Tickets cannot be redeemed without being validated.</span></span>     |

## <a name="explanation"></a><span data-ttu-id="66040-117">說明</span><span class="sxs-lookup"><span data-stu-id="66040-117">Explanation</span></span>  
 <span data-ttu-id="66040-118">這個警告事件表示不驗證，無法贖回 SSO 票證。</span><span class="sxs-lookup"><span data-stu-id="66040-118">This Warning event indicates that SSO tickets cannot be redeemed without being validated.</span></span> <span data-ttu-id="66040-119">當會贖回 SSO 票證，他們可以 validated 或 not validated。</span><span class="sxs-lookup"><span data-stu-id="66040-119">When SSO tickets are redeemed they can be validated or not validated.</span></span> <span data-ttu-id="66040-120">驗證會提高安全性，藉由比較的 BizTalk 訊息中的使用者名稱所發行的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="66040-120">Validation improves security by comparing the name of the user who issued the ticket with the name of the user in the BizTalk message.</span></span> <span data-ttu-id="66040-121">如果名稱不相同驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="66040-121">If the names are not the same then validation fails.</span></span> <span data-ttu-id="66040-122">BizTalk 訊息流程透過不受信任的主控件，BizTalk 訊息中的使用者名稱會變成不受信任的主機。</span><span class="sxs-lookup"><span data-stu-id="66040-122">When a BizTalk message flows through an un-trusted host, the name of the user in the BizTalk message is changed to that of the un-trusted host.</span></span> <span data-ttu-id="66040-123">驗證可確保 BizTalk 訊息的信任主機僅流經。</span><span class="sxs-lookup"><span data-stu-id="66040-123">Validation ensures that the BizTalk message has only flowed through trusted hosts.</span></span> <span data-ttu-id="66040-124">在 SSO 系統層級 （因為 SSO 系統 選項設定），驗證是必要的但沒有驗證資訊由呼叫端提供，則此訊息表示特別。</span><span class="sxs-lookup"><span data-stu-id="66040-124">This message means specifically that validation is required at the SSO system level (due to an SSO system option setting), but no validation information was provided by the caller.</span></span>  

## <a name="user-action"></a><span data-ttu-id="66040-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="66040-125">User Action</span></span>  
 <span data-ttu-id="66040-126">若要解決這個警告，請執行下列一或多個動作：</span><span class="sxs-lookup"><span data-stu-id="66040-126">To resolve this warning, do one or more of the following:</span></span>  

- <span data-ttu-id="66040-127">如果您使用 BizTalk Server，請確定您的訊息會流經只能透過受信任的主機。</span><span class="sxs-lookup"><span data-stu-id="66040-127">If you are using BizTalk Server, ensure that your message is flowing only through trusted hosts.</span></span> <span data-ttu-id="66040-128">這會減少訊息中的資料遭竄改的風險。</span><span class="sxs-lookup"><span data-stu-id="66040-128">This will reduce the risk of tampering with the data in the message.</span></span>  

- <span data-ttu-id="66040-129">如果您的案例允許，請關閉此應用程式的驗證。</span><span class="sxs-lookup"><span data-stu-id="66040-129">If your scenario allows it, turn off validation for this application.</span></span> <span data-ttu-id="66040-130">驗證是可以在系統或只是此特定應用程式關閉的管理選項。</span><span class="sxs-lookup"><span data-stu-id="66040-130">Validation is an administration option which can be turned off for the system or just for this particular application.</span></span>  

  <span data-ttu-id="66040-131">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="66040-131">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="66040-132">SSO 票證</span><span class="sxs-lookup"><span data-stu-id="66040-132">SSO Tickets</span></span>](../core/sso-tickets.md)  

- [<span data-ttu-id="66040-133">如何列出分支機構應用程式屬性</span><span class="sxs-lookup"><span data-stu-id="66040-133">How to List the Properties of an Affiliate Application</span></span>](../core/how-to-list-the-properties-of-an-affiliate-application.md)  

- [<span data-ttu-id="66040-134">如何更新分支機構應用程式屬性</span><span class="sxs-lookup"><span data-stu-id="66040-134">How to Update the Properties of an Affiliate Application</span></span>](../core/how-to-update-the-properties-of-an-affiliate-application.md)
