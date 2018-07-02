---
title: 單一登入： 事件 10750 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a0fdaf2-d429-40b9-adc3-eb134687fb1a
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 28526c6695cbf8f9c29e99621d6cb2f852fa7021
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984367"
---
# <a name="single-sign-on-event-10750"></a><span data-ttu-id="ab820-102">單一登入： 事件 10750</span><span class="sxs-lookup"><span data-stu-id="ab820-102">Single Sign-On: Event 10750</span></span>
## <a name="details"></a><span data-ttu-id="ab820-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ab820-103">Details</span></span>  

|                 |                                                                                                                                                                                                                                                                  |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="ab820-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ab820-104">Product Name</span></span>   |                                                                                                                    <span data-ttu-id="ab820-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="ab820-105">Enterprise Single Sign-On</span></span>                                                                                                                     |
| <span data-ttu-id="ab820-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="ab820-106">Product Version</span></span> |                                                                                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                    |
|    <span data-ttu-id="ab820-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ab820-107">Event ID</span></span>     |                                                                                                                              <span data-ttu-id="ab820-108">10750</span><span class="sxs-lookup"><span data-stu-id="ab820-108">10750</span></span>                                                                                                                               |
|  <span data-ttu-id="ab820-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="ab820-109">Event Source</span></span>   |                                                                                                                              <span data-ttu-id="ab820-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="ab820-110">ENTSSO</span></span>                                                                                                                              |
|    <span data-ttu-id="ab820-111">元件</span><span class="sxs-lookup"><span data-stu-id="ab820-111">Component</span></span>    |                                                                                                                               <span data-ttu-id="ab820-112">N\A</span><span class="sxs-lookup"><span data-stu-id="ab820-112">N\A</span></span>                                                                                                                                |
|  <span data-ttu-id="ab820-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ab820-113">Symbolic Name</span></span>  |                                                                                                                <span data-ttu-id="ab820-114">SSO_ERROR_PS_WRONG_USER_NAME_TYPE</span><span class="sxs-lookup"><span data-stu-id="ab820-114">SSO_ERROR_PS_WRONG_USER_NAME_TYPE</span></span>                                                                                                                 |
|  <span data-ttu-id="ab820-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ab820-115">Message Text</span></span>   | <span data-ttu-id="ab820-116">PasswordChangeNotify： 不正確的使用者名稱類型。</span><span class="sxs-lookup"><span data-stu-id="ab820-116">PasswordChangeNotify: Incorrect User Name Type.</span></span> <span data-ttu-id="ab820-117">接受的值只有 USER_NAME_TYPE_NT4。</span><span class="sxs-lookup"><span data-stu-id="ab820-117">The only accepted value is USER_NAME_TYPE_NT4.</span></span><br /><br /> <span data-ttu-id="ab820-118">設定目標 Active Directory.%r 中，不正確</span><span class="sxs-lookup"><span data-stu-id="ab820-118">The target is incorrectly configured in Active Directory.%r</span></span><br /><br /> <span data-ttu-id="ab820-119">使用者名稱類型: %1 %r</span><span class="sxs-lookup"><span data-stu-id="ab820-119">User Name Type: %1%r</span></span><br /><br /> <span data-ttu-id="ab820-120">用戶端使用者: %2 %r</span><span class="sxs-lookup"><span data-stu-id="ab820-120">Client User: %2%r</span></span><br /><br /> <span data-ttu-id="ab820-121">錯誤碼： %3</span><span class="sxs-lookup"><span data-stu-id="ab820-121">Error Code: %3</span></span> |

## <a name="explanation"></a><span data-ttu-id="ab820-122">說明</span><span class="sxs-lookup"><span data-stu-id="ab820-122">Explanation</span></span>  
 <span data-ttu-id="ab820-123">這個錯誤事件表示密碼同步處理收到的密碼變更的密碼變更通知服務 (PCNS)，但密碼變更是格式錯誤。</span><span class="sxs-lookup"><span data-stu-id="ab820-123">This Error event indicates that Password Sync received a password change from the Password Change Notification Service (PCNS), but the password change was in the wrong format.</span></span>  

## <a name="user-action"></a><span data-ttu-id="ab820-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ab820-124">User Action</span></span>  
 <span data-ttu-id="ab820-125">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="ab820-125">To resolve this error, do the following:</span></span>  

- <span data-ttu-id="ab820-126">檢查 PCNS 設定。</span><span class="sxs-lookup"><span data-stu-id="ab820-126">Check the PCNS configuration.</span></span> <span data-ttu-id="ab820-127">PCNS 可以只在網域控制站上執行。</span><span class="sxs-lookup"><span data-stu-id="ab820-127">PCNS can run only on a domain controller.</span></span>  

- <span data-ttu-id="ab820-128">Active Directory 中設定使用者名稱類型 USER_NAME_TYPE_NT4。</span><span class="sxs-lookup"><span data-stu-id="ab820-128">Configure User Name Type to USER_NAME_TYPE_NT4 in Active Directory.</span></span>  

  <span data-ttu-id="ab820-129">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="ab820-129">For more information, see the following resources:</span></span>  

- <span data-ttu-id="ab820-130">請參閱 Active Directory 文件，如需有關如何指定使用者名稱類型資訊。</span><span class="sxs-lookup"><span data-stu-id="ab820-130">Refer to Active Directory documentation for information on how to specify User Name Type.</span></span>  

- [<span data-ttu-id="ab820-131">密碼同步</span><span class="sxs-lookup"><span data-stu-id="ab820-131">Password Synchronization</span></span>](../core/password-synchronization2.md)
