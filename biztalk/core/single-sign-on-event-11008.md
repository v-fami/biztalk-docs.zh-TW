---
title: 單一登入： 事件 11008 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7e11dbc-7596-45fa-ae54-a6e79498e60e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f3a77dcfb89a3040cf6c1acb71a053d57393591
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983727"
---
# <a name="single-sign-on-event-11008"></a><span data-ttu-id="04be4-102">單一登入： 事件 11008</span><span class="sxs-lookup"><span data-stu-id="04be4-102">Single Sign-On: Event 11008</span></span>
## <a name="details"></a><span data-ttu-id="04be4-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="04be4-103">Details</span></span>  
  
|                 |                                                                                                                                                           |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="04be4-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="04be4-104">Product Name</span></span>   |                                                                 <span data-ttu-id="04be4-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="04be4-105">Enterprise Single Sign-On</span></span>                                                                 |
| <span data-ttu-id="04be4-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="04be4-106">Product Version</span></span> |                                                [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                 |
|    <span data-ttu-id="04be4-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="04be4-107">Event ID</span></span>     |                                                                           <span data-ttu-id="04be4-108">11008</span><span class="sxs-lookup"><span data-stu-id="04be4-108">11008</span></span>                                                                           |
|  <span data-ttu-id="04be4-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="04be4-109">Event Source</span></span>   |                                                                          <span data-ttu-id="04be4-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="04be4-110">ENTSSO</span></span>                                                                           |
|    <span data-ttu-id="04be4-111">元件</span><span class="sxs-lookup"><span data-stu-id="04be4-111">Component</span></span>    |                                                                            <span data-ttu-id="04be4-112">不適用</span><span class="sxs-lookup"><span data-stu-id="04be4-112">N/A</span></span>                                                                            |
|  <span data-ttu-id="04be4-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="04be4-113">Symbolic Name</span></span>  |                                                                   <span data-ttu-id="04be4-114">SSO_WARN_CHECK_GROUP</span><span class="sxs-lookup"><span data-stu-id="04be4-114">SSO_WARN_CHECK_GROUP</span></span>                                                                    |
|  <span data-ttu-id="04be4-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="04be4-115">Message Text</span></span>   | <span data-ttu-id="04be4-116">檢查群組成員資格 failed.%r</span><span class="sxs-lookup"><span data-stu-id="04be4-116">Check group membership failed.%r</span></span><br /><br /> <span data-ttu-id="04be4-117">群組名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="04be4-117">Group Name: %1%r</span></span><br /><br /> <span data-ttu-id="04be4-118">帳戶名稱: %2 %r</span><span class="sxs-lookup"><span data-stu-id="04be4-118">Account Name: %2%r</span></span><br /><br /> <span data-ttu-id="04be4-119">其他資料: %3 %r</span><span class="sxs-lookup"><span data-stu-id="04be4-119">Additional Data: %3%r</span></span><br /><br /> <span data-ttu-id="04be4-120">錯誤碼： %4</span><span class="sxs-lookup"><span data-stu-id="04be4-120">Error Code: %4</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="04be4-121">說明</span><span class="sxs-lookup"><span data-stu-id="04be4-121">Explanation</span></span>  
 <span data-ttu-id="04be4-122">這是最有可能因網路問題、 跨網域使用或的網域控制站混合層級 (例如，如果您的系統會使用兩個網域控制站時，才[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]和[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="04be4-122">This is most likely caused by network issues, cross-domain use, or a mixed level of domain controllers (for example, if your system uses domain controllers from both [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] and [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="04be4-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="04be4-123">User Action</span></span>  
 <span data-ttu-id="04be4-124">請檢查您的網路系統管理員，以查看是否有任何網路問題，或者您的系統有任何跨網域使用或的網域控制站混合層級。</span><span class="sxs-lookup"><span data-stu-id="04be4-124">Check with your network administrator to see if there are any network issues, or if your system has any cross-domain use or mixed level of domain controllers.</span></span>