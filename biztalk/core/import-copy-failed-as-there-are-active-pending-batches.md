---
title: 匯入複製失敗，因為有作用-擱置中的批次 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17803f0a-3c70-4a8a-8e8d-7f874ed9ad92
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a74bfdccbd12db00cd0f325aedee2e42cc76729
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970535"
---
# <a name="import-copy-failed-as-there-are-active-pending-batches"></a><span data-ttu-id="1ccee-102">匯入複製失敗，因為有作用-擱置中的批次</span><span class="sxs-lookup"><span data-stu-id="1ccee-102">Import-Copy failed as there are active-pending batches</span></span>
## <a name="details"></a><span data-ttu-id="1ccee-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1ccee-103">Details</span></span>  
  
|                 |                                                                                                                |
|-----------------|----------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="1ccee-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1ccee-104">Product Name</span></span>   |               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]               |
| <span data-ttu-id="1ccee-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="1ccee-105">Product Version</span></span> |                           [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                           |
|    <span data-ttu-id="1ccee-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1ccee-106">Event ID</span></span>     |                                                       -                                                        |
|  <span data-ttu-id="1ccee-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="1ccee-107">Event Source</span></span>   |             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="1ccee-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="1ccee-108"> EDI</span></span>             |
|    <span data-ttu-id="1ccee-109">元件</span><span class="sxs-lookup"><span data-stu-id="1ccee-109">Component</span></span>    |                                                   <span data-ttu-id="1ccee-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="1ccee-110">EDI Engine</span></span>                                                   |
|  <span data-ttu-id="1ccee-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1ccee-111">Symbolic Name</span></span>  |                                              <span data-ttu-id="1ccee-112">Err_ActiveBatchFound</span><span class="sxs-lookup"><span data-stu-id="1ccee-112">Err_ActiveBatchFound</span></span>                                              |
|  <span data-ttu-id="1ccee-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1ccee-113">Message Text</span></span>   | <span data-ttu-id="1ccee-114">匯入/複製失敗，因為有作用中/擱置中的批次。</span><span class="sxs-lookup"><span data-stu-id="1ccee-114">Import/Copy failed as there are active/pending batches.</span></span> <span data-ttu-id="1ccee-115">停止作用中/擱置中的批次，然後再次嘗試匯入/複製。</span><span class="sxs-lookup"><span data-stu-id="1ccee-115">Stop active/pending batches and try importing/copying.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="1ccee-116">說明</span><span class="sxs-lookup"><span data-stu-id="1ccee-116">Explanation</span></span>  
 <span data-ttu-id="1ccee-117">這個錯誤/警告/資訊事件表示 BizTalk Server 無法匯入繫結檔案，或複製的設定，受影響的合約具有一或多個作用中或擱置中的批次。</span><span class="sxs-lookup"><span data-stu-id="1ccee-117">This Error/Warning/Information event indicates BizTalk Server was unable to Import a binding file or copy the settings as the affected Agreement(s) have one or more active or pending batch.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1ccee-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1ccee-118">User Action</span></span>  
 <span data-ttu-id="1ccee-119">若要解決這個錯誤，請確定在受影響的協議中的所有批次會顯示為協議屬性中已停止。</span><span class="sxs-lookup"><span data-stu-id="1ccee-119">To resolve this error, ensure that all the batches in affected agreements are showing as stopped in the Agreement properties.</span></span>