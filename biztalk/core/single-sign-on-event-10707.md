---
title: 單一登入： 事件 10707 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59629786-4f98-4861-aba3-153670bafc12
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81f4d484aa7a69f23cb66a921f1c630db9fcf790
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="single-sign-on-event-10707"></a><span data-ttu-id="8a4c2-102">單一登入： 事件 10707</span><span class="sxs-lookup"><span data-stu-id="8a4c2-102">Single Sign-On: Event 10707</span></span>
## <a name="details"></a><span data-ttu-id="8a4c2-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8a4c2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8a4c2-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="8a4c2-104">Product Name</span></span>|<span data-ttu-id="8a4c2-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="8a4c2-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="8a4c2-106">제품 버전</span><span class="sxs-lookup"><span data-stu-id="8a4c2-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="8a4c2-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8a4c2-107">Event ID</span></span>|<span data-ttu-id="8a4c2-108">10707</span><span class="sxs-lookup"><span data-stu-id="8a4c2-108">10707</span></span>|  
|<span data-ttu-id="8a4c2-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="8a4c2-109">Event Source</span></span>|<span data-ttu-id="8a4c2-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="8a4c2-110">ENTSSO</span></span>|  
|<span data-ttu-id="8a4c2-111">구성 요소</span><span class="sxs-lookup"><span data-stu-id="8a4c2-111">Component</span></span>|<span data-ttu-id="8a4c2-112">해당 없음</span><span class="sxs-lookup"><span data-stu-id="8a4c2-112">N\A</span></span>|  
|<span data-ttu-id="8a4c2-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8a4c2-113">Symbolic Name</span></span>|<span data-ttu-id="8a4c2-114">SSO_WARN_PS_NO_APP_SYNC</span><span class="sxs-lookup"><span data-stu-id="8a4c2-114">SSO_WARN_PS_NO_APP_SYNC</span></span>|  
|<span data-ttu-id="8a4c2-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8a4c2-115">Message Text</span></span>|<span data-ttu-id="8a4c2-116">密碼同步旗標，此配接器必須允許密碼同步處理，而且必須符合全域旗標。</span><span class="sxs-lookup"><span data-stu-id="8a4c2-116">Password sync flags for this adapter must allow password sync and must match the global flags.</span></span> <span data-ttu-id="8a4c2-117">請檢查配接器旗標和全域 flags.%r</span><span class="sxs-lookup"><span data-stu-id="8a4c2-117">Check the adapter flags and the global flags.%r</span></span><br /><br /> <span data-ttu-id="8a4c2-118">介面卡: %1</span><span class="sxs-lookup"><span data-stu-id="8a4c2-118">Adapter: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8a4c2-119">說明</span><span class="sxs-lookup"><span data-stu-id="8a4c2-119">Explanation</span></span>  
 <span data-ttu-id="8a4c2-120">此警告事件表示密碼同步旗標，此配接器必須允許密碼同步處理，必須符合全域旗標。</span><span class="sxs-lookup"><span data-stu-id="8a4c2-120">This Warning event indicates that password sync flags for this adapter must allow password sync and must match the global flags.</span></span>  
  
 <span data-ttu-id="8a4c2-121">一個密碼同步處理密碼同步配接器由兩個旗標來控制，可傳送到外部系統 (SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL) 的密碼，以及另一個可接收外部系統 (SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB) 的密碼。</span><span class="sxs-lookup"><span data-stu-id="8a4c2-121">Password sync for a password sync adapter is controlled by two flags, one allows sending of password to external systems (SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL) and another which allows receiving of passwords from external systems (SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB).</span></span> <span data-ttu-id="8a4c2-122">成功的密碼同步處理這些必須設定兩個 「 全域旗標 」 以及特定配接器旗標。</span><span class="sxs-lookup"><span data-stu-id="8a4c2-122">For successfull password sync these must be set for both the “global flags” and also for the specific adapter flags.</span></span> <span data-ttu-id="8a4c2-123">密碼同步處理要求的外部密碼同步配接器，但任一這些旗標設定為 「 全域旗標 」 和配接器旗標時，會發出這個警告事件。</span><span class="sxs-lookup"><span data-stu-id="8a4c2-123">This warning event is issued when password sync is requested by an external password sync adapter and neither of these flags is set for both the “global flags” and the adapter flags.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8a4c2-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8a4c2-124">User Action</span></span>  
 <span data-ttu-id="8a4c2-125">若要解決這個警告，請執行下列作業︰</span><span class="sxs-lookup"><span data-stu-id="8a4c2-125">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="8a4c2-126">使用 SSO 管理 MMC 嵌入式管理單元 (系統 & #124;屬性與 #124;選項） 或命令列工具  `ssomanage –enable winsync/extsync` 啟用全域旗標。</span><span class="sxs-lookup"><span data-stu-id="8a4c2-126">Use the SSO Admin MMC Snap-In (System &#124; Properties &#124; Options) or command line tool  `ssomanage –enable winsync/extsync` to enable the global flags.</span></span>  
  
## <a name="more-info"></a><span data-ttu-id="8a4c2-127">其他資訊</span><span class="sxs-lookup"><span data-stu-id="8a4c2-127">More info</span></span>
  
-   <span data-ttu-id="8a4c2-128">**企業單一登入旗標** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="8a4c2-128">**Enterprise Single Sign-On Flags** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>  
  
-   [<span data-ttu-id="8a4c2-129">如何管理密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="8a4c2-129">How to Administer Password Synchronization</span></span>](../core/how-to-administer-password-synchronization.md)