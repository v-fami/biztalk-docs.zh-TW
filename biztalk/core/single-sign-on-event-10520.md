---
title: 單一登入： 事件 10520 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 91662072-d87c-4290-8afb-2143143ee858
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0721ae4d89ee05792f2189a0d6a6b2c5e4efdddb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011383"
---
# <a name="single-sign-on-event-10520"></a><span data-ttu-id="900f8-102">單一登入： 事件 10520</span><span class="sxs-lookup"><span data-stu-id="900f8-102">Single Sign-On: Event 10520</span></span>
## <a name="details"></a><span data-ttu-id="900f8-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="900f8-103">Details</span></span>  

|                 |                                                                                                                                        |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="900f8-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="900f8-104">Product Name</span></span>   |                                                       <span data-ttu-id="900f8-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="900f8-105">Enterprise Single Sign-On</span></span>                                                        |
| <span data-ttu-id="900f8-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="900f8-106">Product Version</span></span> |                                       [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                       |
|    <span data-ttu-id="900f8-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="900f8-107">Event ID</span></span>     |                                                                 <span data-ttu-id="900f8-108">10520</span><span class="sxs-lookup"><span data-stu-id="900f8-108">10520</span></span>                                                                  |
|  <span data-ttu-id="900f8-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="900f8-109">Event Source</span></span>   |                                                                 <span data-ttu-id="900f8-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="900f8-110">ENTSSO</span></span>                                                                 |
|    <span data-ttu-id="900f8-111">元件</span><span class="sxs-lookup"><span data-stu-id="900f8-111">Component</span></span>    |                                                                  <span data-ttu-id="900f8-112">N\A</span><span class="sxs-lookup"><span data-stu-id="900f8-112">N\A</span></span>                                                                   |
|  <span data-ttu-id="900f8-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="900f8-113">Symbolic Name</span></span>  |                                                          <span data-ttu-id="900f8-114">SSO_WARN_NO_SECRETS</span><span class="sxs-lookup"><span data-stu-id="900f8-114">SSO_WARN_NO_SECRETS</span></span>                                                           |
|  <span data-ttu-id="900f8-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="900f8-115">Message Text</span></span>   | <span data-ttu-id="900f8-116">主要密碼伺服器的登錄中找不到任何祕密。</span><span class="sxs-lookup"><span data-stu-id="900f8-116">No secrets were found in the registry of the master secret server.</span></span> <span data-ttu-id="900f8-117">您可以使用 組態工具來產生或還原主要祕密。</span><span class="sxs-lookup"><span data-stu-id="900f8-117">Use the configuration tools to generate or restore a master secret.</span></span> |

## <a name="explanation"></a><span data-ttu-id="900f8-118">說明</span><span class="sxs-lookup"><span data-stu-id="900f8-118">Explanation</span></span>  
 <span data-ttu-id="900f8-119">這個警告事件表示，任何祕密找不到主要密碼伺服器的登錄中。</span><span class="sxs-lookup"><span data-stu-id="900f8-119">This Warning event indicates that no secrets were found in the registry of the master secret server.</span></span> <span data-ttu-id="900f8-120">SSO 主要祕密儲存在 SSO 主要祕密伺服器的登錄中加密。</span><span class="sxs-lookup"><span data-stu-id="900f8-120">The SSO master secrets are stored encrypted in the registry of the SSO master secret server.</span></span> <span data-ttu-id="900f8-121">兩個密碼通常都會保存在登錄中： 目前的主要祕密和先前的主要密碼。</span><span class="sxs-lookup"><span data-stu-id="900f8-121">Two secrets are typically kept in the registry: the current master secret, and the previous master secret.</span></span> <span data-ttu-id="900f8-122">密碼會識別使用 GUID （主要祕密識別碼）。</span><span class="sxs-lookup"><span data-stu-id="900f8-122">Secrets are identified using a GUID (the master secret id).</span></span> <span data-ttu-id="900f8-123">如果要求時的登錄中找不到指定的主要祕密，就會傳回此錯誤的程式碼。</span><span class="sxs-lookup"><span data-stu-id="900f8-123">If the specified master secret cannot be found in the registry when requested, this error code will be returned.</span></span>  

## <a name="user-action"></a><span data-ttu-id="900f8-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="900f8-124">User Action</span></span>  
 <span data-ttu-id="900f8-125">若要解決此 warnming，執行一或多個項目：</span><span class="sxs-lookup"><span data-stu-id="900f8-125">To resolve this warnming, do one or more of the following:</span></span>  

- <span data-ttu-id="900f8-126">確認主要密碼伺服器名稱正確且預期。</span><span class="sxs-lookup"><span data-stu-id="900f8-126">Check that the master secret server name is correct and as expected.</span></span>  

- <span data-ttu-id="900f8-127">如果正確，請檢查該主要密碼伺服器的登錄中的主要祕密。</span><span class="sxs-lookup"><span data-stu-id="900f8-127">If it is correct, check that the master secret is present in the registry of that master secret server.</span></span> <span data-ttu-id="900f8-128">主要祕密位於的 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ENTSSO\SSOSS （此金鑰是只能在 SSO 主要祕密伺服器上存在）。</span><span class="sxs-lookup"><span data-stu-id="900f8-128">The master secret is located under HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ENTSSO\SSOSS (this key is present only on the SSO master secret server).</span></span>  

- <span data-ttu-id="900f8-129">如果該索引鍵遺漏，則主要祕密不存在。</span><span class="sxs-lookup"><span data-stu-id="900f8-129">If that key is missing then the master secret is not present.</span></span> <span data-ttu-id="900f8-130">應該要有一或多個索引鍵下 SSOSS 命名為包含加密的金鑰的 Guid。</span><span class="sxs-lookup"><span data-stu-id="900f8-130">There should be one or more keys under SSOSS named as GUIDs which contain the encrypted keys.</span></span> <span data-ttu-id="900f8-131">如果沒有這些然後主要祕密不存在。</span><span class="sxs-lookup"><span data-stu-id="900f8-131">If these are not present then the master secret is not present.</span></span> <span data-ttu-id="900f8-132">主要祕密均具有 Guid （主要祕密識別碼） 讓這些 Guid （如果有的話） 應該符合所要求的祕密的主要祕密識別碼。</span><span class="sxs-lookup"><span data-stu-id="900f8-132">Master secrets are identified with GUIDs (the master secret id) so these GUIDs (if present) should match the master secret id of the secret that was requested.</span></span> <span data-ttu-id="900f8-133">如果名為 Guid 的索引鍵，但它們不符合要求的主要祕密識別碼，則沒有 mixup 之間在登錄中的主要密碼和密碼是用來加密 SSO 資料庫 (SSODB) 中的資料。</span><span class="sxs-lookup"><span data-stu-id="900f8-133">If there are keys named as GUIDs but they don’t match the requested master secret id, then there is a mixup between the master secret in the registry and the secret that was used to encrypt the data in the SSO database (SSODB).</span></span> <span data-ttu-id="900f8-134">可能需要在此情況下，還原不同的主要祕密或 SSODB 可能已從舊版的備份還原。</span><span class="sxs-lookup"><span data-stu-id="900f8-134">It may be necessary to restore a different master secret in this case, or maybe the SSODB has been restored from a downlevel backup.</span></span> <span data-ttu-id="900f8-135">如果主要祕密根本不存在，然後可以使用 SSO 組態工具 （命令列或 MMC） 的表單已還原的備份，或可以產生新的祕密。</span><span class="sxs-lookup"><span data-stu-id="900f8-135">If the master secret is not present at all, then it can be restored form backup using the SSO configuration tools (command line or MMC) or a new secret can be generated.</span></span> <span data-ttu-id="900f8-136">請注意，您通常只想来產生新的主要祕密，如果這是新的安裝，而且沒有任何現有的加密 SSO 資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="900f8-136">Note that you would normally only want to generate a new master secret if this is a new installation and there is no existing encrypted data in the SSO database.</span></span> <span data-ttu-id="900f8-137">第一次在初始設定期間通常會產生主要祕密。</span><span class="sxs-lookup"><span data-stu-id="900f8-137">The master secret is normally generated for the first time during initial configuration.</span></span>  

  <span data-ttu-id="900f8-138">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="900f8-138">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="900f8-139">主要密碼伺服器</span><span class="sxs-lookup"><span data-stu-id="900f8-139">Master Secret Server</span></span>](../core/master-secret-server.md)  

- [<span data-ttu-id="900f8-140">管理主要密碼</span><span class="sxs-lookup"><span data-stu-id="900f8-140">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)  

- [<span data-ttu-id="900f8-141">設定 SSO</span><span class="sxs-lookup"><span data-stu-id="900f8-141">Configuring SSO</span></span>](../core/configuring-sso.md)
