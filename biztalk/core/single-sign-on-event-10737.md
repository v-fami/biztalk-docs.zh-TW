---
title: 單一登入： 事件 10737 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2102930b-8b1f-4d48-a14d-e8884dc7f9aa
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd21b244e86c14aaf0f3af7418f1ca2ed8fbf067
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987679"
---
# <a name="single-sign-on-event-10737"></a><span data-ttu-id="d10d1-102">單一登入： 事件 10737</span><span class="sxs-lookup"><span data-stu-id="d10d1-102">Single Sign-On: Event 10737</span></span>
## <a name="details"></a><span data-ttu-id="d10d1-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d10d1-103">Details</span></span>  

|                 |                                                                                                                                                                                                                        |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="d10d1-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d10d1-104">Product Name</span></span>   |                                                                                               <span data-ttu-id="d10d1-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="d10d1-105">Enterprise Single Sign-On</span></span>                                                                                                |
| <span data-ttu-id="d10d1-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="d10d1-106">Product Version</span></span> |                                                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                               |
|    <span data-ttu-id="d10d1-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d10d1-107">Event ID</span></span>     |                                                                                                         <span data-ttu-id="d10d1-108">10737</span><span class="sxs-lookup"><span data-stu-id="d10d1-108">10737</span></span>                                                                                                          |
|  <span data-ttu-id="d10d1-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="d10d1-109">Event Source</span></span>   |                                                                                                         <span data-ttu-id="d10d1-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="d10d1-110">ENTSSO</span></span>                                                                                                         |
|    <span data-ttu-id="d10d1-111">元件</span><span class="sxs-lookup"><span data-stu-id="d10d1-111">Component</span></span>    |                                                                                                          <span data-ttu-id="d10d1-112">N\A</span><span class="sxs-lookup"><span data-stu-id="d10d1-112">N\A</span></span>                                                                                                           |
|  <span data-ttu-id="d10d1-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d10d1-113">Symbolic Name</span></span>  |                                                                                           <span data-ttu-id="d10d1-114">SSO_WARN_PS_SET_EXTERNAL_PASSWORD</span><span class="sxs-lookup"><span data-stu-id="d10d1-114">SSO_WARN_PS_SET_EXTERNAL_PASSWORD</span></span>                                                                                            |
|  <span data-ttu-id="d10d1-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d10d1-115">Message Text</span></span>   | <span data-ttu-id="d10d1-116">無法更新 SSO database.%r 中的外部密碼</span><span class="sxs-lookup"><span data-stu-id="d10d1-116">Failed to update the external password in the SSO database.%r</span></span><br /><br /> <span data-ttu-id="d10d1-117">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="d10d1-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="d10d1-118">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="d10d1-118">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="d10d1-119">應用程式名稱: %3 %r</span><span class="sxs-lookup"><span data-stu-id="d10d1-119">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="d10d1-120">外部帳戶: %4 %r</span><span class="sxs-lookup"><span data-stu-id="d10d1-120">External Account: %4%r</span></span><br /><br /> <span data-ttu-id="d10d1-121">錯誤碼： %5</span><span class="sxs-lookup"><span data-stu-id="d10d1-121">Error Code: %5</span></span> |

## <a name="explanation"></a><span data-ttu-id="d10d1-122">說明</span><span class="sxs-lookup"><span data-stu-id="d10d1-122">Explanation</span></span>  
 <span data-ttu-id="d10d1-123">這個警告事件表示 SSO 無法更新 SSO 資料庫中的外部密碼。</span><span class="sxs-lookup"><span data-stu-id="d10d1-123">This Warning event indicates that SSO failed to update the external password in the SSO database.</span></span> <span data-ttu-id="d10d1-124">有各種可能的原因的警告訊息中指出的失敗在某些情況下，這個警告可能表示設定有問題，或對應可能已刪除，處理密碼變更時。</span><span class="sxs-lookup"><span data-stu-id="d10d1-124">There are various possible causes of failure indicated in the warning message; in some cases, this warning might indicate a configuration problem, or the mapping may have been deleted while the password change was in process.</span></span>  

## <a name="user-action"></a><span data-ttu-id="d10d1-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d10d1-125">User Action</span></span>  
 <span data-ttu-id="d10d1-126">若要解決這個警告，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="d10d1-126">To resolve this warning, do the following:</span></span>  

- <span data-ttu-id="d10d1-127">重試一次變更密碼。</span><span class="sxs-lookup"><span data-stu-id="d10d1-127">Retry the password change.</span></span>  

- <span data-ttu-id="d10d1-128">如果其他嘗試繼續失敗，變更的密碼使用 UI 或命令列工具，以手動方式。</span><span class="sxs-lookup"><span data-stu-id="d10d1-128">If additional attempts continue to fail, change the password manually using the UI or command line tools.</span></span>  

  <span data-ttu-id="d10d1-129">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="d10d1-129">For more information, see the following resources:</span></span>  

- [<span data-ttu-id="d10d1-130">密碼同步</span><span class="sxs-lookup"><span data-stu-id="d10d1-130">Password Synchronization</span></span>](../core/password-synchronization2.md)
