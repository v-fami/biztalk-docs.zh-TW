---
title: 無法匯入服務端點組態。 | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dae5154-04e2-4d9b-b2b2-85313683fd9e
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d33b9b4963b69ed732c16e266300e398d7884035
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994311"
---
# <a name="unable-to-import-service-endpoint-configuration"></a><span data-ttu-id="d2c16-103">無法匯入服務端點組態。</span><span class="sxs-lookup"><span data-stu-id="d2c16-103">Unable to import service endpoint configuration.</span></span>
## <a name="details"></a><span data-ttu-id="d2c16-104">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d2c16-104">Details</span></span>  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="d2c16-105">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d2c16-105">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="d2c16-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="d2c16-106">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="d2c16-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d2c16-107">Event ID</span></span>     |                                         <span data-ttu-id="d2c16-108">0</span><span class="sxs-lookup"><span data-stu-id="d2c16-108">0</span></span>                                          |
|  <span data-ttu-id="d2c16-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="d2c16-109">Event Source</span></span>   |                                         <span data-ttu-id="d2c16-110">0</span><span class="sxs-lookup"><span data-stu-id="d2c16-110">0</span></span>                                          |
|    <span data-ttu-id="d2c16-111">元件</span><span class="sxs-lookup"><span data-stu-id="d2c16-111">Component</span></span>    |                                         <span data-ttu-id="d2c16-112">0</span><span class="sxs-lookup"><span data-stu-id="d2c16-112">0</span></span>                                          |
|  <span data-ttu-id="d2c16-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d2c16-113">Symbolic Name</span></span>  |                                         <span data-ttu-id="d2c16-114">0</span><span class="sxs-lookup"><span data-stu-id="d2c16-114">0</span></span>                                          |
|  <span data-ttu-id="d2c16-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d2c16-115">Message Text</span></span>   |                  <span data-ttu-id="d2c16-116">無法匯入服務端點組態</span><span class="sxs-lookup"><span data-stu-id="d2c16-116">Unable to import service endpoint configuration</span></span>                   |
  
## <a name="explanation"></a><span data-ttu-id="d2c16-117">說明</span><span class="sxs-lookup"><span data-stu-id="d2c16-117">Explanation</span></span>  
 <span data-ttu-id="d2c16-118">可能有多個說明此錯誤。</span><span class="sxs-lookup"><span data-stu-id="d2c16-118">There could be more than one explanation for this error.</span></span> <span data-ttu-id="d2c16-119">組態檔可能包含無效的字元。</span><span class="sxs-lookup"><span data-stu-id="d2c16-119">The configuration file may contain invalid characters.</span></span> <span data-ttu-id="d2c16-120">根項目可能已遺失。</span><span class="sxs-lookup"><span data-stu-id="d2c16-120">The root element may be missing.</span></span> <span data-ttu-id="d2c16-121">根層級的資料可能不正確。</span><span class="sxs-lookup"><span data-stu-id="d2c16-121">The data at the root level may be invalid.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d2c16-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d2c16-122">User Action</span></span>  
 <span data-ttu-id="d2c16-123">驗證組態檔的有效性。</span><span class="sxs-lookup"><span data-stu-id="d2c16-123">Verify the validity of the configuration file.</span></span> <span data-ttu-id="d2c16-124">嘗試使用服務組態編輯器中開啟組態檔 (**svcConfigEditor.exe**)，並確認每個屬性。</span><span class="sxs-lookup"><span data-stu-id="d2c16-124">Try to open the configuration file with the Service Configuration Editor (**svcConfigEditor.exe**) and verify each property.</span></span>