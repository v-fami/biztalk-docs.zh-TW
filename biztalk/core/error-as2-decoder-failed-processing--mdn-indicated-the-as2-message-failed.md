---
title: AS2 解碼器處理失敗，因為 MDN 表示 AS2 訊息處理失敗 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bce620a-f336-435e-b7c3-3db060f2819d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20454f1c551b6b4828c42e09f0442b83275256ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240118"
---
# <a name="the-as2-decoder-failed-processing-because-the-mdn-indicated-the-as2-message-failed-processing"></a><span data-ttu-id="d7980-102">AS2 解碼器處理失敗，因為 MDN 表示 AS2 訊息處理失敗</span><span class="sxs-lookup"><span data-stu-id="d7980-102">The AS2 Decoder failed processing because the MDN indicated the AS2 message failed processing</span></span>
## <a name="details"></a><span data-ttu-id="d7980-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d7980-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d7980-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d7980-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d7980-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d7980-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="d7980-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d7980-106">Event ID</span></span>|-|  
|<span data-ttu-id="d7980-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="d7980-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d7980-108">EDI</span><span class="sxs-lookup"><span data-stu-id="d7980-108"> EDI</span></span>|  
|<span data-ttu-id="d7980-109">元件</span><span class="sxs-lookup"><span data-stu-id="d7980-109">Component</span></span>|<span data-ttu-id="d7980-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="d7980-110">AS2 Engine</span></span>|  
|<span data-ttu-id="d7980-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d7980-111">Symbolic Name</span></span>|<span data-ttu-id="d7980-112">AS2DecoderMdnProcessingFailureReturned</span><span class="sxs-lookup"><span data-stu-id="d7980-112">AS2DecoderMdnProcessingFailureReturned</span></span>|  
|<span data-ttu-id="d7980-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d7980-113">Message Text</span></span>|<span data-ttu-id="d7980-114">AS2 解碼器處理失敗，因為 MDN 表示 AS2 訊息處理失敗。</span><span class="sxs-lookup"><span data-stu-id="d7980-114">The AS2 Decoder failure processing because the MDN indicated the AS2 message failed processing.</span></span>  <span data-ttu-id="d7980-115">MDN 訊息的詳細資料如下： AS2-從:"{0}"AS2-到:"\ {1 \}"MessageID:"\ {2 \}"OriginalMessageID:"\ {3\}"</span><span class="sxs-lookup"><span data-stu-id="d7980-115">Details of the MDN message are as follows:  AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}" OriginalMessageID:"{3}"</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d7980-116">說明</span><span class="sxs-lookup"><span data-stu-id="d7980-116">Explanation</span></span>  
 <span data-ttu-id="d7980-117">這個錯誤/警告/資訊事件表示，MDN 回應指出，原始 AS2 訊息的接收者無法處理原始 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="d7980-117">This Error/Warning/Information event indicates that the MDN response shows that the receiver of the original AS2 message could not process the original AS2 message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d7980-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d7980-118">User Action</span></span>  
 <span data-ttu-id="d7980-119">若要解決這個錯誤，請連絡 AS2 訊息的接收者，判斷接收者無法處理的原因，接著在修正原始 AS2 訊息後重新傳送。</span><span class="sxs-lookup"><span data-stu-id="d7980-119">To resolve this error, contact the receiver of the AS2 message, determine why processing failed at the receiver, fix the original AS2 message, and then resend.</span></span>