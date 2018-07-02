---
title: 從後端應用程式的 FRR 接收位置的訊息 |Microsoft Docs
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
ms.openlocfilehash: 9133a4499e655003ec2cc3d2e0d654e5a225f58b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981527"
---
# <a name="frr-receive-location-for-messages-from-the-back-end-application"></a><span data-ttu-id="48ec6-102">從後端應用程式的 FRR 接收位置的訊息</span><span class="sxs-lookup"><span data-stu-id="48ec6-102">FRR Receive Location for Messages from the Back-End Application</span></span>
<span data-ttu-id="48ec6-103">若要啟用 FIN 回應對帳 (FRR)，您必須設定 FRR 接收位置，接收來自後端應用程式和路由傳送到 BizTalk MessageBox 取用 FRR 協調流程。</span><span class="sxs-lookup"><span data-stu-id="48ec6-103">To enable FIN response reconciliation (FRR), you must set up an FRR receive location that receives messages from the back-end application and routes them to the BizTalk MessageBox for consumption by the FRR orchestration.</span></span> <span data-ttu-id="48ec6-104">接收位置路由傳送訊息，以透過自訂的 FRR 接收管線，您必須建立下列管線元件：</span><span class="sxs-lookup"><span data-stu-id="48ec6-104">The receive location routes a message through a custom FRR receive pipeline that you must create with the following pipeline components:</span></span>  
  
- <span data-ttu-id="48ec6-105">SWIFT 解譯器的解譯階段</span><span class="sxs-lookup"><span data-stu-id="48ec6-105">The SWIFT disassembler in the Disassemble stage</span></span>  
  
- <span data-ttu-id="48ec6-106">SWIFT 的 FRR 解碼器管線元件中的解碼器階段</span><span class="sxs-lookup"><span data-stu-id="48ec6-106">The SWIFT FRR Decoder pipeline component in the Decoder stage</span></span>  
  
- <span data-ttu-id="48ec6-107">SWIFT 的 FRR CorrelationSet 解析管線元件中的合作對象解析 」 階段</span><span class="sxs-lookup"><span data-stu-id="48ec6-107">The SWIFT FRR CorrelationSet Resolver pipeline component in the Party Resolution stage</span></span>  
  
  <span data-ttu-id="48ec6-108">接收埠處理之訊息的[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed = = False 和[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SWIFTBOUND = = True。</span><span class="sxs-lookup"><span data-stu-id="48ec6-108">The receive port handles messages that have [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed==False and [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SWIFTBOUND==True.</span></span> <span data-ttu-id="48ec6-109">傳輸機制是後端應用程式所規定的任何內容。</span><span class="sxs-lookup"><span data-stu-id="48ec6-109">The transport mechanism is whatever the back-end application dictates.</span></span>  
  
  <span data-ttu-id="48ec6-110">此接收埠會使用相同的自訂接收管線會使用接收位置所來自 SWIFT 的訊息。</span><span class="sxs-lookup"><span data-stu-id="48ec6-110">This receive port uses the same custom receive pipeline that is used by the receive location for messages from SWIFT.</span></span> <span data-ttu-id="48ec6-111">不過，管線會執行不同的函式的兩個接收位置。</span><span class="sxs-lookup"><span data-stu-id="48ec6-111">However, the pipeline performs different functions for the two receive locations.</span></span> <span data-ttu-id="48ec6-112">在 接收位置從後端應用程式的訊息，SWIFT 的 FRR CorrelationSet 解析管線元件會初始化的相互關聯 token。</span><span class="sxs-lookup"><span data-stu-id="48ec6-112">In the receive location for messages from the back-end application, the SWIFT FRR CorrelationSet Resolver pipeline component initializes the correlation token.</span></span>