---
title: 單一登入： 事件 10613 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7a87ca19-24a0-4cf8-984f-2f70d7b5018c
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf7230a0d6400a7265ef9f3cedb6bb47cc23aade
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271222"
---
# <a name="single-sign-on-event-10613"></a><span data-ttu-id="89d19-102">單一登入： 事件 10613</span><span class="sxs-lookup"><span data-stu-id="89d19-102">Single Sign-On: Event 10613</span></span>
## <a name="details"></a><span data-ttu-id="89d19-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="89d19-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="89d19-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="89d19-104">Product Name</span></span>|<span data-ttu-id="89d19-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="89d19-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="89d19-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="89d19-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="89d19-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="89d19-107">Event ID</span></span>|<span data-ttu-id="89d19-108">10613</span><span class="sxs-lookup"><span data-stu-id="89d19-108">10613</span></span>|  
|<span data-ttu-id="89d19-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="89d19-109">Event Source</span></span>|<span data-ttu-id="89d19-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="89d19-110">ENTSSO</span></span>|  
|<span data-ttu-id="89d19-111">元件</span><span class="sxs-lookup"><span data-stu-id="89d19-111">Component</span></span>|<span data-ttu-id="89d19-112">不適用</span><span class="sxs-lookup"><span data-stu-id="89d19-112">N/A</span></span>|  
|<span data-ttu-id="89d19-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="89d19-113">Symbolic Name</span></span>|<span data-ttu-id="89d19-114">SSO_ERROR_RPC_CALLBACK</span><span class="sxs-lookup"><span data-stu-id="89d19-114">SSO_ERROR_RPC_CALLBACK</span></span>|  
|<span data-ttu-id="89d19-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="89d19-115">Message Text</span></span>|<span data-ttu-id="89d19-116">SSO 伺服器存取遭拒。%r</span><span class="sxs-lookup"><span data-stu-id="89d19-116">SSO server access denied.%r</span></span><br /><br /> <span data-ttu-id="89d19-117">用戶端使用者: %1 %r</span><span class="sxs-lookup"><span data-stu-id="89d19-117">Client User: %1%r</span></span><br /><br /> <span data-ttu-id="89d19-118">RPC 呼叫資訊: %2: %3 %r</span><span class="sxs-lookup"><span data-stu-id="89d19-118">RPC call information: %2:%3%r</span></span><br /><br /> <span data-ttu-id="89d19-119">錯誤碼： %4</span><span class="sxs-lookup"><span data-stu-id="89d19-119">Error Code: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="89d19-120">說明</span><span class="sxs-lookup"><span data-stu-id="89d19-120">Explanation</span></span>  
 <span data-ttu-id="89d19-121">呼叫已從用戶端對 SSO 伺服器，但不是被接受。</span><span class="sxs-lookup"><span data-stu-id="89d19-121">A call was made from a client to the SSO Server but was not accepted.</span></span> <span data-ttu-id="89d19-122">原因可能是由數種不同原因，例如不正確的通訊協定或用戶端上沒有足夠的安全性權限。</span><span class="sxs-lookup"><span data-stu-id="89d19-122">This can be caused by a number of different reasons, such as incorrect protocol or insufficient security permissions on the client.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="89d19-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="89d19-123">User Action</span></span>  
 <span data-ttu-id="89d19-124">請注意，此訊息中的資訊和事件記錄檔中的任何相關資訊，請連絡 Microsoft 產品支援服務。</span><span class="sxs-lookup"><span data-stu-id="89d19-124">Note the information in this message, and any relevant information in the event log, and contact Microsoft Product Support Services.</span></span>