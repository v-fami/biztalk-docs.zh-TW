---
title: 訊息類型不允許作為協議一部分 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 829f8230-33b8-4b5f-a56a-d0c1d3a17271
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1ed9c1e4891a3365484b60e51848a998f2d152b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982367"
---
# <a name="message-type-is-not-allowed-as-part-of-the-agreement"></a><span data-ttu-id="ec72d-102">訊息類型不允許作為協議的一部分</span><span class="sxs-lookup"><span data-stu-id="ec72d-102">Message Type is not allowed as part of the Agreement</span></span>
## <a name="details"></a><span data-ttu-id="ec72d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ec72d-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="ec72d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ec72d-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="ec72d-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="ec72d-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="ec72d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ec72d-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="ec72d-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="ec72d-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ec72d-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="ec72d-108"> EDI</span></span> |
|    <span data-ttu-id="ec72d-109">元件</span><span class="sxs-lookup"><span data-stu-id="ec72d-109">Component</span></span>    |                                       <span data-ttu-id="ec72d-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="ec72d-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="ec72d-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ec72d-111">Symbolic Name</span></span>  |                          <span data-ttu-id="ec72d-112">TransactionSetNotAllowedDescription</span><span class="sxs-lookup"><span data-stu-id="ec72d-112">TransactionSetNotAllowedDescription</span></span>                           |
|  <span data-ttu-id="ec72d-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ec72d-113">Message Text</span></span>   |               <span data-ttu-id="ec72d-114">訊息類型{0}不允許作為協議的一部分。</span><span class="sxs-lookup"><span data-stu-id="ec72d-114">Message Type {0} is not allowed as part of the Agreement.</span></span>                |
  
## <a name="explanation"></a><span data-ttu-id="ec72d-115">說明</span><span class="sxs-lookup"><span data-stu-id="ec72d-115">Explanation</span></span>  
 <span data-ttu-id="ec72d-116">這個錯誤/警告/資訊事件表示 BizTalk Server 無法處理文件，因為文件的訊息類型不允許作為協議的一部分。</span><span class="sxs-lookup"><span data-stu-id="ec72d-116">This Error/Warning/Information event indicates BizTalk Server was able to process the document because the message type of the document is not allowed as part of the agreement.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ec72d-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ec72d-117">User Action</span></span>  
 <span data-ttu-id="ec72d-118">若要解決這個錯誤，請查看的訊息類型，會允許和不允許作為協議的一部分。</span><span class="sxs-lookup"><span data-stu-id="ec72d-118">To resolve this error, please look at the message types that are allowed and not allowed as part of the agreement.</span></span>