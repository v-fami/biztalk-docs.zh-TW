---
title: 單一登入： 事件 10715 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f63c98d2-988e-466f-be40-171b13a34732
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9bc461aa812c2c61844c11d54743335ac89321a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994855"
---
# <a name="single-sign-on-event-10715"></a><span data-ttu-id="19f4c-102">單一登入： 事件 10715</span><span class="sxs-lookup"><span data-stu-id="19f4c-102">Single Sign-On: Event 10715</span></span>
## <a name="details"></a><span data-ttu-id="19f4c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="19f4c-103">Details</span></span>  

|                 |                                                                                                                                                                                                                  |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="19f4c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="19f4c-104">Product Name</span></span>   |                                                                                            <span data-ttu-id="19f4c-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="19f4c-105">Enterprise Single Sign-On</span></span>                                                                                             |
| <span data-ttu-id="19f4c-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="19f4c-106">Product Version</span></span> |                                                                            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                            |
|    <span data-ttu-id="19f4c-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="19f4c-107">Event ID</span></span>     |                                                                                                      <span data-ttu-id="19f4c-108">10715</span><span class="sxs-lookup"><span data-stu-id="19f4c-108">10715</span></span>                                                                                                       |
|  <span data-ttu-id="19f4c-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="19f4c-109">Event Source</span></span>   |                                                                                                      <span data-ttu-id="19f4c-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="19f4c-110">ENTSSO</span></span>                                                                                                      |
|    <span data-ttu-id="19f4c-111">元件</span><span class="sxs-lookup"><span data-stu-id="19f4c-111">Component</span></span>    |                                                                                                       <span data-ttu-id="19f4c-112">N\A</span><span class="sxs-lookup"><span data-stu-id="19f4c-112">N\A</span></span>                                                                                                        |
|  <span data-ttu-id="19f4c-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="19f4c-113">Symbolic Name</span></span>  |                                                                                            <span data-ttu-id="19f4c-114">SSO_WARN_NO_CREATE_ADAPTER</span><span class="sxs-lookup"><span data-stu-id="19f4c-114">SSO_WARN_NO_CREATE_ADAPTER</span></span>                                                                                            |
|  <span data-ttu-id="19f4c-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="19f4c-115">Message Text</span></span>   | <span data-ttu-id="19f4c-116">用戶端使用者必須是 SSO 系統管理員帳戶的成員，才能建立配接器。%r</span><span class="sxs-lookup"><span data-stu-id="19f4c-116">The client user must be a member of the SSO Administrators account to create adapters.%r</span></span><br /><br /> <span data-ttu-id="19f4c-117">用戶端使用者: %1 %r</span><span class="sxs-lookup"><span data-stu-id="19f4c-117">Client User: %1%r</span></span><br /><br /> <span data-ttu-id="19f4c-118">SSO 系統管理員: %2 %r</span><span class="sxs-lookup"><span data-stu-id="19f4c-118">SSO Administrators: %2%r</span></span><br /><br /> <span data-ttu-id="19f4c-119">配接器: %3 %r</span><span class="sxs-lookup"><span data-stu-id="19f4c-119">Adapter: %3%r</span></span><br /><br /> <span data-ttu-id="19f4c-120">錯誤碼： %4</span><span class="sxs-lookup"><span data-stu-id="19f4c-120">Error Code: %4</span></span> |

## <a name="explanation"></a><span data-ttu-id="19f4c-121">說明</span><span class="sxs-lookup"><span data-stu-id="19f4c-121">Explanation</span></span>  
 <span data-ttu-id="19f4c-122">這個警告事件表示用戶端使用者必須是 SSO 系統管理員帳戶的成員，才能建立配接器。</span><span class="sxs-lookup"><span data-stu-id="19f4c-122">This Warning event indicates that the client user must be a member of the SSO Administrators account to create adapters.</span></span>  

## <a name="user-action"></a><span data-ttu-id="19f4c-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="19f4c-123">User Action</span></span>  
 <span data-ttu-id="19f4c-124">若要解決這個警告，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="19f4c-124">To resolve this warning, do the following:</span></span>  

- <span data-ttu-id="19f4c-125">使用屬於 SSO 系統管理員群組的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="19f4c-125">Logon with an account that belongs to the SSO Administrators group.</span></span>  

  <span data-ttu-id="19f4c-126">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="19f4c-126">For more information, see the following resources:</span></span>  

- [<span data-ttu-id="19f4c-127">SSO 使用者群組</span><span class="sxs-lookup"><span data-stu-id="19f4c-127">SSO User Groups</span></span>](../core/sso-user-groups.md)
