---
title: "FRR NAK 處理常式範例的運作方式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f11bd20-3a0e-4d96-8e0a-32fecc7eed7e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 009cb0c3dffce5f88c72207866f6778e3deb7b28
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-the-frr-nak-handler-sample-works"></a><span data-ttu-id="add06-102">FRR NAK 處理常式範例的運作方式</span><span class="sxs-lookup"><span data-stu-id="add06-102">How the FRR NAK Handler Sample Works</span></span>
<span data-ttu-id="add06-103">範例 FRR NAK 自訂處理常式做為 FIN 回應對帳 (FRR) 協調流程與訊息修復協調流程之間的媒介。</span><span class="sxs-lookup"><span data-stu-id="add06-103">The sample FRR NAK custom handler serves as an intermediary between the FIN Response Reconciliation (FRR) orchestration and the message-repair orchestration.</span></span> <span data-ttu-id="add06-104">FRR 協調流程中指出的 SWIFT 網路嘗試接收訊息時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="add06-104">The FRR orchestration identifies the error that occurred when the SWIFT network attempted to receive the message.</span></span> <span data-ttu-id="add06-105">FRR 協調流程的輸出是一段訊息與錯誤物件。</span><span class="sxs-lookup"><span data-stu-id="add06-105">The output of the FRR orchestration is a one-part message with an error object.</span></span> <span data-ttu-id="add06-106">FRR NAK 自訂處理常式會將該訊息轉換成的兩個部分訊息，指出錯誤發生時，啟用要由訊息修復協調流程收取訊息的錯誤組件。</span><span class="sxs-lookup"><span data-stu-id="add06-106">The FRR NAK custom handler transforms that message into a two-part message, with an error part that indicates the error that occurred, enabling the message to be picked up by the message-repair orchestration.</span></span> <span data-ttu-id="add06-107">開啟 訊息修復協調流程中的訊息[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]可讓您找出錯誤的是，修復的訊息，因此，並重新送出的表單，讓[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]可以重新傳送至 SAA。</span><span class="sxs-lookup"><span data-stu-id="add06-107">The message-repair orchestration opens the message in an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form that enables you to find out what the error was, repair the message accordingly, and resubmit it so that [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] can resend it to SAA.</span></span>  
  
 <span data-ttu-id="add06-108">FRR NAK 自訂處理常式處理的 SWIFT 網路無法成功接收訊息時，就會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="add06-108">The following steps occur when the FRR NAK custom handler processes a message that the SWIFT network could not successfully receive:</span></span>  
  
1.  <span data-ttu-id="add06-109">FRR 協調流程有相互關聯的 MTS21_FIN_ACKNAK NAK 訊息失敗的訊息之後，RepairSWIFTRejectedMessage 協調流程 （自訂的處理常式） 會拾取原始訊息 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="add06-109">After the FRR orchestration has correlated the failed message to the MTS21_FIN_ACKNAK NAK message, the RepairSWIFTRejectedMessage orchestration (the custom handler) picks up the original message from the MessageBox.</span></span> <span data-ttu-id="add06-110">它沒有，因為它會篩選 A4SWIFT_FRRFailed = = True 和 A4SWIFT_SendingServiceType ="A4SWIFT_FrrService"。</span><span class="sxs-lookup"><span data-stu-id="add06-110">It does so because it filters on A4SWIFT_FRRFailed==True and A4SWIFT_SendingServiceType="A4SWIFT_FrrService".</span></span>  
  
2.  <span data-ttu-id="add06-111">自訂處理常式不會拾取 MTS21_FIN_ACKNAK NAK 相關訊息，FRR 原始訊息。</span><span class="sxs-lookup"><span data-stu-id="add06-111">The custom handler does not pick up the MTS21_FIN_ACKNAK NAK message that FRR correlated to the original message.</span></span> <span data-ttu-id="add06-112">相反地，它會建立錯誤集合物件、 填入 BRE 驗證錯誤，指出哪些 A4SWIFT_FRRFailedReason 屬性，然後將它加入至原始訊息。</span><span class="sxs-lookup"><span data-stu-id="add06-112">Instead, it creates an error collection object, populates it with a BRE validation error that indicates what the A4SWIFT_FRRFailedReason property was, and adds it to the original message.</span></span> <span data-ttu-id="add06-113">訊息修復協調流程可以處理這兩個部分則訊息。</span><span class="sxs-lookup"><span data-stu-id="add06-113">The message-repair orchestration can process this two-part message.</span></span>  
  
3.  <span data-ttu-id="add06-114">自訂處理常式會升級下列屬性會收取訊息修復協調流程的訊息： A4SWIFT_Failed = = True，A4SWIFT_SwiftBound = = True，而且 BTS。作業 ="A4SWIFT_DASMMarkedAsFailed"。</span><span class="sxs-lookup"><span data-stu-id="add06-114">The custom handler promotes the following properties to cause the message to be picked up by the message-repair orchestration: A4SWIFT_Failed==True, A4SWIFT_SwiftBound==True, and BTS.Operation="A4SWIFT_DASMMarkedAsFailed".</span></span> <span data-ttu-id="add06-115">它會設定為 2，組件屬性的數目，並設定適當的錯誤屬性。</span><span class="sxs-lookup"><span data-stu-id="add06-115">It sets the number of parts property to 2, and sets the appropriate error properties.</span></span>  
  
4.  <span data-ttu-id="add06-116">因為升級的屬性，而訊息修復協調流程才能收取訊息，而 RepairSWIFTRejectedMessage 協調流程會終止。</span><span class="sxs-lookup"><span data-stu-id="add06-116">As a result of the promoted properties, the message-repair orchestration picks up the message, and the RepairSWIFTRejectedMessage orchestration terminates.</span></span>