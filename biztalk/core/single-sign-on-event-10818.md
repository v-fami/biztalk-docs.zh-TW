---
title: 單一登入： 事件 10818 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6ad54646-4285-42e5-a270-d56935742a95
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be2c40fa5da46f5045b55c815be9f6f8048cda67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277366"
---
# <a name="single-sign-on-event-10818"></a><span data-ttu-id="e21ad-102">單一登入： 事件 10818</span><span class="sxs-lookup"><span data-stu-id="e21ad-102">Single Sign-On: Event 10818</span></span>
## <a name="details"></a><span data-ttu-id="e21ad-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e21ad-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e21ad-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e21ad-104">Product Name</span></span>|<span data-ttu-id="e21ad-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="e21ad-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="e21ad-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="e21ad-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="e21ad-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e21ad-107">Event ID</span></span>|<span data-ttu-id="e21ad-108">10818</span><span class="sxs-lookup"><span data-stu-id="e21ad-108">10818</span></span>|  
|<span data-ttu-id="e21ad-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="e21ad-109">Event Source</span></span>|<span data-ttu-id="e21ad-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="e21ad-110">ENTSSO</span></span>|  
|<span data-ttu-id="e21ad-111">元件</span><span class="sxs-lookup"><span data-stu-id="e21ad-111">Component</span></span>|<span data-ttu-id="e21ad-112">不適用</span><span class="sxs-lookup"><span data-stu-id="e21ad-112">N/A</span></span>|  
|<span data-ttu-id="e21ad-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e21ad-113">Symbolic Name</span></span>|<span data-ttu-id="e21ad-114">ENTSSO_E_AMBIGUOUS_SYNC_FIELDS</span><span class="sxs-lookup"><span data-stu-id="e21ad-114">ENTSSO_E_AMBIGUOUS_SYNC_FIELDS</span></span>|  
|<span data-ttu-id="e21ad-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e21ad-115">Message Text</span></span>|<span data-ttu-id="e21ad-116">應用程式必須具有兩個欄位，或只有一個欄位必須標示為同步。</span><span class="sxs-lookup"><span data-stu-id="e21ad-116">The application must have two fields or only one field must be marked for sync.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e21ad-117">說明</span><span class="sxs-lookup"><span data-stu-id="e21ad-117">Explanation</span></span>  
 <span data-ttu-id="e21ad-118">如果有兩個以上的欄位，則只有唯一一個必須標示為密碼同步。</span><span class="sxs-lookup"><span data-stu-id="e21ad-118">If there are more than two fields, then one and only one must be marked for password sync.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e21ad-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e21ad-119">User Action</span></span>  
 <span data-ttu-id="e21ad-120">若要修正這種情況，您必須刪除應用程式然後重新建立，讓應用程式遵循這些準則。</span><span class="sxs-lookup"><span data-stu-id="e21ad-120">To remedy this situation, you must delete the application and recreate it so that it follows these guidelines.</span></span>