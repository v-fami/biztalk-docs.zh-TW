---
title: 單一登入： 事件 10843 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 847e464e-5733-4703-905f-d44a4c4f5cc3
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40b7e03f54d4c4ac2b7074d2aa13d771ce20a9e5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012999"
---
# <a name="single-sign-on-event-10843"></a><span data-ttu-id="f6a1d-102">單一登入： 事件 10843</span><span class="sxs-lookup"><span data-stu-id="f6a1d-102">Single Sign-On: Event 10843</span></span>
## <a name="details"></a><span data-ttu-id="f6a1d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f6a1d-103">Details</span></span>  
  
|                 |                                                                                                                                                                     |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="f6a1d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f6a1d-104">Product Name</span></span>   |                                                                      <span data-ttu-id="f6a1d-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="f6a1d-105">Enterprise Single Sign-On</span></span>                                                                      |
| <span data-ttu-id="f6a1d-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="f6a1d-106">Product Version</span></span> |                                                     [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                      |
|    <span data-ttu-id="f6a1d-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f6a1d-107">Event ID</span></span>     |                                                                                <span data-ttu-id="f6a1d-108">10843</span><span class="sxs-lookup"><span data-stu-id="f6a1d-108">10843</span></span>                                                                                |
|  <span data-ttu-id="f6a1d-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="f6a1d-109">Event Source</span></span>   |                                                                               <span data-ttu-id="f6a1d-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="f6a1d-110">ENTSSO</span></span>                                                                                |
|    <span data-ttu-id="f6a1d-111">元件</span><span class="sxs-lookup"><span data-stu-id="f6a1d-111">Component</span></span>    |                                                                                 <span data-ttu-id="f6a1d-112">不適用</span><span class="sxs-lookup"><span data-stu-id="f6a1d-112">N/A</span></span>                                                                                 |
|  <span data-ttu-id="f6a1d-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f6a1d-113">Symbolic Name</span></span>  |                                                                         <span data-ttu-id="f6a1d-114">ENTSSO_E_NO_SECRET2</span><span class="sxs-lookup"><span data-stu-id="f6a1d-114">ENTSSO_E_NO_SECRET2</span></span>                                                                         |
|  <span data-ttu-id="f6a1d-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f6a1d-115">Message Text</span></span>   | <span data-ttu-id="f6a1d-116">無法執行加密或解密，因為無法從主要密碼伺服器可用的祕密。</span><span class="sxs-lookup"><span data-stu-id="f6a1d-116">Cannot perform encryption or decryption because the secret is not available from the master secret server.</span></span> <span data-ttu-id="f6a1d-117">請參閱事件日誌 (在電腦 ‘%1’ 上) 中的相關錯誤。</span><span class="sxs-lookup"><span data-stu-id="f6a1d-117">See the event log (on computer ‘%1’) for related errors.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="f6a1d-118">說明</span><span class="sxs-lookup"><span data-stu-id="f6a1d-118">Explanation</span></span>  
 <span data-ttu-id="f6a1d-119">存取遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="f6a1d-119">Access is denied.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f6a1d-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f6a1d-120">User Action</span></span>  
 <span data-ttu-id="f6a1d-121">主要密碼伺服器離線，或在主要密碼伺服器缺少必要的主要祕密。</span><span class="sxs-lookup"><span data-stu-id="f6a1d-121">Either the master secret server is off-line, or the master secret server is missing the required master secret.</span></span> <span data-ttu-id="f6a1d-122">在指定電腦的相關錯誤，請參閱事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="f6a1d-122">See the event log on the specified computer for related errors.</span></span>