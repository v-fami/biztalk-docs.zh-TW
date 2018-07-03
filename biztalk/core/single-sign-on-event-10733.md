---
title: 單一登入： 事件 10733 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01520ae4-f692-4697-82ce-53a8a63b5bd9
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd392f2a00d3010039501b99f731f1d9c350cdda
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023484"
---
# <a name="single-sign-on-event-10733"></a><span data-ttu-id="0acc3-102">單一登入： 事件 10733</span><span class="sxs-lookup"><span data-stu-id="0acc3-102">Single Sign-On: Event 10733</span></span>
## <a name="details"></a><span data-ttu-id="0acc3-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0acc3-103">Details</span></span>  

|                 |                                                                                                                                                             |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="0acc3-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0acc3-104">Product Name</span></span>   |                                                                  <span data-ttu-id="0acc3-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="0acc3-105">Enterprise Single Sign-On</span></span>                                                                  |
| <span data-ttu-id="0acc3-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="0acc3-106">Product Version</span></span> |                                                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                  |
|    <span data-ttu-id="0acc3-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0acc3-107">Event ID</span></span>     |                                                                            <span data-ttu-id="0acc3-108">10733</span><span class="sxs-lookup"><span data-stu-id="0acc3-108">10733</span></span>                                                                            |
|  <span data-ttu-id="0acc3-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="0acc3-109">Event Source</span></span>   |                                                                           <span data-ttu-id="0acc3-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="0acc3-110">ENTSSO</span></span>                                                                            |
|    <span data-ttu-id="0acc3-111">元件</span><span class="sxs-lookup"><span data-stu-id="0acc3-111">Component</span></span>    |                                                                             <span data-ttu-id="0acc3-112">N\A</span><span class="sxs-lookup"><span data-stu-id="0acc3-112">N\A</span></span>                                                                             |
|  <span data-ttu-id="0acc3-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0acc3-113">Symbolic Name</span></span>  |                                                              <span data-ttu-id="0acc3-114">SSO_WARN_PS_SET_WINDOWS_PASSWORD</span><span class="sxs-lookup"><span data-stu-id="0acc3-114">SSO_WARN_PS_SET_WINDOWS_PASSWORD</span></span>                                                               |
|  <span data-ttu-id="0acc3-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0acc3-115">Message Text</span></span>   | <span data-ttu-id="0acc3-116">無法更新 SSO 資料庫中的 Windows 密碼。%r</span><span class="sxs-lookup"><span data-stu-id="0acc3-116">Failed to update the Windows password in the SSO database.%r</span></span><br /><br /> <span data-ttu-id="0acc3-117">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="0acc3-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="0acc3-118">Windows 帳戶： %2\\%3 %r</span><span class="sxs-lookup"><span data-stu-id="0acc3-118">Windows Account: %2\\%3%r</span></span><br /><br /> <span data-ttu-id="0acc3-119">錯誤碼： %4</span><span class="sxs-lookup"><span data-stu-id="0acc3-119">Error Code: %4</span></span> |

## <a name="explanation"></a><span data-ttu-id="0acc3-120">說明</span><span class="sxs-lookup"><span data-stu-id="0acc3-120">Explanation</span></span>  
 <span data-ttu-id="0acc3-121">這個警告事件表示「密碼同步」無法更新 SSO 資料庫中指定的 Windows 帳戶密碼。</span><span class="sxs-lookup"><span data-stu-id="0acc3-121">This Warning event indicates that Password Sync failed to update the specified Windows account password in the SSO database.</span></span>  

## <a name="user-action"></a><span data-ttu-id="0acc3-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0acc3-122">User Action</span></span>  
 <span data-ttu-id="0acc3-123">若要解決這個警告，請執行下列一或多個動作：</span><span class="sxs-lookup"><span data-stu-id="0acc3-123">To resolve this warning, do one or more of the following:</span></span>  

- <span data-ttu-id="0acc3-124">請檢查系統和應用程式事件日誌中的相關錯誤。</span><span class="sxs-lookup"><span data-stu-id="0acc3-124">Check the system and application event logs for associated errors.</span></span>  

- <span data-ttu-id="0acc3-125">請確認指定帳戶的密碼是有效的 Windows 密碼。</span><span class="sxs-lookup"><span data-stu-id="0acc3-125">Verify the password for the specified account is a valid Windows password.</span></span>  

  <span data-ttu-id="0acc3-126">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="0acc3-126">For more information, see the following resources:</span></span>  

- [<span data-ttu-id="0acc3-127">密碼同步</span><span class="sxs-lookup"><span data-stu-id="0acc3-127">Password Synchronization</span></span>](../core/password-synchronization2.md)
