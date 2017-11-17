---
title: "範例訊息簡報 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, SWIFT message block
- SWIFT messages, message block example
ms.assetid: 3136a7da-658d-4100-bbe5-2186ee8bafd1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a14fe8cf93d0c657f2cebbdca3b2f9058f909982
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sample-message-presentation"></a><span data-ttu-id="a8f31-102">範例訊息簡報</span><span class="sxs-lookup"><span data-stu-id="a8f31-102">Sample Message Presentation</span></span>
<span data-ttu-id="a8f31-103">下表顯示的 SWIFT 訊息區塊配置的範例。</span><span class="sxs-lookup"><span data-stu-id="a8f31-103">The following table shows an example of the block layout of a SWIFT message.</span></span>  
  
|<span data-ttu-id="a8f31-104">區塊</span><span class="sxs-lookup"><span data-stu-id="a8f31-104">Block</span></span>|<span data-ttu-id="a8f31-105">範例</span><span class="sxs-lookup"><span data-stu-id="a8f31-105">Example</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="a8f31-106">**區塊 1**基本的標頭</span><span class="sxs-lookup"><span data-stu-id="a8f31-106">**Block 1** Basic Header</span></span>|<span data-ttu-id="a8f31-107">{1:F01BCITITMMAXXX0012000123}</span><span class="sxs-lookup"><span data-stu-id="a8f31-107">{1:F01BCITITMMAXXX0012000123}</span></span>|  
|<span data-ttu-id="a8f31-108">**封鎖 2** (I) 應用程式標頭的輸入 （SWIFT)</span><span class="sxs-lookup"><span data-stu-id="a8f31-108">**Block 2** (I) Application Header Input (to SWIFT)</span></span><br /><br /> <span data-ttu-id="a8f31-109">或</span><span class="sxs-lookup"><span data-stu-id="a8f31-109">Or</span></span><br /><br /> <span data-ttu-id="a8f31-110">**封鎖 2** (O) 應用程式標頭輸出 （來自 SWIFT)</span><span class="sxs-lookup"><span data-stu-id="a8f31-110">**Block 2** (O) Application Header Output (from SWIFT)</span></span>|<span data-ttu-id="a8f31-111">{2:I103VBOEATWWXXXXN}或者 {2:O1030840010605BNPAFRPPAXXX00120078960106051051U3</span><span class="sxs-lookup"><span data-stu-id="a8f31-111">{2:I103VBOEATWWXXXXN} Or {2:O1030840010605BNPAFRPPAXXX00120078960106051051U3</span></span>|  
|<span data-ttu-id="a8f31-112">**區塊 3**使用者標頭</span><span class="sxs-lookup"><span data-stu-id="a8f31-112">**Block 3** User Header</span></span>|<span data-ttu-id="a8f31-113">{3: {108:BCITITMMA950906}}</span><span class="sxs-lookup"><span data-stu-id="a8f31-113">{3:{108:BCITITMMA950906}}</span></span>|  
|<span data-ttu-id="a8f31-114">**封鎖 4**文字</span><span class="sxs-lookup"><span data-stu-id="a8f31-114">**Block 4** Text</span></span>|<span data-ttu-id="a8f31-115">{4:\<CRLF >: 20:1234567890\<CRLF >: 23B:CRED\<CRLF >: 32A:010605GBP45000，\<CRLF >: 33B:GBP45000，\<CRLF >: 50K:MASTERS 匯入\<CRLF > RUE DES ARBRES119\<CRLF > CAMBRAI\<CRLF >: 52A:BNPAFRPPCAM\<CRLF >: 53A:POCIITMM680\<CRLF >: 57A:BCITITMM680\<CRLF >: 59: / P03452032022819 30\<CRLF > 總計匯入\<CRLF > PESCARA\<CRLF >: 70: RFB/INV 5591\<CRLF >: 71A:SHA\<CRLF >-}</span><span class="sxs-lookup"><span data-stu-id="a8f31-115">{4:\<CRLF> :20:1234567890\<CRLF> :23B:CRED\<CRLF> :32A:010605GBP45000,\<CRLF> :33B:GBP45000,\<CRLF> :50K:MASTERS IMPORT\<CRLF> RUE DES ARBRES 119\<CRLF> CAMBRAI\<CRLF> :52A:BNPAFRPPCAM\<CRLF> :53A:POCIITMM680\<CRLF> :57A:BCITITMM680\<CRLF> :59:/P03452032022819 30\<CRLF> GRAND IMPORT\<CRLF> PESCARA\<CRLF> :70:/RFB/INV 5591\<CRLF> :71A:SHA\<CRLF> -}</span></span>|  
|<span data-ttu-id="a8f31-116">**封鎖 5**結尾</span><span class="sxs-lookup"><span data-stu-id="a8f31-116">**Block 5** Trailers</span></span>|<span data-ttu-id="a8f31-117">{5: {MAC: 12345678} {CHK:123456789ABC}}</span><span class="sxs-lookup"><span data-stu-id="a8f31-117">{5:{MAC:12345678}{CHK:123456789ABC}}</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a8f31-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8f31-118">See Also</span></span>  
 [<span data-ttu-id="a8f31-119">SWIFT 的結構描述</span><span class="sxs-lookup"><span data-stu-id="a8f31-119">SWIFT Schemas</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-schemas.md)