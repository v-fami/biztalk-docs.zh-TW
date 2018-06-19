---
title: 無法序列化批次訊息，因為沒有任何相關聯的合作對象傳送埠 |Microsoft 文件
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
ms.openlocfilehash: 5b20d10a2c7b584eccc7d1fb57e5132a4ac0d608
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241478"
---
# <a name="batch-message-cannot-be-serialized-as-there-is-no-party-associated-with-send-port"></a><span data-ttu-id="8d1e9-102">無法序列化批次訊息，因為沒有任何傳送埠相關聯的合作對象</span><span class="sxs-lookup"><span data-stu-id="8d1e9-102">Batch message cannot be serialized as there is no party associated with send port</span></span>
## <a name="details"></a><span data-ttu-id="8d1e9-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8d1e9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8d1e9-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8d1e9-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="8d1e9-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="8d1e9-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="8d1e9-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8d1e9-106">Event ID</span></span>|-|  
|<span data-ttu-id="8d1e9-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="8d1e9-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8d1e9-108">EDI</span><span class="sxs-lookup"><span data-stu-id="8d1e9-108"> EDI</span></span>|  
|<span data-ttu-id="8d1e9-109">元件</span><span class="sxs-lookup"><span data-stu-id="8d1e9-109">Component</span></span>|<span data-ttu-id="8d1e9-110">批次處理引擎</span><span class="sxs-lookup"><span data-stu-id="8d1e9-110">Batching Engine</span></span>|  
|<span data-ttu-id="8d1e9-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8d1e9-111">Symbolic Name</span></span>|<span data-ttu-id="8d1e9-112">BatchMessageSerializationFailureDueToMissingParty</span><span class="sxs-lookup"><span data-stu-id="8d1e9-112">BatchMessageSerializationFailureDueToMissingParty</span></span>|  
|<span data-ttu-id="8d1e9-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8d1e9-113">Message Text</span></span>|<span data-ttu-id="8d1e9-114">無法序列化批次訊息，因為沒有任何相關聯的合作對象傳送埠 {0}。</span><span class="sxs-lookup"><span data-stu-id="8d1e9-114">Batch message can not be serialized as there is no party associated with send port {0}.</span></span> <span data-ttu-id="8d1e9-115">請確定合作對象連接埠相關聯</span><span class="sxs-lookup"><span data-stu-id="8d1e9-115">Make sure that a party is associated with the port</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8d1e9-116">說明</span><span class="sxs-lookup"><span data-stu-id="8d1e9-116">Explanation</span></span>  
 <span data-ttu-id="8d1e9-117">這個錯誤/警告/資訊事件表示，傳送管線無法處理保留的交換因為無法判定應該要傳送訊息的合作對象。</span><span class="sxs-lookup"><span data-stu-id="8d1e9-117">This Error/Warning/Information event indicates that the send pipeline could not process a preserved interchange because it could not determine the party that the message should be sent to.</span></span> <span data-ttu-id="8d1e9-118">因為沒有設定 DestinationPartyName 內容屬性，它無法判斷合作對象。</span><span class="sxs-lookup"><span data-stu-id="8d1e9-118">It could not determine the party because the DestinationPartyName context property was not set.</span></span> <span data-ttu-id="8d1e9-119">如此一來，傳送管線無法判斷信封設定。</span><span class="sxs-lookup"><span data-stu-id="8d1e9-119">As a result, the send pipeline could not determine the envelope settings.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8d1e9-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8d1e9-120">User Action</span></span>  
 <span data-ttu-id="8d1e9-121">若要解決這個錯誤，讓訊息通過傳送管線，並接著判斷訊息的 DestinationPartyName 內容屬性。</span><span class="sxs-lookup"><span data-stu-id="8d1e9-121">To resolve this error, pass the message through a passthrough send pipeline, and then determine the DestinationPartyName context property for the message.</span></span> <span data-ttu-id="8d1e9-122">驗證合作對象存在。</span><span class="sxs-lookup"><span data-stu-id="8d1e9-122">Verify that the party exists.</span></span> <span data-ttu-id="8d1e9-123">如果沒有，請建立合作對象，，然後再重新傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="8d1e9-123">If not, create the party, and then resend the message.</span></span>