---
title: 單一登入： 事件 10521 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00d427ff-74d0-45f5-bb55-ab12b564d767
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8af1b2ac8d2ac3645db6a6a80146832378aececf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008567"
---
# <a name="single-sign-on-event-10521"></a><span data-ttu-id="5edcd-102">單一登入： 事件 10521</span><span class="sxs-lookup"><span data-stu-id="5edcd-102">Single Sign-On: Event 10521</span></span>
## <a name="details"></a><span data-ttu-id="5edcd-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5edcd-103">Details</span></span>  

|                 |                                                                       |
|-----------------|-----------------------------------------------------------------------|
|  <span data-ttu-id="5edcd-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="5edcd-104">Product Name</span></span>   |                       <span data-ttu-id="5edcd-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="5edcd-105">Enterprise Single Sign-On</span></span>                       |
| <span data-ttu-id="5edcd-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="5edcd-106">Product Version</span></span> |      [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]       |
|    <span data-ttu-id="5edcd-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="5edcd-107">Event ID</span></span>     |                                 <span data-ttu-id="5edcd-108">10521</span><span class="sxs-lookup"><span data-stu-id="5edcd-108">10521</span></span>                                 |
|  <span data-ttu-id="5edcd-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="5edcd-109">Event Source</span></span>   |                                <span data-ttu-id="5edcd-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="5edcd-110">ENTSSO</span></span>                                 |
|    <span data-ttu-id="5edcd-111">元件</span><span class="sxs-lookup"><span data-stu-id="5edcd-111">Component</span></span>    |                                  <span data-ttu-id="5edcd-112">N\A</span><span class="sxs-lookup"><span data-stu-id="5edcd-112">N\A</span></span>                                  |
|  <span data-ttu-id="5edcd-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="5edcd-113">Symbolic Name</span></span>  |                     <span data-ttu-id="5edcd-114">SSO_ERROR_SECRETS_NOT_LOADED</span><span class="sxs-lookup"><span data-stu-id="5edcd-114">SSO_ERROR_SECRETS_NOT_LOADED</span></span>                      |
|  <span data-ttu-id="5edcd-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="5edcd-115">Message Text</span></span>   | <span data-ttu-id="5edcd-116">無法從主要密碼伺服器的登錄載入祕密。</span><span class="sxs-lookup"><span data-stu-id="5edcd-116">Could not load secrets from the registry of the master secret server.</span></span> |

## <a name="explanation"></a><span data-ttu-id="5edcd-117">說明</span><span class="sxs-lookup"><span data-stu-id="5edcd-117">Explanation</span></span>  
 <span data-ttu-id="5edcd-118">當無法從登錄取得主要祕密，這個錯誤事件發生於主要密碼伺服器上。</span><span class="sxs-lookup"><span data-stu-id="5edcd-118">This Error event occurs on the master secret server when the master secrets cannot be obtained from the registry.</span></span> <span data-ttu-id="5edcd-119">在進一步的資訊在事件記錄檔中，可能會有相關的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="5edcd-119">There may be related errors messages in the event log with further information.</span></span> <span data-ttu-id="5edcd-120">這最可能的原因是已權限錯誤或加密錯誤時，SSO 服務帳戶嘗試存取登錄。</span><span class="sxs-lookup"><span data-stu-id="5edcd-120">The most likely cause of this is that there has been a permissions error or an encryption error when the SSO service account attempted to access the registry.</span></span> <span data-ttu-id="5edcd-121">SSO 服務帳戶已變更時，可能發生這項目。</span><span class="sxs-lookup"><span data-stu-id="5edcd-121">This can occur when the SSO service account has been changed.</span></span> <span data-ttu-id="5edcd-122">主要祕密已加密的 SSO 服務帳戶識別為基礎的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="5edcd-122">The master secret is encrypted with a key that is based on the identity of the SSO service account.</span></span> <span data-ttu-id="5edcd-123">如果該帳戶已變更，在登錄中現有的主要密碼都無法再解密。</span><span class="sxs-lookup"><span data-stu-id="5edcd-123">If that account is changed, then the existing master secret in the registry can no longer be decrypted.</span></span>  

## <a name="user-action"></a><span data-ttu-id="5edcd-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="5edcd-124">User Action</span></span>  
 <span data-ttu-id="5edcd-125">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="5edcd-125">To resolve this error, do the following:</span></span>  

- <span data-ttu-id="5edcd-126">備份主要祕密，變更 SSO 服務帳戶，然後再還原主要祕密，以變更 SSO 服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="5edcd-126">Change the SSO service account by backing-up the master secret, then changing the SSO service account, and then restoring the master secret.</span></span> <span data-ttu-id="5edcd-127">這可以還原主要祕密，並應可修正此錯誤。</span><span class="sxs-lookup"><span data-stu-id="5edcd-127">This can restore the master secret and should fix this error.</span></span>  

  <span data-ttu-id="5edcd-128">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="5edcd-128">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="5edcd-129">主要密碼伺服器</span><span class="sxs-lookup"><span data-stu-id="5edcd-129">Master Secret Server</span></span>](../core/master-secret-server.md)  

- [<span data-ttu-id="5edcd-130">管理主要密碼</span><span class="sxs-lookup"><span data-stu-id="5edcd-130">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)  

- [<span data-ttu-id="5edcd-131">設定 SSO</span><span class="sxs-lookup"><span data-stu-id="5edcd-131">Configuring SSO</span></span>](../core/configuring-sso.md)  

- [<span data-ttu-id="5edcd-132">SSO 安全性建議</span><span class="sxs-lookup"><span data-stu-id="5edcd-132">SSO Security Recommendations</span></span>](../core/sso-security-recommendations.md)
