---
title: 單一登入： 事件 10850 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 04e2af52-d35b-491a-a983-d80442dd6aef
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94e9bef6d104b8da3c41d295005a7a274a1d2610
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278030"
---
# <a name="single-sign-on-event-10850"></a><span data-ttu-id="717eb-102">單一登入： 事件 10850</span><span class="sxs-lookup"><span data-stu-id="717eb-102">Single Sign-On: Event 10850</span></span>
## <a name="details"></a><span data-ttu-id="717eb-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="717eb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="717eb-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="717eb-104">Product Name</span></span>|<span data-ttu-id="717eb-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="717eb-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="717eb-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="717eb-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="717eb-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="717eb-107">Event ID</span></span>|<span data-ttu-id="717eb-108">10850</span><span class="sxs-lookup"><span data-stu-id="717eb-108">10850</span></span>|  
|<span data-ttu-id="717eb-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="717eb-109">Event Source</span></span>|<span data-ttu-id="717eb-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="717eb-110">ENTSSO</span></span>|  
|<span data-ttu-id="717eb-111">元件</span><span class="sxs-lookup"><span data-stu-id="717eb-111">Component</span></span>|<span data-ttu-id="717eb-112">不適用</span><span class="sxs-lookup"><span data-stu-id="717eb-112">N/A</span></span>|  
|<span data-ttu-id="717eb-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="717eb-113">Symbolic Name</span></span>|<span data-ttu-id="717eb-114">ENTSSO_E_ENABLED_NOT_ALLOWED_CREATE</span><span class="sxs-lookup"><span data-stu-id="717eb-114">ENTSSO_E_ENABLED_NOT_ALLOWED_CREATE</span></span>|  
|<span data-ttu-id="717eb-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="717eb-115">Message Text</span></span>|<span data-ttu-id="717eb-116">無法以指定的「啟用」旗標建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="717eb-116">An application cannot be created with the 'enabled' flag specified.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="717eb-117">說明</span><span class="sxs-lookup"><span data-stu-id="717eb-117">Explanation</span></span>  
 <span data-ttu-id="717eb-118">在啟用應用程式之前，必須建立應用程式並輸入其每個欄位的欄位資訊 (例如使用者識別碼和密碼)。</span><span class="sxs-lookup"><span data-stu-id="717eb-118">Before enabling an application, it is necessary to both create the application and enter the field information for each of its fields (i.e. UserID and Password).</span></span> <span data-ttu-id="717eb-119">無法建立已設定「已啟用」欄位的應用程式。</span><span class="sxs-lookup"><span data-stu-id="717eb-119">It is not possible to create an application with the “enabled” field already set.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="717eb-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="717eb-120">User Action</span></span>  
 <span data-ttu-id="717eb-121">再次建立應用程式 (使用「建立應用程式 API」或「建立新分支機構應用程式精靈」)。</span><span class="sxs-lookup"><span data-stu-id="717eb-121">Create the application again (using either the Create Application API or the Create New Affiliate Application Wizard).</span></span> <span data-ttu-id="717eb-122">當應用程式已完成且已填入欄位時，啟用應用程式。</span><span class="sxs-lookup"><span data-stu-id="717eb-122">When the application is complete and the fields populated, enable the application.</span></span>