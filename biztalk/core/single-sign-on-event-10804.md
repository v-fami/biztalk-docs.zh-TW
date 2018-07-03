---
title: 單一登入： 事件 10804 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4d98bef-fdc3-4627-bb5b-663fa502b965
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3a262448f4d07a01f726f111ca5ddd01901e9e7d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37017010"
---
# <a name="single-sign-on-event-10804"></a><span data-ttu-id="d9105-102">單一登入： 事件 10804</span><span class="sxs-lookup"><span data-stu-id="d9105-102">Single Sign-On: Event 10804</span></span>
## <a name="details"></a><span data-ttu-id="d9105-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d9105-103">Details</span></span>  
  
|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  <span data-ttu-id="d9105-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d9105-104">Product Name</span></span>   |                 <span data-ttu-id="d9105-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="d9105-105">Enterprise Single Sign-On</span></span>                  |
| <span data-ttu-id="d9105-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="d9105-106">Product Version</span></span> | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    <span data-ttu-id="d9105-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d9105-107">Event ID</span></span>     |                           <span data-ttu-id="d9105-108">10804</span><span class="sxs-lookup"><span data-stu-id="d9105-108">10804</span></span>                            |
|  <span data-ttu-id="d9105-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="d9105-109">Event Source</span></span>   |                           <span data-ttu-id="d9105-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="d9105-110">ENTSSO</span></span>                           |
|    <span data-ttu-id="d9105-111">元件</span><span class="sxs-lookup"><span data-stu-id="d9105-111">Component</span></span>    |                            <span data-ttu-id="d9105-112">不適用</span><span class="sxs-lookup"><span data-stu-id="d9105-112">N/A</span></span>                             |
|  <span data-ttu-id="d9105-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d9105-113">Symbolic Name</span></span>  |                <span data-ttu-id="d9105-114">ENTSSO_E_INCORRECT_COMPUTER</span><span class="sxs-lookup"><span data-stu-id="d9105-114">ENTSSO_E_INCORRECT_COMPUTER</span></span>                 |
|  <span data-ttu-id="d9105-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d9105-115">Message Text</span></span>   |     <span data-ttu-id="d9105-116">此配接器不是針對此電腦設定。</span><span class="sxs-lookup"><span data-stu-id="d9105-116">This adapter is not configured for this computer.</span></span>      |
  
## <a name="explanation"></a><span data-ttu-id="d9105-117">說明</span><span class="sxs-lookup"><span data-stu-id="d9105-117">Explanation</span></span>  
 <span data-ttu-id="d9105-118">每個配接器都設定為在特定電腦上執行，以其完整名稱識別。</span><span class="sxs-lookup"><span data-stu-id="d9105-118">Each adapter is configured to run on a specific computer, which is identified by its long name.</span></span> <span data-ttu-id="d9105-119">名稱不正確，或您嘗試在不同電腦上執行配接器。</span><span class="sxs-lookup"><span data-stu-id="d9105-119">Either the name is incorrect, or you are trying to run the adapter on a different computer.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d9105-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d9105-120">User Action</span></span>  
 <span data-ttu-id="d9105-121">請參閱此配接器的組態來判斷適當電腦的適當名稱。</span><span class="sxs-lookup"><span data-stu-id="d9105-121">See the configuration for this adapter to determine the proper name of the appropriate computer.</span></span>