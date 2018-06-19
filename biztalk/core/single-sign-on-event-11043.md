---
title: 單一登入： 事件 11043 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 128d68fb-1905-49b3-9b67-30a9442569cc
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc211e4726c68a16f860dd0431a234765e80b76a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276454"
---
# <a name="single-sign-on-event-11043"></a><span data-ttu-id="fd3ad-102">單一登入： 事件 11043</span><span class="sxs-lookup"><span data-stu-id="fd3ad-102">Single Sign-On: Event 11043</span></span>
## <a name="details"></a><span data-ttu-id="fd3ad-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fd3ad-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fd3ad-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="fd3ad-104">Product Name</span></span>|<span data-ttu-id="fd3ad-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="fd3ad-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="fd3ad-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="fd3ad-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="fd3ad-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="fd3ad-107">Event ID</span></span>|<span data-ttu-id="fd3ad-108">11043</span><span class="sxs-lookup"><span data-stu-id="fd3ad-108">11043</span></span>|  
|<span data-ttu-id="fd3ad-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="fd3ad-109">Event Source</span></span>|<span data-ttu-id="fd3ad-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="fd3ad-110">ENTSSO</span></span>|  
|<span data-ttu-id="fd3ad-111">元件</span><span class="sxs-lookup"><span data-stu-id="fd3ad-111">Component</span></span>|<span data-ttu-id="fd3ad-112">不適用</span><span class="sxs-lookup"><span data-stu-id="fd3ad-112">N/A</span></span>|  
|<span data-ttu-id="fd3ad-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="fd3ad-113">Symbolic Name</span></span>|<span data-ttu-id="fd3ad-114">SSO_WARN_PS_ADAPTER_REPORTED_FAILURE</span><span class="sxs-lookup"><span data-stu-id="fd3ad-114">SSO_WARN_PS_ADAPTER_REPORTED_FAILURE</span></span>|  
|<span data-ttu-id="fd3ad-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="fd3ad-115">Message Text</span></span>|<span data-ttu-id="fd3ad-116">密碼同步配接器報告在嘗試變更外部密碼時失敗。</span><span class="sxs-lookup"><span data-stu-id="fd3ad-116">The password sync adapter reported a failure while attempting to change the external password.</span></span> <span data-ttu-id="fd3ad-117">在 SSO 資料庫中未更新外部密碼。%r</span><span class="sxs-lookup"><span data-stu-id="fd3ad-117">The external password was not updated in the SSO database.%r</span></span><br /><br /> <span data-ttu-id="fd3ad-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="fd3ad-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="fd3ad-119">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="fd3ad-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="fd3ad-120">外部帳戶: %3 %r</span><span class="sxs-lookup"><span data-stu-id="fd3ad-120">External Account: %3%r</span></span><br /><br /> <span data-ttu-id="fd3ad-121">錯誤訊息: %4 %r</span><span class="sxs-lookup"><span data-stu-id="fd3ad-121">Error Message: %4%r</span></span><br /><br /> <span data-ttu-id="fd3ad-122">錯誤碼： %5</span><span class="sxs-lookup"><span data-stu-id="fd3ad-122">Error Code: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fd3ad-123">說明</span><span class="sxs-lookup"><span data-stu-id="fd3ad-123">Explanation</span></span>  
 <span data-ttu-id="fd3ad-124">當 ENTSSO 密碼同步配接器來傳送密碼變更時，外部密碼必須先成功變更 ENTSSO 使其成為 SSO 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="fd3ad-124">When ENTSSO sends a password change to a password sync adapter, the external password must be successfully changed before ENTSSO makes it in the SSO database.</span></span> <span data-ttu-id="fd3ad-125">在此情況下，並未發生。</span><span class="sxs-lookup"><span data-stu-id="fd3ad-125">In this case, that did not occur.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fd3ad-126">使用者動作</span><span class="sxs-lookup"><span data-stu-id="fd3ad-126">User Action</span></span>  
 <span data-ttu-id="fd3ad-127">請注意警告訊息中的資訊，請連絡系統管理員。</span><span class="sxs-lookup"><span data-stu-id="fd3ad-127">Note the information in the warning message and consult your system administrator.</span></span>