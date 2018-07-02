---
title: 命名空間中找不到類型 |Microsoft Docs
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
ms.openlocfilehash: 8b369b3ce29b989f01f0ea95d6f32a663d7e7bc5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980759"
---
# <a name="type-cannot-be-found-in-namespace"></a><span data-ttu-id="99792-102">命名空間中找不到類型</span><span class="sxs-lookup"><span data-stu-id="99792-102">Type cannot be found in namespace</span></span>
## <a name="details"></a><span data-ttu-id="99792-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="99792-103">Details</span></span>  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="99792-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="99792-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="99792-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="99792-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="99792-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="99792-106">Event ID</span></span>     |                                         <span data-ttu-id="99792-107">0</span><span class="sxs-lookup"><span data-stu-id="99792-107">0</span></span>                                          |
|  <span data-ttu-id="99792-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="99792-108">Event Source</span></span>   |                                         <span data-ttu-id="99792-109">0</span><span class="sxs-lookup"><span data-stu-id="99792-109">0</span></span>                                          |
|    <span data-ttu-id="99792-110">元件</span><span class="sxs-lookup"><span data-stu-id="99792-110">Component</span></span>    |                                         <span data-ttu-id="99792-111">0</span><span class="sxs-lookup"><span data-stu-id="99792-111">0</span></span>                                          |
|  <span data-ttu-id="99792-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="99792-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="99792-113">0</span><span class="sxs-lookup"><span data-stu-id="99792-113">0</span></span>                                          |
|  <span data-ttu-id="99792-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="99792-114">Message Text</span></span>   |                <span data-ttu-id="99792-115">錯誤： 類型 」{0}「 無法找到命名空間中 」{1}"</span><span class="sxs-lookup"><span data-stu-id="99792-115">Error: Type "{0}" cannot be found in namespace "{1}"</span></span>                |
  
## <a name="explanation"></a><span data-ttu-id="99792-116">說明</span><span class="sxs-lookup"><span data-stu-id="99792-116">Explanation</span></span>  
 <span data-ttu-id="99792-117">此錯誤表示所建立的成品參考不能在指定的命名空間中找到的類型。</span><span class="sxs-lookup"><span data-stu-id="99792-117">This error indicates artifacts that are created are referencing types which cannot be found in the namespace specified.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="99792-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="99792-118">User Action</span></span>  
 <span data-ttu-id="99792-119">新增包含找不到，類型的參考，並再次執行精靈，（如果您擁有想要使用的 WCF 服務時）。</span><span class="sxs-lookup"><span data-stu-id="99792-119">Add a reference that contain the type that is not found, and run the wizard again (if you own the WCF service that you are trying to consume).</span></span> <span data-ttu-id="99792-120">否則，請連絡服務提供者。</span><span class="sxs-lookup"><span data-stu-id="99792-120">Otherwise, contact the service provider.</span></span>