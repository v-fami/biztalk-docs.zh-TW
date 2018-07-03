---
title: 單一登入： 事件 10613 |Microsoft Docs
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
ms.openlocfilehash: 250f113e0cd60b417cee29d32f8e61fbf38632dc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023804"
---
# <a name="single-sign-on-event-10613"></a><span data-ttu-id="54309-102">單一登入： 事件 10613</span><span class="sxs-lookup"><span data-stu-id="54309-102">Single Sign-On: Event 10613</span></span>
## <a name="details"></a><span data-ttu-id="54309-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="54309-103">Details</span></span>  
  
|                 |                                                                                                                                |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="54309-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="54309-104">Product Name</span></span>   |                                                   <span data-ttu-id="54309-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="54309-105">Enterprise Single Sign-On</span></span>                                                    |
| <span data-ttu-id="54309-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="54309-106">Product Version</span></span> |                                   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                   |
|    <span data-ttu-id="54309-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="54309-107">Event ID</span></span>     |                                                             <span data-ttu-id="54309-108">10613</span><span class="sxs-lookup"><span data-stu-id="54309-108">10613</span></span>                                                              |
|  <span data-ttu-id="54309-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="54309-109">Event Source</span></span>   |                                                             <span data-ttu-id="54309-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="54309-110">ENTSSO</span></span>                                                             |
|    <span data-ttu-id="54309-111">元件</span><span class="sxs-lookup"><span data-stu-id="54309-111">Component</span></span>    |                                                              <span data-ttu-id="54309-112">不適用</span><span class="sxs-lookup"><span data-stu-id="54309-112">N/A</span></span>                                                               |
|  <span data-ttu-id="54309-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="54309-113">Symbolic Name</span></span>  |                                                     <span data-ttu-id="54309-114">SSO_ERROR_RPC_CALLBACK</span><span class="sxs-lookup"><span data-stu-id="54309-114">SSO_ERROR_RPC_CALLBACK</span></span>                                                     |
|  <span data-ttu-id="54309-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="54309-115">Message Text</span></span>   | <span data-ttu-id="54309-116">SSO 伺服器存取遭拒。%r</span><span class="sxs-lookup"><span data-stu-id="54309-116">SSO server access denied.%r</span></span><br /><br /> <span data-ttu-id="54309-117">用戶端使用者: %1 %r</span><span class="sxs-lookup"><span data-stu-id="54309-117">Client User: %1%r</span></span><br /><br /> <span data-ttu-id="54309-118">RPC 呼叫資訊: %2: %3 %r</span><span class="sxs-lookup"><span data-stu-id="54309-118">RPC call information: %2:%3%r</span></span><br /><br /> <span data-ttu-id="54309-119">錯誤碼： %4</span><span class="sxs-lookup"><span data-stu-id="54309-119">Error Code: %4</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="54309-120">說明</span><span class="sxs-lookup"><span data-stu-id="54309-120">Explanation</span></span>  
 <span data-ttu-id="54309-121">呼叫已從用戶端對 SSO 伺服器，但不是被接受。</span><span class="sxs-lookup"><span data-stu-id="54309-121">A call was made from a client to the SSO Server but was not accepted.</span></span> <span data-ttu-id="54309-122">原因可能是由數項不同的原因，例如不正確的通訊協定或用戶端上沒有足夠的安全性權限。</span><span class="sxs-lookup"><span data-stu-id="54309-122">This can be caused by a number of different reasons, such as incorrect protocol or insufficient security permissions on the client.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="54309-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="54309-123">User Action</span></span>  
 <span data-ttu-id="54309-124">請注意，此訊息中的資訊和事件記錄檔中的任何相關資訊，請連絡 Microsoft 產品支援服務。</span><span class="sxs-lookup"><span data-stu-id="54309-124">Note the information in this message, and any relevant information in the event log, and contact Microsoft Product Support Services.</span></span>