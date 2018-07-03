---
title: X12 交換 Xml 序列化失敗，因為無效的結構。 尋找 TransactionSet 或 GE，但是找不到 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d058fdbb-6be5-499f-86f7-0eb8a85c5fb2
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05608a6e38d90a9e18004fa650ee6d5f7911109c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977551"
---
# <a name="x12-interchange-xml-serialization-failed-due-to-invalid-structure-looking-for-transactionset-or-ge-but-not-found"></a><span data-ttu-id="6c5c9-103">X12 交換 Xml 序列化失敗，因為無效的結構。</span><span class="sxs-lookup"><span data-stu-id="6c5c9-103">X12 interchange Xml serialization failed due to invalid structure.</span></span> <span data-ttu-id="6c5c9-104">尋找 TransactionSet 或 GE，但是找不到</span><span class="sxs-lookup"><span data-stu-id="6c5c9-104">Looking for TransactionSet or GE, but not found</span></span>
## <a name="details"></a><span data-ttu-id="6c5c9-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6c5c9-105">Details</span></span>  
  
|                 |                                                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="6c5c9-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="6c5c9-106">Product Name</span></span>   |                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                 |
| <span data-ttu-id="6c5c9-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="6c5c9-107">Product Version</span></span> |                             [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                             |
|    <span data-ttu-id="6c5c9-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="6c5c9-108">Event ID</span></span>     |                                                         -                                                          |
|  <span data-ttu-id="6c5c9-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="6c5c9-109">Event Source</span></span>   |               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="6c5c9-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="6c5c9-110"> EDI</span></span>               |
|    <span data-ttu-id="6c5c9-111">元件</span><span class="sxs-lookup"><span data-stu-id="6c5c9-111">Component</span></span>    |                                                     <span data-ttu-id="6c5c9-112">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="6c5c9-112">EDI Engine</span></span>                                                     |
|  <span data-ttu-id="6c5c9-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="6c5c9-113">Symbolic Name</span></span>  |                                           <span data-ttu-id="6c5c9-114">X12TransactionSetOrGeNotFound</span><span class="sxs-lookup"><span data-stu-id="6c5c9-114">X12TransactionSetOrGeNotFound</span></span>                                            |
|  <span data-ttu-id="6c5c9-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="6c5c9-115">Message Text</span></span>   | <span data-ttu-id="6c5c9-116">X12 交換 Xml 序列化失敗，因為無效的結構。</span><span class="sxs-lookup"><span data-stu-id="6c5c9-116">X12 interchange Xml serialization failed due to invalid structure.</span></span> <span data-ttu-id="6c5c9-117">尋找 TransactionSet 或 GE，但是找不到</span><span class="sxs-lookup"><span data-stu-id="6c5c9-117">Looking for TransactionSet or GE, but not found</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="6c5c9-118">說明</span><span class="sxs-lookup"><span data-stu-id="6c5c9-118">Explanation</span></span>  
 <span data-ttu-id="6c5c9-119">這個錯誤/警告/資訊事件表示，傳送管線無法序列化到外寄交換的交換結構無效，因此。</span><span class="sxs-lookup"><span data-stu-id="6c5c9-119">This Error/Warning/Information event indicates that the send pipeline could not serialize the outgoing interchange because the structure of the interchange was invalid.</span></span> <span data-ttu-id="6c5c9-120">原因可能是必要的標頭或結尾不存在或無效。</span><span class="sxs-lookup"><span data-stu-id="6c5c9-120">The reason could be that the required headers or trailers are not present or are invalid.</span></span> <span data-ttu-id="6c5c9-121">如果設定群組中的交易之後沒有接著另一個交易集或群組的結尾，它可能會發生。</span><span class="sxs-lookup"><span data-stu-id="6c5c9-121">It could occur if a transaction set in a group is not followed by another transaction set or the group trailer.</span></span> <span data-ttu-id="6c5c9-122">如果結構完整性檢查失敗時，它也可能發生。</span><span class="sxs-lookup"><span data-stu-id="6c5c9-122">It could also occur if structural integrity checks failed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6c5c9-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="6c5c9-123">User Action</span></span>  
 <span data-ttu-id="6c5c9-124">若要解決這個錯誤，請確認交換，以確保群組或交易集標頭和結尾都有效，然後再重新傳送交換的結構。</span><span class="sxs-lookup"><span data-stu-id="6c5c9-124">To resolve this error, verify the structure of the interchange, ensuring that the group or transaction set headers and trailers are valid, and then resend the interchange.</span></span>