---
title: "AS2 解碼器發生例外狀況處理期間 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5f16d2e-e83c-4e2c-84be-41b5ed012dce
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2826a938a4f081b8c5895da809e9f16966e25834
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-as2-decoder-encountered-an-exception-during-processing"></a><span data-ttu-id="f8ae6-102">AS2 解碼器發生在處理期間的例外狀況</span><span class="sxs-lookup"><span data-stu-id="f8ae6-102">The AS2 Decoder encountered an exception during processing</span></span>
## <a name="details"></a><span data-ttu-id="f8ae6-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f8ae6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f8ae6-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f8ae6-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f8ae6-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="f8ae6-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="f8ae6-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f8ae6-106">Event ID</span></span>|-|  
|<span data-ttu-id="f8ae6-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="f8ae6-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f8ae6-108">EDI</span><span class="sxs-lookup"><span data-stu-id="f8ae6-108"> EDI</span></span>|  
|<span data-ttu-id="f8ae6-109">元件</span><span class="sxs-lookup"><span data-stu-id="f8ae6-109">Component</span></span>|<span data-ttu-id="f8ae6-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="f8ae6-110">AS2 Engine</span></span>|  
|<span data-ttu-id="f8ae6-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f8ae6-111">Symbolic Name</span></span>|<span data-ttu-id="f8ae6-112">AS2DecoderExceptionEncounteredDuringProcessing</span><span class="sxs-lookup"><span data-stu-id="f8ae6-112">AS2DecoderExceptionEncounteredDuringProcessing</span></span>|  
|<span data-ttu-id="f8ae6-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f8ae6-113">Message Text</span></span>|<span data-ttu-id="f8ae6-114">AS2 解碼器在處理過程中發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f8ae6-114">The AS2 Decoder encountered an exception during processing.</span></span>  <span data-ttu-id="f8ae6-115">訊息和例外狀況的詳細資料如下： AS2-從:"{0}"AS2-到:"\ {1 \}"MessageID:"\ {2 \}"MessageType:"{3} 」 例外狀況:"\ {4\}"</span><span class="sxs-lookup"><span data-stu-id="f8ae6-115">Details of the message and exception are as follows:  AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}" MessageType: "{3}" Exception:"{4}"</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f8ae6-116">說明</span><span class="sxs-lookup"><span data-stu-id="f8ae6-116">Explanation</span></span>  
 <span data-ttu-id="f8ae6-117">這個錯誤/警告/資訊事件表示，由於 AS2 解碼器發生問題，因此接收管線無法處理內送 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="f8ae6-117">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming AS2 message because of an issue with the AS2 Decoder.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f8ae6-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f8ae6-118">User Action</span></span>  
 <span data-ttu-id="f8ae6-119">若要解決這個錯誤，請檢查 AS2 錯誤程式碼以判斷錯誤條件的本質。</span><span class="sxs-lookup"><span data-stu-id="f8ae6-119">To resolve this error, determine the nature of the error condition by checking the AS2 error code.</span></span> <span data-ttu-id="f8ae6-120">如需有關 AS2 錯誤碼的詳細資訊，請參閱中的 < AS2 錯誤碼 > 主題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]說明檔。</span><span class="sxs-lookup"><span data-stu-id="f8ae6-120">For more information on AS2 error codes, see the "AS2 Error Codes" topic in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] help file.</span></span>