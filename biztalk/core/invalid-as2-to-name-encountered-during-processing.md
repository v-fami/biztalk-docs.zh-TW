---
title: 無效的 AS2-處理過程中發現名稱 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 84d848b5-b2a3-460d-85d4-c3576e4e3aaf
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32ba8039d57bdc88f2aeed8e2654c5dc738f3d69
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002671"
---
# <a name="invalid-as2-to-name-encountered-during-processing"></a><span data-ttu-id="f23f3-102">無效的 AS2-在處理期間發生的名稱</span><span class="sxs-lookup"><span data-stu-id="f23f3-102">Invalid AS2-To name encountered during processing</span></span>
## <a name="details"></a><span data-ttu-id="f23f3-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f23f3-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="f23f3-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f23f3-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="f23f3-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="f23f3-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="f23f3-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f23f3-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="f23f3-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="f23f3-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f23f3-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="f23f3-108"> EDI</span></span> |
|    <span data-ttu-id="f23f3-109">元件</span><span class="sxs-lookup"><span data-stu-id="f23f3-109">Component</span></span>    |                                       <span data-ttu-id="f23f3-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="f23f3-110">AS2 Engine</span></span>                                       |
|  <span data-ttu-id="f23f3-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f23f3-111">Symbolic Name</span></span>  |                            <span data-ttu-id="f23f3-112">InvalidAS2ToNameEncounteredError</span><span class="sxs-lookup"><span data-stu-id="f23f3-112">InvalidAS2ToNameEncounteredError</span></span>                            |
|  <span data-ttu-id="f23f3-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f23f3-113">Message Text</span></span>   |             <span data-ttu-id="f23f3-114">無效的 AS2-在處理期間發生的名稱。</span><span class="sxs-lookup"><span data-stu-id="f23f3-114">Invalid AS2-To name encountered during processing.</span></span>  <span data-ttu-id="f23f3-115">值： {0}</span><span class="sxs-lookup"><span data-stu-id="f23f3-115">Value: {0}</span></span>             |
  
## <a name="explanation"></a><span data-ttu-id="f23f3-116">說明</span><span class="sxs-lookup"><span data-stu-id="f23f3-116">Explanation</span></span>  
 <span data-ttu-id="f23f3-117">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換或傳送管線無法處理外寄交換，因為值的 AS2-To 標頭不符合AS2 RFC 4130 中的規格。</span><span class="sxs-lookup"><span data-stu-id="f23f3-117">This Error/Warning/Information event indicates that either the receive pipeline could not process the incoming interchange or the send pipeline could not process the outgoing interchange because the value of the AS2-To header did not conform to the specifications in AS2 RFC 4130.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f23f3-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f23f3-118">User Action</span></span>  
 <span data-ttu-id="f23f3-119">若要解決這個錯誤，請確定 AS2-To 標頭中傳入或傳出的訊息符合 AS2 RFC 4130 第 6.2 節的規格。</span><span class="sxs-lookup"><span data-stu-id="f23f3-119">To resolve this error, make sure that the AS2-To header in the incoming or outgoing message conforms to the specifications in section 6.2 of AS2 RFC 4130.</span></span>