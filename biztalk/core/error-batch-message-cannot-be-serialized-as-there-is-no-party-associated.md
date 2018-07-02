---
title: 無法序列化批次訊息，因為沒有任何相關聯的合作對象傳送埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d697ff9c-a6d1-4a3c-9ec3-4cd496f7eec2
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84915c3544ed6e4222dd7fb035808617b51e5280
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969559"
---
# <a name="batch-message-cannot-be-serialized-as-there-is-no-party-associated-with-send-port"></a><span data-ttu-id="0f879-102">無法序列化批次訊息，因為沒有合作對象與傳送埠相關聯</span><span class="sxs-lookup"><span data-stu-id="0f879-102">Batch message cannot be serialized as there is no party associated with send port</span></span>
## <a name="details"></a><span data-ttu-id="0f879-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0f879-103">Details</span></span>  
  
|                 |                                                                                                                                            |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="0f879-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0f879-104">Product Name</span></span>   |                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                             |
| <span data-ttu-id="0f879-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="0f879-105">Product Version</span></span> |                                         [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                         |
|    <span data-ttu-id="0f879-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0f879-106">Event ID</span></span>     |                                                                     -                                                                      |
|  <span data-ttu-id="0f879-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="0f879-107">Event Source</span></span>   |                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0f879-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="0f879-108"> EDI</span></span>                           |
|    <span data-ttu-id="0f879-109">元件</span><span class="sxs-lookup"><span data-stu-id="0f879-109">Component</span></span>    |                                                              <span data-ttu-id="0f879-110">批次引擎</span><span class="sxs-lookup"><span data-stu-id="0f879-110">Batching Engine</span></span>                                                               |
|  <span data-ttu-id="0f879-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0f879-111">Symbolic Name</span></span>  |                                             <span data-ttu-id="0f879-112">BatchMessageSerializationFailureDueToMissingParty</span><span class="sxs-lookup"><span data-stu-id="0f879-112">BatchMessageSerializationFailureDueToMissingParty</span></span>                                              |
|  <span data-ttu-id="0f879-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0f879-113">Message Text</span></span>   | <span data-ttu-id="0f879-114">批次訊息無法序列化，因為沒有任何相關聯的合作對象傳送埠{0}。</span><span class="sxs-lookup"><span data-stu-id="0f879-114">Batch message can not be serialized as there is no party associated with send port {0}.</span></span> <span data-ttu-id="0f879-115">請確定合作對象相關聯的連接埠</span><span class="sxs-lookup"><span data-stu-id="0f879-115">Make sure that a party is associated with the port</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="0f879-116">說明</span><span class="sxs-lookup"><span data-stu-id="0f879-116">Explanation</span></span>  
 <span data-ttu-id="0f879-117">這個錯誤/警告/資訊事件表示，傳送管線無法處理保留的交換因為無法判斷訊息應傳送至合作對象。</span><span class="sxs-lookup"><span data-stu-id="0f879-117">This Error/Warning/Information event indicates that the send pipeline could not process a preserved interchange because it could not determine the party that the message should be sent to.</span></span> <span data-ttu-id="0f879-118">因為未設定 DestinationPartyName 內容屬性，它無法判斷合作對象。</span><span class="sxs-lookup"><span data-stu-id="0f879-118">It could not determine the party because the DestinationPartyName context property was not set.</span></span> <span data-ttu-id="0f879-119">如此一來，傳送管線無法判斷信封設定。</span><span class="sxs-lookup"><span data-stu-id="0f879-119">As a result, the send pipeline could not determine the envelope settings.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0f879-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0f879-120">User Action</span></span>  
 <span data-ttu-id="0f879-121">若要解決這個錯誤，讓訊息通過傳送管線，並再決定 DestinationPartyName 內容屬性的訊息。</span><span class="sxs-lookup"><span data-stu-id="0f879-121">To resolve this error, pass the message through a passthrough send pipeline, and then determine the DestinationPartyName context property for the message.</span></span> <span data-ttu-id="0f879-122">驗證合作對象存在。</span><span class="sxs-lookup"><span data-stu-id="0f879-122">Verify that the party exists.</span></span> <span data-ttu-id="0f879-123">如果不是，建立合作對象，然後再重新傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="0f879-123">If not, create the party, and then resend the message.</span></span>