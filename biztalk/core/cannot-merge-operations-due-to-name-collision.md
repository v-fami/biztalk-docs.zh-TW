---
title: 無法合併作業，因為名稱衝突 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81ddb8b7-6f7e-420c-b7c3-921c0e305326
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57bbb3b085af45ede5632e20f67d5e6c0c4e304e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992319"
---
# <a name="cannot-merge-operations-due-to-name-collision"></a><span data-ttu-id="c75e4-102">無法合併作業，因為名稱衝突</span><span class="sxs-lookup"><span data-stu-id="c75e4-102">Cannot merge operations due to name collision</span></span>
## <a name="details"></a><span data-ttu-id="c75e4-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c75e4-103">Details</span></span>  
  
|                 |                                                                                                             |
|-----------------|-------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="c75e4-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c75e4-104">Product Name</span></span>   |             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]              |
| <span data-ttu-id="c75e4-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="c75e4-105">Product Version</span></span> |                         [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                          |
|    <span data-ttu-id="c75e4-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c75e4-106">Event ID</span></span>     |                                                      <span data-ttu-id="c75e4-107">0</span><span class="sxs-lookup"><span data-stu-id="c75e4-107">0</span></span>                                                      |
|  <span data-ttu-id="c75e4-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="c75e4-108">Event Source</span></span>   |                                                      <span data-ttu-id="c75e4-109">0</span><span class="sxs-lookup"><span data-stu-id="c75e4-109">0</span></span>                                                      |
|    <span data-ttu-id="c75e4-110">元件</span><span class="sxs-lookup"><span data-stu-id="c75e4-110">Component</span></span>    |                                                      <span data-ttu-id="c75e4-111">0</span><span class="sxs-lookup"><span data-stu-id="c75e4-111">0</span></span>                                                      |
|  <span data-ttu-id="c75e4-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c75e4-112">Symbolic Name</span></span>  |                                                      <span data-ttu-id="c75e4-113">0</span><span class="sxs-lookup"><span data-stu-id="c75e4-113">0</span></span>                                                      |
|  <span data-ttu-id="c75e4-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c75e4-114">Message Text</span></span>   | <span data-ttu-id="c75e4-115">無法合併作業 「{0}"因為名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="c75e4-115">Cannot merge operation "{0}" due to name collision.</span></span> <span data-ttu-id="c75e4-116">Web 服務中的所有作業必須都有唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="c75e4-116">All operations in a web service must have unique names.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="c75e4-117">說明</span><span class="sxs-lookup"><span data-stu-id="c75e4-117">Explanation</span></span>  
 <span data-ttu-id="c75e4-118">此錯誤表示的連接埠名稱或作業名稱的兩個不同的連接埠正在合併具有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="c75e4-118">This error indicates the port name or the operation name of two different ports that are being merged have the same name.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c75e4-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c75e4-119">User Action</span></span>  
 <span data-ttu-id="c75e4-120">使用連接埠組態精靈，請確定正在進行合併的所有連接埠有不同的連接埠名稱和作業。</span><span class="sxs-lookup"><span data-stu-id="c75e4-120">Using the Port Configuration Wizard, ensure that all the ports that are being merged have different port names and operation.</span></span>  
  
 <span data-ttu-id="c75e4-121">如需有關通訊埠組態的詳細資訊，請參閱下列資源中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="c75e4-121">For additional information on port configuration, see the following resource in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="c75e4-122">如何執行連接埠組態精靈</span><span class="sxs-lookup"><span data-stu-id="c75e4-122">How to Run the Port Configuration Wizard</span></span>](../core/how-to-run-the-port-configuration-wizard.md)