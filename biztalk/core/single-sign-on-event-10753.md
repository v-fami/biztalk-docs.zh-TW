---
title: 單一登入： 事件 10753 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6b538083-180b-4a15-bedf-aac4fc351c30
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10fb7980b8c039c6ef02e52952564c581e88054b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969079"
---
# <a name="single-sign-on-event-10753"></a><span data-ttu-id="78d56-102">單一登入： 事件 10753</span><span class="sxs-lookup"><span data-stu-id="78d56-102">Single Sign-On: Event 10753</span></span>
## <a name="details"></a><span data-ttu-id="78d56-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="78d56-103">Details</span></span>  
  
|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  <span data-ttu-id="78d56-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="78d56-104">Product Name</span></span>   |                 <span data-ttu-id="78d56-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="78d56-105">Enterprise Single Sign-On</span></span>                  |
| <span data-ttu-id="78d56-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="78d56-106">Product Version</span></span> | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    <span data-ttu-id="78d56-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="78d56-107">Event ID</span></span>     |                           <span data-ttu-id="78d56-108">10753</span><span class="sxs-lookup"><span data-stu-id="78d56-108">10753</span></span>                            |
|  <span data-ttu-id="78d56-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="78d56-109">Event Source</span></span>   |                           <span data-ttu-id="78d56-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="78d56-110">ENTSSO</span></span>                           |
|    <span data-ttu-id="78d56-111">元件</span><span class="sxs-lookup"><span data-stu-id="78d56-111">Component</span></span>    |                            <span data-ttu-id="78d56-112">不適用</span><span class="sxs-lookup"><span data-stu-id="78d56-112">N/A</span></span>                             |
|  <span data-ttu-id="78d56-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="78d56-113">Symbolic Name</span></span>  |                  <span data-ttu-id="78d56-114">ENTSSO_E_MAPPING_EXISTS</span><span class="sxs-lookup"><span data-stu-id="78d56-114">ENTSSO_E_MAPPING_EXISTS</span></span>                   |
|  <span data-ttu-id="78d56-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="78d56-115">Message Text</span></span>   |                <span data-ttu-id="78d56-116">對應已經存在。</span><span class="sxs-lookup"><span data-stu-id="78d56-116">The mapping already exists.</span></span>                 |
  
## <a name="explanation"></a><span data-ttu-id="78d56-117">說明</span><span class="sxs-lookup"><span data-stu-id="78d56-117">Explanation</span></span>  
 <span data-ttu-id="78d56-118">此對應已經存在，已在使用中的 Windows 帳戶或外部的帳戶。</span><span class="sxs-lookup"><span data-stu-id="78d56-118">This mapping already exists, either on the Windows account already in use or the external account.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="78d56-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="78d56-119">User Action</span></span>  
 <span data-ttu-id="78d56-120">檢查現有的對應與您嘗試建立的對應。</span><span class="sxs-lookup"><span data-stu-id="78d56-120">Check the existing mappings and the mapping you are trying to create.</span></span> <span data-ttu-id="78d56-121">如果您已經想要的對應存在，使用它，並刪除您新的一個。</span><span class="sxs-lookup"><span data-stu-id="78d56-121">If the mapping you want already exists, use it and delete your new one.</span></span> <span data-ttu-id="78d56-122">如果沒有，請刪除您的新帳戶，並重新建立它。</span><span class="sxs-lookup"><span data-stu-id="78d56-122">If not, delete your new one and recreate it.</span></span>