---
title: "訊息的自訂處理常式的 FRR 傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FRR, send ports
- custom handlers
- FRR, custom handlers
- send ports, FRR
- send ports, custom handlers
ms.assetid: 486d7410-fde1-4a9b-a9c2-64c1ed85ebc0
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6babc312ddad7d77a96e29bc9e59ec9298aa6ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="frr-send-ports-for-messages-to-the-custom-handlers"></a><span data-ttu-id="48240-102">訊息的自訂處理常式的 FRR 傳送埠</span><span class="sxs-lookup"><span data-stu-id="48240-102">FRR Send Ports for Messages to the Custom Handlers</span></span>
<span data-ttu-id="48240-103">若要啟用 FRR 自訂處理常式，您必須建立一系列 FRR 傳送埠，其中每個將特定類型的原始訊息複本路由傳送至的自訂處理常式。</span><span class="sxs-lookup"><span data-stu-id="48240-103">To enable custom handlers for FRR, you must create a series of FRR send ports, each one of which routes a copy of an original message of a certain type to the custom handlers.</span></span> <span data-ttu-id="48240-104">這兩個傳送埠都必須具有下列管線元件：</span><span class="sxs-lookup"><span data-stu-id="48240-104">These send ports must have the following pipeline components:</span></span>  
  
-   <span data-ttu-id="48240-105">「 組合 」 階段中的 SWIFT 組合器</span><span class="sxs-lookup"><span data-stu-id="48240-105">The SWIFT assembler in the Assemble stage</span></span>  
  
-   <span data-ttu-id="48240-106">SWIFTSendFrrComponent 管線元件中的編碼階段</span><span class="sxs-lookup"><span data-stu-id="48240-106">The SWIFTSendFrrComponent pipeline component in the Encode stage</span></span>  
  
 <span data-ttu-id="48240-107">對於未成功傳送的類別 0 到 9 SWIFT FIN 訊息以外的所有訊息，傳送埠必須包含下列的篩選器：</span><span class="sxs-lookup"><span data-stu-id="48240-107">For all messages except Category 0 to 9 SWIFT FIN messages that are not successfully sent, the send port must have the following filters:</span></span>  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="48240-108">_SendingServiceType = = [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService</span><span class="sxs-lookup"><span data-stu-id="48240-108">_SendingServiceType == [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService</span></span>  
  
-   <span data-ttu-id="48240-109">BTS。作業會設定每個訊息類型所需的值。</span><span class="sxs-lookup"><span data-stu-id="48240-109">BTS.Operation set to the value required for each message type.</span></span> <span data-ttu-id="48240-110">針對 BTS 的可能值。作業屬性，請參閱表格[FRR 傳送埠建立的自訂處理常式的傳送](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="48240-110">For the possible values for the BTS.Operation property, see the table in [Creating the FRR Send Ports for Sending to the Custom Handlers](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md).</span></span>  
  
 <span data-ttu-id="48240-111">對於類別 0 到 9 SWIFT FIN 未成功傳送的訊息，傳送埠必須具有下列的篩選器：</span><span class="sxs-lookup"><span data-stu-id="48240-111">For Category 0 to 9 SWIFT FIN messages that are not successfully sent, the send port must have the following filters:</span></span>  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="48240-112">_SendingServiceTyp = =[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService</span><span class="sxs-lookup"><span data-stu-id="48240-112">_SendingServiceTyp==[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService</span></span>  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="48240-113">_FrrFailed = = true</span><span class="sxs-lookup"><span data-stu-id="48240-113">_FrrFailed==True</span></span>  
  
-   <span data-ttu-id="48240-114">BTS。作業 = =[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSendMTMsg</span><span class="sxs-lookup"><span data-stu-id="48240-114">BTS.Operation==[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSendMTMsg</span></span>  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="48240-115">_FRRFailedReason 設為所需的每個訊息類型的值。</span><span class="sxs-lookup"><span data-stu-id="48240-115">_FRRFailedReason set to the value required for each message type.</span></span> <span data-ttu-id="48240-116">針對 BTS 的可能值。作業屬性，請參閱表格[FRR 傳送埠建立的自訂處理常式的傳送](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="48240-116">For the possible values for the BTS.Operation property, see the table in [Creating the FRR Send Ports for Sending to the Custom Handlers](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md).</span></span>