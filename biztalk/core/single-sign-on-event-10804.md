---
title: 單一登入： 事件 10804 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4d98bef-fdc3-4627-bb5b-663fa502b965
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b65c59ce736804215cd7c70428905d776d8e0e4b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276646"
---
# <a name="single-sign-on-event-10804"></a><span data-ttu-id="f486a-102">單一登入： 事件 10804</span><span class="sxs-lookup"><span data-stu-id="f486a-102">Single Sign-On: Event 10804</span></span>
## <a name="details"></a><span data-ttu-id="f486a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f486a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f486a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f486a-104">Product Name</span></span>|<span data-ttu-id="f486a-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="f486a-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="f486a-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="f486a-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="f486a-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f486a-107">Event ID</span></span>|<span data-ttu-id="f486a-108">10804</span><span class="sxs-lookup"><span data-stu-id="f486a-108">10804</span></span>|  
|<span data-ttu-id="f486a-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="f486a-109">Event Source</span></span>|<span data-ttu-id="f486a-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="f486a-110">ENTSSO</span></span>|  
|<span data-ttu-id="f486a-111">元件</span><span class="sxs-lookup"><span data-stu-id="f486a-111">Component</span></span>|<span data-ttu-id="f486a-112">不適用</span><span class="sxs-lookup"><span data-stu-id="f486a-112">N/A</span></span>|  
|<span data-ttu-id="f486a-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f486a-113">Symbolic Name</span></span>|<span data-ttu-id="f486a-114">ENTSSO_E_INCORRECT_COMPUTER</span><span class="sxs-lookup"><span data-stu-id="f486a-114">ENTSSO_E_INCORRECT_COMPUTER</span></span>|  
|<span data-ttu-id="f486a-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f486a-115">Message Text</span></span>|<span data-ttu-id="f486a-116">此配接器不是針對此電腦設定。</span><span class="sxs-lookup"><span data-stu-id="f486a-116">This adapter is not configured for this computer.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f486a-117">說明</span><span class="sxs-lookup"><span data-stu-id="f486a-117">Explanation</span></span>  
 <span data-ttu-id="f486a-118">每個配接器都設定為在特定電腦上執行，以其完整名稱識別。</span><span class="sxs-lookup"><span data-stu-id="f486a-118">Each adapter is configured to run on a specific computer, which is identified by its long name.</span></span> <span data-ttu-id="f486a-119">名稱不正確，或您嘗試在不同電腦上執行配接器。</span><span class="sxs-lookup"><span data-stu-id="f486a-119">Either the name is incorrect, or you are trying to run the adapter on a different computer.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f486a-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f486a-120">User Action</span></span>  
 <span data-ttu-id="f486a-121">請參閱此配接器的組態來判斷適當電腦的適當名稱。</span><span class="sxs-lookup"><span data-stu-id="f486a-121">See the configuration for this adapter to determine the proper name of the appropriate computer.</span></span>