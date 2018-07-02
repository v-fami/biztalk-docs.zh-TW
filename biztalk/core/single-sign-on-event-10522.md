---
title: 單一登入： 事件 10522 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd634a57-01dc-44bd-bcf9-668689db7b77
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4f8bb97c8c537cca8b2f9c6e9176409d7da4dd3e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972127"
---
# <a name="single-sign-on-event-10522"></a><span data-ttu-id="28d50-102">單一登入： 事件 10522</span><span class="sxs-lookup"><span data-stu-id="28d50-102">Single Sign-On: Event 10522</span></span>
## <a name="details"></a><span data-ttu-id="28d50-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="28d50-103">Details</span></span>  

|                 |                                                                                               |
|-----------------|-----------------------------------------------------------------------------------------------|
|  <span data-ttu-id="28d50-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="28d50-104">Product Name</span></span>   |                                   <span data-ttu-id="28d50-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="28d50-105">Enterprise Single Sign-On</span></span>                                   |
| <span data-ttu-id="28d50-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="28d50-106">Product Version</span></span> |                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                   |
|    <span data-ttu-id="28d50-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="28d50-107">Event ID</span></span>     |                                             <span data-ttu-id="28d50-108">10522</span><span class="sxs-lookup"><span data-stu-id="28d50-108">10522</span></span>                                             |
|  <span data-ttu-id="28d50-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="28d50-109">Event Source</span></span>   |                                            <span data-ttu-id="28d50-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="28d50-110">ENTSSO</span></span>                                             |
|    <span data-ttu-id="28d50-111">元件</span><span class="sxs-lookup"><span data-stu-id="28d50-111">Component</span></span>    |                                              <span data-ttu-id="28d50-112">N\A</span><span class="sxs-lookup"><span data-stu-id="28d50-112">N\A</span></span>                                              |
|  <span data-ttu-id="28d50-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="28d50-113">Symbolic Name</span></span>  |                                      <span data-ttu-id="28d50-114">SSO_ERROR_REENCRYPT</span><span class="sxs-lookup"><span data-stu-id="28d50-114">SSO_ERROR_REENCRYPT</span></span>                                      |
|  <span data-ttu-id="28d50-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="28d50-115">Message Text</span></span>   | <span data-ttu-id="28d50-116">SSO 資料庫重新加密失敗。</span><span class="sxs-lookup"><span data-stu-id="28d50-116">SSO database re-encryption failed.</span></span> <span data-ttu-id="28d50-117">將再試一次在 %1 minutes.%r</span><span class="sxs-lookup"><span data-stu-id="28d50-117">Will try again in %1 minutes.%r</span></span><br /><br /> <span data-ttu-id="28d50-118">錯誤碼： %2</span><span class="sxs-lookup"><span data-stu-id="28d50-118">Error Code: %2</span></span> |

## <a name="explanation"></a><span data-ttu-id="28d50-119">說明</span><span class="sxs-lookup"><span data-stu-id="28d50-119">Explanation</span></span>  
 <span data-ttu-id="28d50-120">這個錯誤事件表示 SSO 資料庫重新加密失敗。</span><span class="sxs-lookup"><span data-stu-id="28d50-120">This Error event indicates that the SSO database re-encryption failed.</span></span> <span data-ttu-id="28d50-121">當主要密碼伺服器上，啟動 SSO 服務時，第一件事就是檢查是否有任何項目仍然使用先前的主要密碼加密的 SSO 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="28d50-121">When the SSO service starts on the master secret server, the first thing it does is to check if there is anything in the SSO database still encrypted with the previous master secret.</span></span> <span data-ttu-id="28d50-122">如果找到任何項目，它會解密該資訊 （使用先前的密碼），並重新使用目前的主要祕密加密。</span><span class="sxs-lookup"><span data-stu-id="28d50-122">If it finds anything, it decrypts that information (using the previous secret) and re-encrypts it using the current master secret.</span></span> <span data-ttu-id="28d50-123">如果因為任何原因此程序失敗，則會發出此事件訊息。</span><span class="sxs-lookup"><span data-stu-id="28d50-123">If for any reason this process fails, then this event message is issued.</span></span>  

## <a name="user-action"></a><span data-ttu-id="28d50-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="28d50-124">User Action</span></span>  
 <span data-ttu-id="28d50-125">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="28d50-125">To resolve this error, do the following:</span></span>  

- <span data-ttu-id="28d50-126">請檢查以判斷錯誤的根本原因可能是錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="28d50-126">Check the error code to determine what the underlying cause of the error might be.</span></span> <span data-ttu-id="28d50-127">這可能是資料庫或網路問題。</span><span class="sxs-lookup"><span data-stu-id="28d50-127">This could be a network or database issue.</span></span> <span data-ttu-id="28d50-128">如果它是有間歇性、 的則需要採取任何動作不，因為會在短暫延遲之後，再次嘗試重新加密。</span><span class="sxs-lookup"><span data-stu-id="28d50-128">If it is intermittent, then no action is required because re-encryption will be attempted again after a short delay.</span></span> <span data-ttu-id="28d50-129">如果此問題不是間歇性發生，請停止 SSO 服務，並嘗試解決此問題。</span><span class="sxs-lookup"><span data-stu-id="28d50-129">If the issue is not intermittent, stop the SSO service and attempt to resolve the issue.</span></span> <span data-ttu-id="28d50-130">一旦解決問題，然後重新啟動 SSO 服務重新啟動 SSO 服務將自動執行重新加密。</span><span class="sxs-lookup"><span data-stu-id="28d50-130">Once the issue is resolved then restart the SSO service, Restarting the SSO service will automatically perform the re-encryption.</span></span>  

  <span data-ttu-id="28d50-131">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="28d50-131">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="28d50-132">如何顯示 SSO 資料庫資訊</span><span class="sxs-lookup"><span data-stu-id="28d50-132">How to Display the SSO Database Information</span></span>](../core/how-to-display-the-sso-database-information.md)  

- [<span data-ttu-id="28d50-133">主要密碼伺服器</span><span class="sxs-lookup"><span data-stu-id="28d50-133">Master Secret Server</span></span>](../core/master-secret-server.md)
