---
title: 無法匯入用戶端端點組態 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8375e153-ed1c-4bf4-b461-ac026a4b3478
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f3faa6a12bee397edcadb3f15c12a47d763fdce
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987183"
---
# <a name="unable-to-import-client-endpoint-configuration"></a><span data-ttu-id="15dc8-102">無法匯入用戶端端點組態</span><span class="sxs-lookup"><span data-stu-id="15dc8-102">Unable to import client endpoint configuration</span></span>
## <a name="details"></a><span data-ttu-id="15dc8-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="15dc8-103">Details</span></span>  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="15dc8-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="15dc8-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="15dc8-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="15dc8-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="15dc8-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="15dc8-106">Event ID</span></span>     |                                         <span data-ttu-id="15dc8-107">0</span><span class="sxs-lookup"><span data-stu-id="15dc8-107">0</span></span>                                          |
|  <span data-ttu-id="15dc8-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="15dc8-108">Event Source</span></span>   |                                         <span data-ttu-id="15dc8-109">0</span><span class="sxs-lookup"><span data-stu-id="15dc8-109">0</span></span>                                          |
|    <span data-ttu-id="15dc8-110">元件</span><span class="sxs-lookup"><span data-stu-id="15dc8-110">Component</span></span>    |                                         <span data-ttu-id="15dc8-111">0</span><span class="sxs-lookup"><span data-stu-id="15dc8-111">0</span></span>                                          |
|  <span data-ttu-id="15dc8-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="15dc8-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="15dc8-113">0</span><span class="sxs-lookup"><span data-stu-id="15dc8-113">0</span></span>                                          |
|  <span data-ttu-id="15dc8-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="15dc8-114">Message Text</span></span>   |                   <span data-ttu-id="15dc8-115">無法匯入用戶端端點組態</span><span class="sxs-lookup"><span data-stu-id="15dc8-115">Unable to import client endpoint configuration</span></span>                   |
  
## <a name="explanation"></a><span data-ttu-id="15dc8-116">說明</span><span class="sxs-lookup"><span data-stu-id="15dc8-116">Explanation</span></span>  
 <span data-ttu-id="15dc8-117">可能有多個說明此錯誤。</span><span class="sxs-lookup"><span data-stu-id="15dc8-117">There could be more than one explanation for this error.</span></span> <span data-ttu-id="15dc8-118">組態檔可能包含無效的字元。</span><span class="sxs-lookup"><span data-stu-id="15dc8-118">The configuration file may contain invalid characters.</span></span> <span data-ttu-id="15dc8-119">根項目可能已遺失。</span><span class="sxs-lookup"><span data-stu-id="15dc8-119">The root element may be missing.</span></span> <span data-ttu-id="15dc8-120">根層級的資料可能不正確。</span><span class="sxs-lookup"><span data-stu-id="15dc8-120">The data at the root level may be invalid.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="15dc8-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="15dc8-121">User Action</span></span>  
 <span data-ttu-id="15dc8-122">驗證組態檔的有效性。</span><span class="sxs-lookup"><span data-stu-id="15dc8-122">Verify the validity of the configuration file.</span></span> <span data-ttu-id="15dc8-123">嘗試使用服務組態編輯器中開啟組態檔 (**svcConfigEditor.exe**)，並確認每個屬性。</span><span class="sxs-lookup"><span data-stu-id="15dc8-123">Try to open the configuration file with the Service Configuration Editor (**svcConfigEditor.exe**) and verify each property.</span></span>