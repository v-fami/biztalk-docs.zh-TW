---
title: 單一登入： 事件 11049 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 031ec1a6-4b2b-46b2-9dbb-5525d758651f
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45ac6095950e02e7e73ab287b180bc22d88b4191
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277438"
---
# <a name="single-sign-on-event-11049"></a><span data-ttu-id="86abf-102">單一登入： 事件 11049</span><span class="sxs-lookup"><span data-stu-id="86abf-102">Single Sign-On: Event 11049</span></span>
## <a name="details"></a><span data-ttu-id="86abf-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="86abf-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="86abf-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="86abf-104">Product Name</span></span>|<span data-ttu-id="86abf-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="86abf-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="86abf-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="86abf-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="86abf-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="86abf-107">Event ID</span></span>|<span data-ttu-id="86abf-108">11049</span><span class="sxs-lookup"><span data-stu-id="86abf-108">11049</span></span>|  
|<span data-ttu-id="86abf-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="86abf-109">Event Source</span></span>|<span data-ttu-id="86abf-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="86abf-110">ENTSSO</span></span>|  
|<span data-ttu-id="86abf-111">元件</span><span class="sxs-lookup"><span data-stu-id="86abf-111">Component</span></span>|<span data-ttu-id="86abf-112">不適用</span><span class="sxs-lookup"><span data-stu-id="86abf-112">N/A</span></span>|  
|<span data-ttu-id="86abf-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="86abf-113">Symbolic Name</span></span>|<span data-ttu-id="86abf-114">SSO_ERROR_DTC_FAILED</span><span class="sxs-lookup"><span data-stu-id="86abf-114">SSO_ERROR_DTC_FAILED</span></span>|  
|<span data-ttu-id="86abf-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="86abf-115">Message Text</span></span>|<span data-ttu-id="86abf-116">無法取得 MSDTC。</span><span class="sxs-lookup"><span data-stu-id="86abf-116">Could not get MSDTC.</span></span> <span data-ttu-id="86abf-117">SSO 需要 MSDTC，才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="86abf-117">SSO requires MSDTC for correct operation.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="86abf-118">說明</span><span class="sxs-lookup"><span data-stu-id="86abf-118">Explanation</span></span>  
 <span data-ttu-id="86abf-119">ENTSSO 系統無法連接至 Microsoft 分散式交易協調器 (MSDTC)。</span><span class="sxs-lookup"><span data-stu-id="86abf-119">The ENTSSO system could not connect to the Microsoft Distributed Transaction Coordinator (MSDTC).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="86abf-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="86abf-120">User Action</span></span>  
 <span data-ttu-id="86abf-121">請檢查 MSDTC 目前是否正在運作。</span><span class="sxs-lookup"><span data-stu-id="86abf-121">Check to see if MSDTC is currently operational.</span></span>  
  
 <span data-ttu-id="86abf-122">如需 MSDTC 問題的說明，請參閱[疑難排解 MSDTC 問題的](../core/troubleshooting-problems-with-msdtc.md)。</span><span class="sxs-lookup"><span data-stu-id="86abf-122">For help on MSDTC issues, see [Troubleshooting Problems with MSDTC](../core/troubleshooting-problems-with-msdtc.md).</span></span>