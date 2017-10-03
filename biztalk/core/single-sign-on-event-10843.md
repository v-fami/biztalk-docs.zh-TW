---
title: "單一登入： 事件 10843 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 847e464e-5733-4703-905f-d44a4c4f5cc3
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd86a39d515858e1cda09317ba6139bc67c95ed4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10843"></a><span data-ttu-id="6c664-102">單一登入： 事件 10843</span><span class="sxs-lookup"><span data-stu-id="6c664-102">Single Sign-On: Event 10843</span></span>
## <a name="details"></a><span data-ttu-id="6c664-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6c664-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6c664-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="6c664-104">Product Name</span></span>|<span data-ttu-id="6c664-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="6c664-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="6c664-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="6c664-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="6c664-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="6c664-107">Event ID</span></span>|<span data-ttu-id="6c664-108">10843</span><span class="sxs-lookup"><span data-stu-id="6c664-108">10843</span></span>|  
|<span data-ttu-id="6c664-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="6c664-109">Event Source</span></span>|<span data-ttu-id="6c664-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="6c664-110">ENTSSO</span></span>|  
|<span data-ttu-id="6c664-111">元件</span><span class="sxs-lookup"><span data-stu-id="6c664-111">Component</span></span>|<span data-ttu-id="6c664-112">不適用</span><span class="sxs-lookup"><span data-stu-id="6c664-112">N/A</span></span>|  
|<span data-ttu-id="6c664-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="6c664-113">Symbolic Name</span></span>|<span data-ttu-id="6c664-114">ENTSSO_E_NO_SECRET2</span><span class="sxs-lookup"><span data-stu-id="6c664-114">ENTSSO_E_NO_SECRET2</span></span>|  
|<span data-ttu-id="6c664-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="6c664-115">Message Text</span></span>|<span data-ttu-id="6c664-116">無法執行加密或解密，因為沒有可從主要密碼伺服器的密碼。</span><span class="sxs-lookup"><span data-stu-id="6c664-116">Cannot perform encryption or decryption because the secret is not available from the master secret server.</span></span> <span data-ttu-id="6c664-117">請參閱事件日誌 (在電腦 ‘%1’ 上) 中的相關錯誤。</span><span class="sxs-lookup"><span data-stu-id="6c664-117">See the event log (on computer ‘%1’) for related errors.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6c664-118">說明</span><span class="sxs-lookup"><span data-stu-id="6c664-118">Explanation</span></span>  
 <span data-ttu-id="6c664-119">存取遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="6c664-119">Access is denied.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6c664-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="6c664-120">User Action</span></span>  
 <span data-ttu-id="6c664-121">主要密碼伺服器已離線，或是在主要密碼伺服器遺失必要的主要密碼。</span><span class="sxs-lookup"><span data-stu-id="6c664-121">Either the master secret server is off-line, or the master secret server is missing the required master secret.</span></span> <span data-ttu-id="6c664-122">指定電腦上為相關錯誤，請參閱事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="6c664-122">See the event log on the specified computer for related errors.</span></span>