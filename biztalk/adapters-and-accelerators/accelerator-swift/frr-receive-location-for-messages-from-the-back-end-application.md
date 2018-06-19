---
title: FRR 接收訊息的位置從後端應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FRR, receive locations
- receive locations, FRR
ms.assetid: da0ad616-800f-493f-822f-eca1224722ab
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41d50f83feceac0238742cd474f70ecc1449f906
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22207534"
---
# <a name="frr-receive-location-for-messages-from-the-back-end-application"></a><span data-ttu-id="cc90c-102">FRR 接收訊息的位置從後端應用程式</span><span class="sxs-lookup"><span data-stu-id="cc90c-102">FRR Receive Location for Messages from the Back-End Application</span></span>
<span data-ttu-id="cc90c-103">若要啟用 FIN 回應對帳 (FRR)，您必須設定 FRR 接收位置從後端應用程式接收訊息並路由傳送到 BizTalk MessageBox 取用 FRR 協調流程。</span><span class="sxs-lookup"><span data-stu-id="cc90c-103">To enable FIN response reconciliation (FRR), you must set up an FRR receive location that receives messages from the back-end application and routes them to the BizTalk MessageBox for consumption by the FRR orchestration.</span></span> <span data-ttu-id="cc90c-104">接收位置會透過使用下列管線元件，您必須建立自訂 FRR 接收管線的訊息路由傳送：</span><span class="sxs-lookup"><span data-stu-id="cc90c-104">The receive location routes a message through a custom FRR receive pipeline that you must create with the following pipeline components:</span></span>  
  
-   <span data-ttu-id="cc90c-105">「 解譯 」 階段中的 SWIFT 解譯器</span><span class="sxs-lookup"><span data-stu-id="cc90c-105">The SWIFT disassembler in the Disassemble stage</span></span>  
  
-   <span data-ttu-id="cc90c-106">SWIFT FRR 解碼器管線元件中的解碼器階段</span><span class="sxs-lookup"><span data-stu-id="cc90c-106">The SWIFT FRR Decoder pipeline component in the Decoder stage</span></span>  
  
-   <span data-ttu-id="cc90c-107">SWIFT FRR CorrelationSet 解決器管線元件中的合作對象解析階段</span><span class="sxs-lookup"><span data-stu-id="cc90c-107">The SWIFT FRR CorrelationSet Resolver pipeline component in the Party Resolution stage</span></span>  
  
 <span data-ttu-id="cc90c-108">接收埠處理的訊息[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed = = False 和[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SWIFTBOUND = = True。</span><span class="sxs-lookup"><span data-stu-id="cc90c-108">The receive port handles messages that have [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed==False and [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SWIFTBOUND==True.</span></span> <span data-ttu-id="cc90c-109">傳輸機制為後端應用程式所規定的任何內容。</span><span class="sxs-lookup"><span data-stu-id="cc90c-109">The transport mechanism is whatever the back-end application dictates.</span></span>  
  
 <span data-ttu-id="cc90c-110">此接收埠會接收位置相同的自訂接收管線，可使用來自 SWIFT 的訊息。</span><span class="sxs-lookup"><span data-stu-id="cc90c-110">This receive port uses the same custom receive pipeline that is used by the receive location for messages from SWIFT.</span></span> <span data-ttu-id="cc90c-111">不過，管線會執行不同的函式的兩個接收位置。</span><span class="sxs-lookup"><span data-stu-id="cc90c-111">However, the pipeline performs different functions for the two receive locations.</span></span> <span data-ttu-id="cc90c-112">在接收位置從後端應用程式的訊息，SWIFT FRR CorrelationSet 解決器管線元件會初始化相互關聯 token。</span><span class="sxs-lookup"><span data-stu-id="cc90c-112">In the receive location for messages from the back-end application, the SWIFT FRR CorrelationSet Resolver pipeline component initializes the correlation token.</span></span>