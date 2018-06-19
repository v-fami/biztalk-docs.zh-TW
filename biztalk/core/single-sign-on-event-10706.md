---
title: 單一登入： 事件 10706 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d73db77e-5bb6-431c-a8ca-5682d7ab3d6a
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5703c81d87376349561f644da558b8594cd51b79
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
ms.locfileid: "22271558"
---
# <a name="single-sign-on-event-10706"></a><span data-ttu-id="88f86-102">單一登入： 事件 10706</span><span class="sxs-lookup"><span data-stu-id="88f86-102">Single Sign-On: Event 10706</span></span>
## <a name="details"></a><span data-ttu-id="88f86-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="88f86-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="88f86-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="88f86-104">Product Name</span></span>|<span data-ttu-id="88f86-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="88f86-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="88f86-106">제품 버전</span><span class="sxs-lookup"><span data-stu-id="88f86-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="88f86-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="88f86-107">Event ID</span></span>|<span data-ttu-id="88f86-108">10706</span><span class="sxs-lookup"><span data-stu-id="88f86-108">10706</span></span>|  
|<span data-ttu-id="88f86-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="88f86-109">Event Source</span></span>|<span data-ttu-id="88f86-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="88f86-110">ENTSSO</span></span>|  
|<span data-ttu-id="88f86-111">구성 요소</span><span class="sxs-lookup"><span data-stu-id="88f86-111">Component</span></span>|<span data-ttu-id="88f86-112">해당 없음</span><span class="sxs-lookup"><span data-stu-id="88f86-112">N\A</span></span>|  
|<span data-ttu-id="88f86-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="88f86-113">Symbolic Name</span></span>|<span data-ttu-id="88f86-114">SSO_WARN_PS_NO_GLOBAL_SYNC</span><span class="sxs-lookup"><span data-stu-id="88f86-114">SSO_WARN_PS_NO_GLOBAL_SYNC</span></span>|  
|<span data-ttu-id="88f86-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="88f86-115">Message Text</span></span>|<span data-ttu-id="88f86-116">群組配接器需要全域旗標所允許的密碼同步處理。</span><span class="sxs-lookup"><span data-stu-id="88f86-116">Group adapters require password sync to be allowed by the global flags.</span></span> <span data-ttu-id="88f86-117">檢查全域旗標。%r</span><span class="sxs-lookup"><span data-stu-id="88f86-117">Check the global flags.%r</span></span><br /><br /> <span data-ttu-id="88f86-118">介面卡: %1</span><span class="sxs-lookup"><span data-stu-id="88f86-118">Adapter: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="88f86-119">說明</span><span class="sxs-lookup"><span data-stu-id="88f86-119">Explanation</span></span>  
 <span data-ttu-id="88f86-120">此警告事件表示外部密碼同步配接器已要求密碼同步，且兩者全域旗標設定。</span><span class="sxs-lookup"><span data-stu-id="88f86-120">This Warning event indicates that password sync is requested by an external password sync adapter and neither of the global flags is set.</span></span> <span data-ttu-id="88f86-121">有兩個旗標，一個允許傳送到外部系統的密碼︰ SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL，另一個可接收外部系統 SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB 的密碼。</span><span class="sxs-lookup"><span data-stu-id="88f86-121">There are two flags, one that allows sending of password to external system: SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL and another that allows receiving of passwords from external systems SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="88f86-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="88f86-122">User Action</span></span>  
 <span data-ttu-id="88f86-123">若要解決這個警告，請執行下列作業︰</span><span class="sxs-lookup"><span data-stu-id="88f86-123">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="88f86-124">使用 SSO 管理 MMC 嵌入式管理單元、 (系統 & #124;屬性與 #124。選項） 或命令列工具  `ssomanage –enable winsync/extsync` 啟用全域旗標。</span><span class="sxs-lookup"><span data-stu-id="88f86-124">Use the SSO Admin MMC Snap-In, (System &#124; Properties &#124; Options) or command line tool  `ssomanage –enable winsync/extsync` to enable the global flags.</span></span>  
  
## <a name="more-info"></a><span data-ttu-id="88f86-125">其他資訊</span><span class="sxs-lookup"><span data-stu-id="88f86-125">More info</span></span>
  
-   <span data-ttu-id="88f86-126">**企業單一登入旗標** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="88f86-126">**Enterprise Single Sign-On Flags** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
  
-   [<span data-ttu-id="88f86-127">如何管理密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="88f86-127">How to Administer Password Synchronization</span></span>](../core/how-to-administer-password-synchronization.md)