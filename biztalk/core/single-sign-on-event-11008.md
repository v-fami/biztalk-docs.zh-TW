---
title: "單一登入： 事件 11008 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7e11dbc-7596-45fa-ae54-a6e79498e60e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88d2dfa2cfb71d66b43cfaa77b24b1dfce70fd7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11008"></a><span data-ttu-id="17396-102">單一登入： 事件 11008</span><span class="sxs-lookup"><span data-stu-id="17396-102">Single Sign-On: Event 11008</span></span>
## <a name="details"></a><span data-ttu-id="17396-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="17396-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="17396-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="17396-104">Product Name</span></span>|<span data-ttu-id="17396-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="17396-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="17396-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="17396-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="17396-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="17396-107">Event ID</span></span>|<span data-ttu-id="17396-108">11008</span><span class="sxs-lookup"><span data-stu-id="17396-108">11008</span></span>|  
|<span data-ttu-id="17396-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="17396-109">Event Source</span></span>|<span data-ttu-id="17396-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="17396-110">ENTSSO</span></span>|  
|<span data-ttu-id="17396-111">元件</span><span class="sxs-lookup"><span data-stu-id="17396-111">Component</span></span>|<span data-ttu-id="17396-112">不適用</span><span class="sxs-lookup"><span data-stu-id="17396-112">N/A</span></span>|  
|<span data-ttu-id="17396-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="17396-113">Symbolic Name</span></span>|<span data-ttu-id="17396-114">SSO_WARN_CHECK_GROUP</span><span class="sxs-lookup"><span data-stu-id="17396-114">SSO_WARN_CHECK_GROUP</span></span>|  
|<span data-ttu-id="17396-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="17396-115">Message Text</span></span>|<span data-ttu-id="17396-116">檢查群組成員資格 failed.%r</span><span class="sxs-lookup"><span data-stu-id="17396-116">Check group membership failed.%r</span></span><br /><br /> <span data-ttu-id="17396-117">群組名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="17396-117">Group Name: %1%r</span></span><br /><br /> <span data-ttu-id="17396-118">帳戶名稱: %2 %r</span><span class="sxs-lookup"><span data-stu-id="17396-118">Account Name: %2%r</span></span><br /><br /> <span data-ttu-id="17396-119">其他資料: %3 %r</span><span class="sxs-lookup"><span data-stu-id="17396-119">Additional Data: %3%r</span></span><br /><br /> <span data-ttu-id="17396-120">錯誤碼： %4</span><span class="sxs-lookup"><span data-stu-id="17396-120">Error Code: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="17396-121">說明</span><span class="sxs-lookup"><span data-stu-id="17396-121">Explanation</span></span>  
 <span data-ttu-id="17396-122">這可能是因為網路問題、 跨網域使用或混合層級的網域控制站 (例如，如果您的系統使用的網域控制站，同時從[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]和[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="17396-122">This is most likely caused by network issues, cross-domain use, or a mixed level of domain controllers (for example, if your system uses domain controllers from both [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] and [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="17396-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="17396-123">User Action</span></span>  
 <span data-ttu-id="17396-124">請洽詢您的網路系統管理員，以查看是否有任何網路問題，或如果您的系統具有任何跨網域使用或的網域控制站的混合層級。</span><span class="sxs-lookup"><span data-stu-id="17396-124">Check with your network administrator to see if there are any network issues, or if your system has any cross-domain use or mixed level of domain controllers.</span></span>