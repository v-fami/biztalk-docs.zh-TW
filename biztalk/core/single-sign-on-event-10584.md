---
title: 單一登入： 事件 10584 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8af9377d-b4fd-48a6-961a-3629b3db644a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d08be0100d53f081eb7d8f4faa27d1e7f46f6f46
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270366"
---
# <a name="single-sign-on-event-10584"></a><span data-ttu-id="bea1f-102">單一登入： 事件 10584</span><span class="sxs-lookup"><span data-stu-id="bea1f-102">Single Sign-On: Event 10584</span></span>
## <a name="details"></a><span data-ttu-id="bea1f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bea1f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bea1f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="bea1f-104">Product Name</span></span>|<span data-ttu-id="bea1f-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="bea1f-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="bea1f-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="bea1f-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="bea1f-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="bea1f-107">Event ID</span></span>|<span data-ttu-id="bea1f-108">10584</span><span class="sxs-lookup"><span data-stu-id="bea1f-108">10584</span></span>|  
|<span data-ttu-id="bea1f-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="bea1f-109">Event Source</span></span>|<span data-ttu-id="bea1f-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="bea1f-110">ENTSSO</span></span>|  
|<span data-ttu-id="bea1f-111">元件</span><span class="sxs-lookup"><span data-stu-id="bea1f-111">Component</span></span>|<span data-ttu-id="bea1f-112">不適用</span><span class="sxs-lookup"><span data-stu-id="bea1f-112">N/A</span></span>|  
|<span data-ttu-id="bea1f-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="bea1f-113">Symbolic Name</span></span>|<span data-ttu-id="bea1f-114">SSO_WARN_NO_IMPERSONATION</span><span class="sxs-lookup"><span data-stu-id="bea1f-114">SSO_WARN_NO_IMPERSONATION</span></span>|  
|<span data-ttu-id="bea1f-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="bea1f-115">Message Text</span></span>|<span data-ttu-id="bea1f-116">無法模擬用戶端。%r</span><span class="sxs-lookup"><span data-stu-id="bea1f-116">Could not impersonate the client.%r</span></span><br /><br /> <span data-ttu-id="bea1f-117">錯誤碼： %1</span><span class="sxs-lookup"><span data-stu-id="bea1f-117">Error Code: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bea1f-118">說明</span><span class="sxs-lookup"><span data-stu-id="bea1f-118">Explanation</span></span>  
 <span data-ttu-id="bea1f-119">模擬用戶端是 ENTSSO 系統會驗證用戶端的身分識別的項目。</span><span class="sxs-lookup"><span data-stu-id="bea1f-119">Impersonating the client is something the ENTSSO System does to verify the client’s identity.</span></span> <span data-ttu-id="bea1f-120">當系統無法模擬用戶端，其中三種情況可能會發生。</span><span class="sxs-lookup"><span data-stu-id="bea1f-120">When the system is unable to impersonate a client, one of three things may have occurred.</span></span> <span data-ttu-id="bea1f-121">用戶端可能會嘗試執行的一般活動、 用戶端可能嘗試滲透系統安全性，或用戶端應用程式可能已設計可封鎖模擬。</span><span class="sxs-lookup"><span data-stu-id="bea1f-121">The client may be attempting to perform an usual activity, the client may be attempting to infiltrate system security, or the client application may have been designed to block impersonation.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bea1f-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="bea1f-122">User Action</span></span>  
 <span data-ttu-id="bea1f-123">找出用戶端應用程式並判斷它正嘗試執行作業，以及它封鎖模擬。</span><span class="sxs-lookup"><span data-stu-id="bea1f-123">Locate the client application and determine what it is attempting to do, and whether or not it is blocking impersonation.</span></span>