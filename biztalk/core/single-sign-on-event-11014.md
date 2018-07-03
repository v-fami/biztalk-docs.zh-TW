---
title: 單一登入： 事件 11014 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71e4c9bd-8bda-46ca-9e76-f7b4fa033167
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e86642a7f62b53d45f20e140131d6a12d0771ec
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001128"
---
# <a name="single-sign-on-event-11014"></a><span data-ttu-id="916c3-102">單一登入： 事件 11014</span><span class="sxs-lookup"><span data-stu-id="916c3-102">Single Sign-On: Event 11014</span></span>
## <a name="details"></a><span data-ttu-id="916c3-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="916c3-103">Details</span></span>  
  
|                 |                                                                                                                                                          |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="916c3-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="916c3-104">Product Name</span></span>   |                                                                <span data-ttu-id="916c3-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="916c3-105">Enterprise Single Sign-On</span></span>                                                                 |
| <span data-ttu-id="916c3-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="916c3-106">Product Version</span></span> |                                                [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                |
|    <span data-ttu-id="916c3-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="916c3-107">Event ID</span></span>     |                                                                          <span data-ttu-id="916c3-108">11014</span><span class="sxs-lookup"><span data-stu-id="916c3-108">11014</span></span>                                                                           |
|  <span data-ttu-id="916c3-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="916c3-109">Event Source</span></span>   |                                                                          <span data-ttu-id="916c3-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="916c3-110">ENTSSO</span></span>                                                                          |
|    <span data-ttu-id="916c3-111">元件</span><span class="sxs-lookup"><span data-stu-id="916c3-111">Component</span></span>    |                                                                           <span data-ttu-id="916c3-112">不適用</span><span class="sxs-lookup"><span data-stu-id="916c3-112">N/A</span></span>                                                                            |
|  <span data-ttu-id="916c3-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="916c3-113">Symbolic Name</span></span>  |                                                                  <span data-ttu-id="916c3-114">SSO_ERROR_ACCESS_CHECK</span><span class="sxs-lookup"><span data-stu-id="916c3-114">SSO_ERROR_ACCESS_CHECK</span></span>                                                                  |
|  <span data-ttu-id="916c3-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="916c3-115">Message Text</span></span>   | <span data-ttu-id="916c3-116">存取檢查 failed.%r</span><span class="sxs-lookup"><span data-stu-id="916c3-116">Access check failed.%r</span></span><br /><br /> <span data-ttu-id="916c3-117">用戶端使用者： %1\\%2 %r</span><span class="sxs-lookup"><span data-stu-id="916c3-117">Client User: %1\\%2%r</span></span><br /><br /> <span data-ttu-id="916c3-118">應用程式名稱: %3 %r</span><span class="sxs-lookup"><span data-stu-id="916c3-118">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="916c3-119">其他資料: %4 %r</span><span class="sxs-lookup"><span data-stu-id="916c3-119">Additional Data: %4%r</span></span><br /><br /> <span data-ttu-id="916c3-120">錯誤碼： %5</span><span class="sxs-lookup"><span data-stu-id="916c3-120">Error Code: %5</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="916c3-121">說明</span><span class="sxs-lookup"><span data-stu-id="916c3-121">Explanation</span></span>  
 <span data-ttu-id="916c3-122">存取檢查失敗的用戶端和列出應用程式。</span><span class="sxs-lookup"><span data-stu-id="916c3-122">The access check failed for the client and application listed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="916c3-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="916c3-123">User Action</span></span>  
 <span data-ttu-id="916c3-124">其他的資訊應該能讓您修正此問題。</span><span class="sxs-lookup"><span data-stu-id="916c3-124">The additional information should enable you to fix the problem.</span></span> <span data-ttu-id="916c3-125">若要避免此錯誤在未來，您可以也降低的稽核層級。</span><span class="sxs-lookup"><span data-stu-id="916c3-125">To avoid this error in the future, you can also lower the audit level.</span></span>