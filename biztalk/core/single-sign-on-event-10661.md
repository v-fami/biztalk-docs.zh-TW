---
title: "單一登入： 事件 10661 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3418f37-770d-4021-9341-5dbe99689da6
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6fdc655a87975a89387d84e2aefdd07a603c0ed3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10661"></a><span data-ttu-id="62055-102">單一登入： 事件 10661</span><span class="sxs-lookup"><span data-stu-id="62055-102">Single Sign-On: Event 10661</span></span>
## <a name="details"></a><span data-ttu-id="62055-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="62055-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="62055-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="62055-104">Product Name</span></span>|<span data-ttu-id="62055-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="62055-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="62055-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="62055-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="62055-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="62055-107">Event ID</span></span>|<span data-ttu-id="62055-108">10661</span><span class="sxs-lookup"><span data-stu-id="62055-108">10661</span></span>|  
|<span data-ttu-id="62055-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="62055-109">Event Source</span></span>|<span data-ttu-id="62055-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="62055-110">ENTSSO</span></span>|  
|<span data-ttu-id="62055-111">元件</span><span class="sxs-lookup"><span data-stu-id="62055-111">Component</span></span>|<span data-ttu-id="62055-112">N\A</span><span class="sxs-lookup"><span data-stu-id="62055-112">N\A</span></span>|  
|<span data-ttu-id="62055-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="62055-113">Symbolic Name</span></span>|<span data-ttu-id="62055-114">SSO_ERROR_PASSWORD_SYNC_WINDOWS_START_FAILED</span><span class="sxs-lookup"><span data-stu-id="62055-114">SSO_ERROR_PASSWORD_SYNC_WINDOWS_START_FAILED</span></span>|  
|<span data-ttu-id="62055-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="62055-115">Message Text</span></span>|<span data-ttu-id="62055-116">Windows （來自 PCNS) 的密碼同步無法 start.%r</span><span class="sxs-lookup"><span data-stu-id="62055-116">Password sync for Windows (from PCNS) failed to start.%r</span></span><br /><br /> <span data-ttu-id="62055-117">錯誤碼： %1</span><span class="sxs-lookup"><span data-stu-id="62055-117">Error Code: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="62055-118">說明</span><span class="sxs-lookup"><span data-stu-id="62055-118">Explanation</span></span>  
 <span data-ttu-id="62055-119">這個錯誤事件表示 Windows 的密碼同步無法啟動。</span><span class="sxs-lookup"><span data-stu-id="62055-119">This Error event indicates that password sync for Windows failed to start.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="62055-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="62055-120">User Action</span></span>  
 <span data-ttu-id="62055-121">若要解決這個錯誤，請執行下列一個或多個動作：</span><span class="sxs-lookup"><span data-stu-id="62055-121">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="62055-122">檢查應用程式與系統事件記錄檔相關聯的事件。</span><span class="sxs-lookup"><span data-stu-id="62055-122">Check the application and system event logs for associated events.</span></span>  
  
-   <span data-ttu-id="62055-123">請確認配接器組態屬性。</span><span class="sxs-lookup"><span data-stu-id="62055-123">Verify adapter configuration properties.</span></span>  
  
## <a name="more-info"></a><span data-ttu-id="62055-124">其他資訊</span><span class="sxs-lookup"><span data-stu-id="62055-124">More info</span></span>
  
-   [<span data-ttu-id="62055-125">如何管理密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="62055-125">How to Administer Password Synchronization</span></span>](../core/how-to-administer-password-synchronization.md)  
  
-   <span data-ttu-id="62055-126">**企業單一登入 UI 說明**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="62055-126">**Enterprise Single Sign-On UI Help** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>