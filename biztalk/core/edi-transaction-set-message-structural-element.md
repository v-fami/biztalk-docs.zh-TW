---
title: EDI 交易集訊息結構元素 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: caea8408-c09c-4525-a9c9-18abe4432594
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d49288e9a311c9766e61fe985b9e279a8660f4ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239182"
---
# <a name="edi-transaction-set-message-structural-element"></a><span data-ttu-id="c3d34-102">EDI 交易集訊息結構元素</span><span class="sxs-lookup"><span data-stu-id="c3d34-102">EDI Transaction Set-Message Structural Element</span></span>
<span data-ttu-id="c3d34-103">交易集 (X12 編碼) 或訊息 (EDIFACT 編碼) 包含組成訊息資料的區段。</span><span class="sxs-lookup"><span data-stu-id="c3d34-103">The transaction set (in X12 encoding) or message (in EDIFACT encoding) contains segments that make up the message data.</span></span> <span data-ttu-id="c3d34-104">交易集由標頭、資料區段集合和結尾組成。</span><span class="sxs-lookup"><span data-stu-id="c3d34-104">The transaction set consists of a header, a collection of data segments, and a trailer.</span></span> <span data-ttu-id="c3d34-105">交易處理時所需要的詳細資料都會包含在交易集中。</span><span class="sxs-lookup"><span data-stu-id="c3d34-105">All details that are required to process the transaction are available within the transaction set.</span></span>  
  
 <span data-ttu-id="c3d34-106">交易集的開頭必須是 ST 交易集標頭 (X12) 或 UNH 訊息標頭 (EDIFACT)。</span><span class="sxs-lookup"><span data-stu-id="c3d34-106">A transaction set must start with a ST Transaction Set Header (in X12) or a UNH Message Header (in EDIFACT).</span></span> <span data-ttu-id="c3d34-107">它的結尾必須是 SE 交易集結尾 (X12) 或 UNT 訊息結尾 (EDIFACT)。</span><span class="sxs-lookup"><span data-stu-id="c3d34-107">It must end with a SE Transaction Set Trailer (in X12) or a UNT Message Trailer (in EDIFACT).</span></span> <span data-ttu-id="c3d34-108">結尾會提供資料區段計數，這些區段包括標頭和結尾區段。</span><span class="sxs-lookup"><span data-stu-id="c3d34-108">The trailer provides a count of the data segments that includes the header and trailer segments.</span></span>  
  
 <span data-ttu-id="c3d34-109">交易集可以包含一或多個迴圈，以便在需要重複相關區段的集合時使用。</span><span class="sxs-lookup"><span data-stu-id="c3d34-109">A transaction set can contain one or more loops, which are required to repeat a collection of related segments.</span></span>