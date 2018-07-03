---
title: 訊息的自訂處理常式的 FRR 傳送埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FRR, send ports
- custom handlers
- FRR, custom handlers
- send ports, FRR
- send ports, custom handlers
ms.assetid: 486d7410-fde1-4a9b-a9c2-64c1ed85ebc0
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df8ba2b085268f2c0c272b81b27768db716b63c0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996151"
---
# <a name="frr-send-ports-for-messages-to-the-custom-handlers"></a><span data-ttu-id="02e67-102">訊息的自訂處理常式的 FRR 傳送埠</span><span class="sxs-lookup"><span data-stu-id="02e67-102">FRR Send Ports for Messages to the Custom Handlers</span></span>
<span data-ttu-id="02e67-103">若要啟用 FRR 自訂處理常式，您必須建立一系列的 FRR 傳送埠，其中每個將特定類型的原始訊息複本路由傳送至自訂處理常式。</span><span class="sxs-lookup"><span data-stu-id="02e67-103">To enable custom handlers for FRR, you must create a series of FRR send ports, each one of which routes a copy of an original message of a certain type to the custom handlers.</span></span> <span data-ttu-id="02e67-104">這些傳送連接埠必須具有下列管線元件：</span><span class="sxs-lookup"><span data-stu-id="02e67-104">These send ports must have the following pipeline components:</span></span>  

- <span data-ttu-id="02e67-105">中 「 組合 」 階段的 SWIFT 組合器</span><span class="sxs-lookup"><span data-stu-id="02e67-105">The SWIFT assembler in the Assemble stage</span></span>  

- <span data-ttu-id="02e67-106">SWIFTSendFrrComponent 管線元件中的編碼階段</span><span class="sxs-lookup"><span data-stu-id="02e67-106">The SWIFTSendFrrComponent pipeline component in the Encode stage</span></span>  

  <span data-ttu-id="02e67-107">未成功傳送的分類 0 到 9 SWIFT FIN 訊息以外的所有訊息，傳送埠必須具有下列的篩選器：</span><span class="sxs-lookup"><span data-stu-id="02e67-107">For all messages except Category 0 to 9 SWIFT FIN messages that are not successfully sent, the send port must have the following filters:</span></span>  

- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="02e67-108">_SendingServiceType = = [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService</span><span class="sxs-lookup"><span data-stu-id="02e67-108">_SendingServiceType == [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService</span></span>  

- <span data-ttu-id="02e67-109">BTS。作業會設定每個訊息類型所需的值。</span><span class="sxs-lookup"><span data-stu-id="02e67-109">BTS.Operation set to the value required for each message type.</span></span> <span data-ttu-id="02e67-110">針對 BTS 的可能值。作業屬性，請參閱表格[傳送至自訂處理常式建立 FRR 傳送埠](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="02e67-110">For the possible values for the BTS.Operation property, see the table in [Creating the FRR Send Ports for Sending to the Custom Handlers](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md).</span></span>  

  <span data-ttu-id="02e67-111">為類別 0 到 9 SWIFT FIN 未成功傳送的訊息，傳送埠必須具有下列的篩選條件︰</span><span class="sxs-lookup"><span data-stu-id="02e67-111">For Category 0 to 9 SWIFT FIN messages that are not successfully sent, the send port must have the following filters:</span></span>  

- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="02e67-112">_SendingServiceTyp = =[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService</span><span class="sxs-lookup"><span data-stu-id="02e67-112">_SendingServiceTyp==[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService</span></span>  

- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="02e67-113">_FrrFailed = = true</span><span class="sxs-lookup"><span data-stu-id="02e67-113">_FrrFailed==True</span></span>  

- <span data-ttu-id="02e67-114">BTS。作業 = =[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSendMTMsg</span><span class="sxs-lookup"><span data-stu-id="02e67-114">BTS.Operation==[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSendMTMsg</span></span>  

- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="02e67-115">_FRRFailedReason 設為每個訊息類型所需的值。</span><span class="sxs-lookup"><span data-stu-id="02e67-115">_FRRFailedReason set to the value required for each message type.</span></span> <span data-ttu-id="02e67-116">針對 BTS 的可能值。作業屬性，請參閱表格[傳送至自訂處理常式建立 FRR 傳送埠](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="02e67-116">For the possible values for the BTS.Operation property, see the table in [Creating the FRR Send Ports for Sending to the Custom Handlers](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md).</span></span>
