---
title: 無法合併因名稱衝突的作業 |Microsoft 文件
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
ms.openlocfilehash: a8f884b4eea6be64f1d1575b157805703d12cee3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231710"
---
# <a name="cannot-merge-operations-due-to-name-collision"></a><span data-ttu-id="9f7b0-102">無法合併作業，因為名稱衝突</span><span class="sxs-lookup"><span data-stu-id="9f7b0-102">Cannot merge operations due to name collision</span></span>
## <a name="details"></a><span data-ttu-id="9f7b0-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9f7b0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9f7b0-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="9f7b0-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="9f7b0-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="9f7b0-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="9f7b0-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="9f7b0-106">Event ID</span></span>|<span data-ttu-id="9f7b0-107">0</span><span class="sxs-lookup"><span data-stu-id="9f7b0-107">0</span></span>|  
|<span data-ttu-id="9f7b0-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="9f7b0-108">Event Source</span></span>|<span data-ttu-id="9f7b0-109">0</span><span class="sxs-lookup"><span data-stu-id="9f7b0-109">0</span></span>|  
|<span data-ttu-id="9f7b0-110">元件</span><span class="sxs-lookup"><span data-stu-id="9f7b0-110">Component</span></span>|<span data-ttu-id="9f7b0-111">0</span><span class="sxs-lookup"><span data-stu-id="9f7b0-111">0</span></span>|  
|<span data-ttu-id="9f7b0-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="9f7b0-112">Symbolic Name</span></span>|<span data-ttu-id="9f7b0-113">0</span><span class="sxs-lookup"><span data-stu-id="9f7b0-113">0</span></span>|  
|<span data-ttu-id="9f7b0-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="9f7b0-114">Message Text</span></span>|<span data-ttu-id="9f7b0-115">無法合併操作"{0}"，因為名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="9f7b0-115">Cannot merge operation "{0}" due to name collision.</span></span> <span data-ttu-id="9f7b0-116">Web 服務中的所有作業必須都有唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="9f7b0-116">All operations in a web service must have unique names.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9f7b0-117">說明</span><span class="sxs-lookup"><span data-stu-id="9f7b0-117">Explanation</span></span>  
 <span data-ttu-id="9f7b0-118">此錯誤表示連接埠名稱或操作名稱的兩個不同的連接埠正在合併具有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="9f7b0-118">This error indicates the port name or the operation name of two different ports that are being merged have the same name.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9f7b0-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="9f7b0-119">User Action</span></span>  
 <span data-ttu-id="9f7b0-120">使用連接埠組態精靈，請確定正在進行合併的所有連接埠有不同的連接埠名稱和作業。</span><span class="sxs-lookup"><span data-stu-id="9f7b0-120">Using the Port Configuration Wizard, ensure that all the ports that are being merged have different port names and operation.</span></span>  
  
 <span data-ttu-id="9f7b0-121">如需有關通訊埠組態的詳細資訊，請參閱下列資源中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="9f7b0-121">For additional information on port configuration, see the following resource in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="9f7b0-122">如何執行連接埠組態精靈</span><span class="sxs-lookup"><span data-stu-id="9f7b0-122">How to Run the Port Configuration Wizard</span></span>](../core/how-to-run-the-port-configuration-wizard.md)