---
title: 找不到的應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c37680b2-b38a-40f3-bb27-7b7281299ec3
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 98499420c773328d647a9c7fa1c80e3ab09ba1b1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003455"
---
# <a name="application-not-found"></a><span data-ttu-id="ba5f2-102">找不到的應用程式</span><span class="sxs-lookup"><span data-stu-id="ba5f2-102">Application not found</span></span>
## <a name="details"></a><span data-ttu-id="ba5f2-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ba5f2-103">Details</span></span>  

|                 |                                                                                                         |
|-----------------|---------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="ba5f2-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ba5f2-104">Product Name</span></span>   |           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]            |
| <span data-ttu-id="ba5f2-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="ba5f2-105">Product Version</span></span> |                       [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                        |
|    <span data-ttu-id="ba5f2-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ba5f2-106">Event ID</span></span>     |                                                    <span data-ttu-id="ba5f2-107">0</span><span class="sxs-lookup"><span data-stu-id="ba5f2-107">0</span></span>                                                    |
|  <span data-ttu-id="ba5f2-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="ba5f2-108">Event Source</span></span>   |                                                    <span data-ttu-id="ba5f2-109">0</span><span class="sxs-lookup"><span data-stu-id="ba5f2-109">0</span></span>                                                    |
|    <span data-ttu-id="ba5f2-110">元件</span><span class="sxs-lookup"><span data-stu-id="ba5f2-110">Component</span></span>    |                                                    <span data-ttu-id="ba5f2-111">0</span><span class="sxs-lookup"><span data-stu-id="ba5f2-111">0</span></span>                                                    |
|  <span data-ttu-id="ba5f2-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ba5f2-112">Symbolic Name</span></span>  |                                                    <span data-ttu-id="ba5f2-113">0</span><span class="sxs-lookup"><span data-stu-id="ba5f2-113">0</span></span>                                                    |
|  <span data-ttu-id="ba5f2-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ba5f2-114">Message Text</span></span>   | <span data-ttu-id="ba5f2-115">應用程式 「{0}「 找不到。請確認應用程式存在於預設 BizTalk 組態資料庫</span><span class="sxs-lookup"><span data-stu-id="ba5f2-115">Application "{0}" not found.Verify the application exists in the default BizTalk configuration database</span></span> |

## <a name="explanation"></a><span data-ttu-id="ba5f2-116">說明</span><span class="sxs-lookup"><span data-stu-id="ba5f2-116">Explanation</span></span>  
 <span data-ttu-id="ba5f2-117">此錯誤表示 BizTalk 會使用不存在於 BizTalk 資料庫的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ba5f2-117">This error indicates BizTalk is using an application that does not exist in the BizTalk databases.</span></span>  

## <a name="user-action"></a><span data-ttu-id="ba5f2-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ba5f2-118">User Action</span></span>  
 <span data-ttu-id="ba5f2-119">您可以使用下列程序來設定有效的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ba5f2-119">Use the following procedure to configure a valid application.</span></span>  

#### <a name="to-configure-a-valid-application"></a><span data-ttu-id="ba5f2-120">若要設定有效的應用程式</span><span class="sxs-lookup"><span data-stu-id="ba5f2-120">To configure a valid application</span></span>  

1. <span data-ttu-id="ba5f2-121">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。</span><span class="sxs-lookup"><span data-stu-id="ba5f2-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  

2. <span data-ttu-id="ba5f2-122">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="ba5f2-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand **Applications**.</span></span>  

3. <span data-ttu-id="ba5f2-123">請確定應用程式那里存在。</span><span class="sxs-lookup"><span data-stu-id="ba5f2-123">Ensure that the application exists there.</span></span> <span data-ttu-id="ba5f2-124">否則，請選取不同的有效應用程式。</span><span class="sxs-lookup"><span data-stu-id="ba5f2-124">If not, select a different valid application.</span></span>
