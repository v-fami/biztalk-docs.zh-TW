---
title: 單一登入： 事件 10739 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1039c832-80ff-4cc2-97b4-2671672b6b12
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a08c0b5194b3c6cb2a75966a33d7215fd0b7b499
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969447"
---
# <a name="single-sign-on-event-10739"></a><span data-ttu-id="76a15-102">單一登入： 事件 10739</span><span class="sxs-lookup"><span data-stu-id="76a15-102">Single Sign-On: Event 10739</span></span>
## <a name="details"></a><span data-ttu-id="76a15-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="76a15-103">Details</span></span>  

|                 |                                                                                                                                                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="76a15-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="76a15-104">Product Name</span></span>   |                                                                               <span data-ttu-id="76a15-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="76a15-105">Enterprise Single Sign-On</span></span>                                                                               |
| <span data-ttu-id="76a15-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="76a15-106">Product Version</span></span> |                                                              [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                               |
|    <span data-ttu-id="76a15-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="76a15-107">Event ID</span></span>     |                                                                                         <span data-ttu-id="76a15-108">10739</span><span class="sxs-lookup"><span data-stu-id="76a15-108">10739</span></span>                                                                                         |
|  <span data-ttu-id="76a15-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="76a15-109">Event Source</span></span>   |                                                                                        <span data-ttu-id="76a15-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="76a15-110">ENTSSO</span></span>                                                                                         |
|    <span data-ttu-id="76a15-111">元件</span><span class="sxs-lookup"><span data-stu-id="76a15-111">Component</span></span>    |                                                                                          <span data-ttu-id="76a15-112">N\A</span><span class="sxs-lookup"><span data-stu-id="76a15-112">N\A</span></span>                                                                                          |
|  <span data-ttu-id="76a15-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="76a15-113">Symbolic Name</span></span>  |                                                                       <span data-ttu-id="76a15-114">SSO_WARN_PS_SET_WINDOWS_PASSWORD_ADAPTER</span><span class="sxs-lookup"><span data-stu-id="76a15-114">SSO_WARN_PS_SET_WINDOWS_PASSWORD_ADAPTER</span></span>                                                                        |
|  <span data-ttu-id="76a15-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="76a15-115">Message Text</span></span>   | <span data-ttu-id="76a15-116">無法更新 SSO 資料庫中的 Windows 密碼。%r</span><span class="sxs-lookup"><span data-stu-id="76a15-116">Failed to update the Windows password in the SSO database.%r</span></span><br /><br /> <span data-ttu-id="76a15-117">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="76a15-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="76a15-118">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="76a15-118">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="76a15-119">Windows 帳戶： %3\\%4 %r</span><span class="sxs-lookup"><span data-stu-id="76a15-119">Windows Account: %3\\%4%r</span></span><br /><br /> <span data-ttu-id="76a15-120">錯誤碼： %5</span><span class="sxs-lookup"><span data-stu-id="76a15-120">Error Code: %5</span></span> |

## <a name="explanation"></a><span data-ttu-id="76a15-121">說明</span><span class="sxs-lookup"><span data-stu-id="76a15-121">Explanation</span></span>  
 <span data-ttu-id="76a15-122">這個警告事件表示 SSO 失敗，更新 SSO 資料庫中的 Windows 密碼。</span><span class="sxs-lookup"><span data-stu-id="76a15-122">This Warning event indicates that SSO failed to update the Windows password in the SSO database.</span></span> <span data-ttu-id="76a15-123">有各種可能的原因的警告訊息中指出的失敗在某些情況下，這個警告可能表示設定有問題，或對應可能已刪除，處理密碼變更時。</span><span class="sxs-lookup"><span data-stu-id="76a15-123">There are various possible causes of failure indicated in the warning message; in some cases, this warning might indicate a configuration problem, or the mapping may have been deleted while the password change was in process.</span></span>  

## <a name="user-action"></a><span data-ttu-id="76a15-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="76a15-124">User Action</span></span>  
 <span data-ttu-id="76a15-125">若要解決這個警告，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="76a15-125">To resolve this warning, do the following:</span></span>  

- <span data-ttu-id="76a15-126">重試一次變更密碼。</span><span class="sxs-lookup"><span data-stu-id="76a15-126">Retry the password change.</span></span>  

- <span data-ttu-id="76a15-127">如果其他嘗試繼續失敗，變更的密碼使用 UI 或命令列工具，以手動方式。</span><span class="sxs-lookup"><span data-stu-id="76a15-127">If additional attempts continue to fail, change the password manually using the UI or command line tools.</span></span>  

  <span data-ttu-id="76a15-128">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="76a15-128">For more information, see the following resources:</span></span>  

- [<span data-ttu-id="76a15-129">密碼同步</span><span class="sxs-lookup"><span data-stu-id="76a15-129">Password Synchronization</span></span>](../core/password-synchronization2.md)
