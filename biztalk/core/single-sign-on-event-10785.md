---
title: 單一登入： 事件 10785 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4f4a2ad-a378-4806-ba16-d2872c4773f1
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96194f9ab4a057301e9c0a20d4c222f730e70bfb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991511"
---
# <a name="single-sign-on-event-10785"></a><span data-ttu-id="36185-102">單一登入： 事件 10785</span><span class="sxs-lookup"><span data-stu-id="36185-102">Single Sign-On: Event 10785</span></span>
## <a name="details"></a><span data-ttu-id="36185-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="36185-103">Details</span></span>  
  
|                 |                                                                |
|-----------------|----------------------------------------------------------------|
|  <span data-ttu-id="36185-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="36185-104">Product Name</span></span>   |                   <span data-ttu-id="36185-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="36185-105">Enterprise Single Sign-On</span></span>                    |
| <span data-ttu-id="36185-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="36185-106">Product Version</span></span> |   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]   |
|    <span data-ttu-id="36185-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="36185-107">Event ID</span></span>     |                             <span data-ttu-id="36185-108">10785</span><span class="sxs-lookup"><span data-stu-id="36185-108">10785</span></span>                              |
|  <span data-ttu-id="36185-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="36185-109">Event Source</span></span>   |                             <span data-ttu-id="36185-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="36185-110">ENTSSO</span></span>                             |
|    <span data-ttu-id="36185-111">元件</span><span class="sxs-lookup"><span data-stu-id="36185-111">Component</span></span>    |                              <span data-ttu-id="36185-112">不適用</span><span class="sxs-lookup"><span data-stu-id="36185-112">N/A</span></span>                               |
|  <span data-ttu-id="36185-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="36185-113">Symbolic Name</span></span>  |                       <span data-ttu-id="36185-114">ENTSSO_E_DB_ACCESS</span><span class="sxs-lookup"><span data-stu-id="36185-114">ENTSSO_E_DB_ACCESS</span></span>                       |
|  <span data-ttu-id="36185-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="36185-115">Message Text</span></span>   | <span data-ttu-id="36185-116">嘗試存取 SSO 資料庫時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="36185-116">An error occurred while attempting to access the SSO database.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="36185-117">說明</span><span class="sxs-lookup"><span data-stu-id="36185-117">Explanation</span></span>  
 <span data-ttu-id="36185-118">ENTSSO 資料庫可能已離線。</span><span class="sxs-lookup"><span data-stu-id="36185-118">The ENTSSO database may be offline.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="36185-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="36185-119">User Action</span></span>  
 <span data-ttu-id="36185-120">有系統管理員檢查 ENTSSO 伺服器的事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="36185-120">Have your system administrator check the Event Log on the ENTSSO server.</span></span>