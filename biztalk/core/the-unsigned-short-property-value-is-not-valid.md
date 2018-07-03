---
title: 不帶正負號的 Short 屬性值無效。 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31600ed6-20bc-4382-9eb3-4d6fa9646411
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 198596c03d6ef7c5cd3b9005458f6eea18bd9b9a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011735"
---
# <a name="the-unsigned-short-property-value-is-not-valid"></a><span data-ttu-id="d0671-102">不帶正負號的 Short 屬性值無效</span><span class="sxs-lookup"><span data-stu-id="d0671-102">The unsigned Short property value is not valid</span></span>
## <a name="details"></a><span data-ttu-id="d0671-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d0671-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="d0671-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d0671-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="d0671-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d0671-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="d0671-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d0671-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="d0671-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="d0671-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d0671-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="d0671-108"> EDI</span></span> |
|    <span data-ttu-id="d0671-109">元件</span><span class="sxs-lookup"><span data-stu-id="d0671-109">Component</span></span>    |                                       <span data-ttu-id="d0671-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="d0671-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="d0671-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d0671-111">Symbolic Name</span></span>  |                                <span data-ttu-id="d0671-112">Err_InvalidUnsignedShort</span><span class="sxs-lookup"><span data-stu-id="d0671-112">Err_InvalidUnsignedShort</span></span>                                |
|  <span data-ttu-id="d0671-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d0671-113">Message Text</span></span>   |                    <span data-ttu-id="d0671-114">不帶正負號的 Short 屬性值不是有效的。</span><span class="sxs-lookup"><span data-stu-id="d0671-114">The unsigned Short property value is not valid.</span></span>                     |
  
## <a name="explanation"></a><span data-ttu-id="d0671-115">說明</span><span class="sxs-lookup"><span data-stu-id="d0671-115">Explanation</span></span>  
 <span data-ttu-id="d0671-116">這個錯誤/警告/資訊事件表示 BizTalk Server 無法嘗試決定是否要批次處理的訊息比較的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="d0671-116">This Error/Warning/Information event indicates BizTalk Server was unable to compare a context property while trying to decide whether to Batch a message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d0671-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d0671-117">User Action</span></span>  
 <span data-ttu-id="d0671-118">若要解決這個錯誤，請確定在作用中批次中提供的篩選條件未指定內容屬性具有無效的值不帶正負號的短的 XSD 型別。</span><span class="sxs-lookup"><span data-stu-id="d0671-118">To resolve this error, ensure that the filter provided in Active batches doesn’t specify a context property which has an XSD type of unsigned Short with an invalid value.</span></span>