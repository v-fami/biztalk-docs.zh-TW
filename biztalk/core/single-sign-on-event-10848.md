---
title: 單一登入： 事件 10848 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61888420-29a6-4c64-a884-1b074b586f21
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 59a324ff0a5de2ac6d2292692f2132c10aaabc5b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991031"
---
# <a name="single-sign-on-event-10848"></a><span data-ttu-id="daa5b-102">單一登入： 事件 10848</span><span class="sxs-lookup"><span data-stu-id="daa5b-102">Single Sign-On: Event 10848</span></span>
## <a name="details"></a><span data-ttu-id="daa5b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="daa5b-103">Details</span></span>  
  
|                 |                                                                                            |
|-----------------|--------------------------------------------------------------------------------------------|
|  <span data-ttu-id="daa5b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="daa5b-104">Product Name</span></span>   |                                 <span data-ttu-id="daa5b-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="daa5b-105">Enterprise Single Sign-On</span></span>                                  |
| <span data-ttu-id="daa5b-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="daa5b-106">Product Version</span></span> |                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                 |
|    <span data-ttu-id="daa5b-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="daa5b-107">Event ID</span></span>     |                                           <span data-ttu-id="daa5b-108">10848</span><span class="sxs-lookup"><span data-stu-id="daa5b-108">10848</span></span>                                            |
|  <span data-ttu-id="daa5b-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="daa5b-109">Event Source</span></span>   |                                           <span data-ttu-id="daa5b-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="daa5b-110">ENTSSO</span></span>                                           |
|    <span data-ttu-id="daa5b-111">元件</span><span class="sxs-lookup"><span data-stu-id="daa5b-111">Component</span></span>    |                                            <span data-ttu-id="daa5b-112">不適用</span><span class="sxs-lookup"><span data-stu-id="daa5b-112">N/A</span></span>                                             |
|  <span data-ttu-id="daa5b-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="daa5b-113">Symbolic Name</span></span>  |                         <span data-ttu-id="daa5b-114">ENTSSO_E_DIRECT_SYNC_NOT_ALLOWED_AMBIGUOUS</span><span class="sxs-lookup"><span data-stu-id="daa5b-114">ENTSSO_E_DIRECT_SYNC_NOT_ALLOWED_AMBIGUOUS</span></span>                         |
|  <span data-ttu-id="daa5b-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="daa5b-115">Message Text</span></span>   | <span data-ttu-id="daa5b-116">因為欄位模稜兩可，所以不允許這個應用程式的直接密碼同步。</span><span class="sxs-lookup"><span data-stu-id="daa5b-116">Direct password sync is not allowed for this application because its fields are ambiguous.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="daa5b-117">說明</span><span class="sxs-lookup"><span data-stu-id="daa5b-117">Explanation</span></span>  
 <span data-ttu-id="daa5b-118">如果有兩個以上的欄位，則只有唯一一個必須標示為密碼同步。</span><span class="sxs-lookup"><span data-stu-id="daa5b-118">If there are more than two fields, then one and only one must be marked for password sync.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="daa5b-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="daa5b-119">User Action</span></span>  
 <span data-ttu-id="daa5b-120">若要修正這種情況，您必須刪除應用程式然後重新建立，讓應用程式遵循這些準則。</span><span class="sxs-lookup"><span data-stu-id="daa5b-120">To remedy this situation, you must delete the application and recreate it so that it follows these guidelines.</span></span>