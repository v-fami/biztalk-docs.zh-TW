---
title: Equals、 NotEquals 和 Exists 比較只能是 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aad902a2-d0dc-4d91-87a7-a6305e2f40e0
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50499ea6ab9f002d36c213a8bca871884d3b077a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023468"
---
# <a name="the-comparison-can-only-be-equals-notequals-and-exists"></a><span data-ttu-id="89875-102">比較只能 Equals、 NotEquals 和 Exists</span><span class="sxs-lookup"><span data-stu-id="89875-102">The Comparison can only be Equals, NotEquals and Exists</span></span>
## <a name="details"></a><span data-ttu-id="89875-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="89875-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="89875-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="89875-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="89875-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="89875-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="89875-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="89875-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="89875-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="89875-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="89875-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="89875-108"> EDI</span></span> |
|    <span data-ttu-id="89875-109">元件</span><span class="sxs-lookup"><span data-stu-id="89875-109">Component</span></span>    |                                       <span data-ttu-id="89875-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="89875-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="89875-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="89875-111">Symbolic Name</span></span>  |                                 <span data-ttu-id="89875-112">Err_InvalidComparision</span><span class="sxs-lookup"><span data-stu-id="89875-112">Err_InvalidComparision</span></span>                                 |
|  <span data-ttu-id="89875-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="89875-113">Message Text</span></span>   |                <span data-ttu-id="89875-114">比較只能 Equals、 NotEquals 和 Exists。</span><span class="sxs-lookup"><span data-stu-id="89875-114">The Comparison can only be Equals, NotEquals and Exists.</span></span>                |
  
## <a name="explanation"></a><span data-ttu-id="89875-115">說明</span><span class="sxs-lookup"><span data-stu-id="89875-115">Explanation</span></span>  
 <span data-ttu-id="89875-116">這個錯誤/警告/資訊事件表示 BizTalk Server 無法嘗試決定要批次處理的訊息比較的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="89875-116">This Error/Warning/Information event indicates BizTalk Server was unable to compare a context property while trying to decide to Batch a message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="89875-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="89875-117">User Action</span></span>  
 <span data-ttu-id="89875-118">若要解決這個錯誤，請確定在作用中批次中提供的篩選條件不指定 Equals、 NotEquals 和 Exists 以外的操作員。 不支援其他作業的 XSD 型別。</span><span class="sxs-lookup"><span data-stu-id="89875-118">To resolve this error, ensure that the filter provided in Active batches doesn’t specify an operator  other than Equals, NotEquals and Exists for XSD types that don’t support other operations.</span></span>