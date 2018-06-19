---
title: 命名空間中找不到類型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 66387fa6-3ba3-499f-99d6-bb0033c68adc
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 515dd9b6b73b43bee22ffc7b67745bb45adcaf6c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22286454"
---
# <a name="type-cannot-be-found-in-namespace"></a><span data-ttu-id="7cc20-102">命名空間中找不到型別</span><span class="sxs-lookup"><span data-stu-id="7cc20-102">Type cannot be found in namespace</span></span>
## <a name="details"></a><span data-ttu-id="7cc20-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7cc20-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7cc20-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="7cc20-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="7cc20-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="7cc20-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="7cc20-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7cc20-106">Event ID</span></span>|<span data-ttu-id="7cc20-107">0</span><span class="sxs-lookup"><span data-stu-id="7cc20-107">0</span></span>|  
|<span data-ttu-id="7cc20-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="7cc20-108">Event Source</span></span>|<span data-ttu-id="7cc20-109">0</span><span class="sxs-lookup"><span data-stu-id="7cc20-109">0</span></span>|  
|<span data-ttu-id="7cc20-110">元件</span><span class="sxs-lookup"><span data-stu-id="7cc20-110">Component</span></span>|<span data-ttu-id="7cc20-111">0</span><span class="sxs-lookup"><span data-stu-id="7cc20-111">0</span></span>|  
|<span data-ttu-id="7cc20-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="7cc20-112">Symbolic Name</span></span>|<span data-ttu-id="7cc20-113">0</span><span class="sxs-lookup"><span data-stu-id="7cc20-113">0</span></span>|  
|<span data-ttu-id="7cc20-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="7cc20-114">Message Text</span></span>|<span data-ttu-id="7cc20-115">錯誤： 無法"{1}"命名空間中找到類型"{0}"</span><span class="sxs-lookup"><span data-stu-id="7cc20-115">Error: Type "{0}" cannot be found in namespace "{1}"</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7cc20-116">說明</span><span class="sxs-lookup"><span data-stu-id="7cc20-116">Explanation</span></span>  
 <span data-ttu-id="7cc20-117">此錯誤表示所建立的成品參考指定的命名空間中找不到型別。</span><span class="sxs-lookup"><span data-stu-id="7cc20-117">This error indicates artifacts that are created are referencing types which cannot be found in the namespace specified.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7cc20-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="7cc20-118">User Action</span></span>  
 <span data-ttu-id="7cc20-119">加入包含找不到，類型的參考，然後再次執行精靈，（如果您擁有想要使用的 WCF 服務）。</span><span class="sxs-lookup"><span data-stu-id="7cc20-119">Add a reference that contain the type that is not found, and run the wizard again (if you own the WCF service that you are trying to consume).</span></span> <span data-ttu-id="7cc20-120">否則，請連絡服務提供者。</span><span class="sxs-lookup"><span data-stu-id="7cc20-120">Otherwise, contact the service provider.</span></span>