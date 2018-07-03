---
title: 驗證訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- validating, acknowledgements
- messages, acknowledgements
- acknowledgements, validating
- validating, messages
- acknowledgements, messages
- messages, validating
ms.assetid: 7dba0f40-5e19-4598-82cb-22c71e9536c6
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 35894722d2c95f197a1fe4072c2229cf96fea64f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010055"
---
# <a name="validating-messages"></a><span data-ttu-id="4a495-102">驗證訊息</span><span class="sxs-lookup"><span data-stu-id="4a495-102">Validating Messages</span></span>
<span data-ttu-id="4a495-103">Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 輸入訊息的傳送通知 (ACK)，從應用程式，或交易夥伴可能需要轉換到 HL7 HL7 XML 回條的形式支援編碼通知訊息。</span><span class="sxs-lookup"><span data-stu-id="4a495-103">Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) supports sending acknowledgments (ACK) for inbound messages from an application or trading partner in the form of an HL7 XML receipt that might need conversion to an HL7 encoded ACK message.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="4a495-104"> 通常會產生一個回條之後它會檢查傳入的訊息和相關輸入 （交易夥伴格式） 文件規格。</span><span class="sxs-lookup"><span data-stu-id="4a495-104"> typically generates a receipt after it checks the inbound message against the relevant inbound (trading-partner format) document specification.</span></span> <span data-ttu-id="4a495-105">當所有區段都通過驗證，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]傳回回條，表示應用程式的接受度。</span><span class="sxs-lookup"><span data-stu-id="4a495-105">When all the segments pass validation, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] returns a receipt that indicates acceptance to the application.</span></span> <span data-ttu-id="4a495-106">否則，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會產生表示錯誤或失敗/拒絕的回條。</span><span class="sxs-lookup"><span data-stu-id="4a495-106">Otherwise, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] generates a receipt indicating error or failure/reject.</span></span>  
  
 <span data-ttu-id="4a495-107">[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]通知傳輸報告對 HL7 標準的語法和圖解錯誤。</span><span class="sxs-lookup"><span data-stu-id="4a495-107">The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] ACK transmission reports syntactical and schematic errors against the HL7 standard.</span></span> <span data-ttu-id="4a495-108">如果驗證失敗，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]置於擱置的訊息佇列中的文件，並傳回詳細說明拒絕的回條。</span><span class="sxs-lookup"><span data-stu-id="4a495-108">If the validation fails, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] places the document in the suspended message queue and returns a receipt detailing the rejection.</span></span> <span data-ttu-id="4a495-109">[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]剖析器會執行牽涉到檢查資料型別、 語法和結構描述驗證的驗證。</span><span class="sxs-lookup"><span data-stu-id="4a495-109">The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] parser performs validation that involves checking data types, syntax, and the schema validation.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="4a495-110"> 在接收位置的詳細資料以及剖析記錄發生的任何圖解錯誤。</span><span class="sxs-lookup"><span data-stu-id="4a495-110"> records any schematic errors that occur in parsing in the receipt along with the location details.</span></span>  
  
 <span data-ttu-id="4a495-111">在設定階段中，您需要建立[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]通知以回應所需的成品</span><span class="sxs-lookup"><span data-stu-id="4a495-111">At configure time, you need to create the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] artifacts required for responding with an ACK.</span></span> <span data-ttu-id="4a495-112">[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]剖析器會建立標準 HL7 通知 XML 執行個體。</span><span class="sxs-lookup"><span data-stu-id="4a495-112">The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] parser creates the HL7 canonical ACK XML instance.</span></span> <span data-ttu-id="4a495-113">BizTalk 會將此轉換成適當的 BizTalk 對應中的所需的版本格式，並驗證目的格式。</span><span class="sxs-lookup"><span data-stu-id="4a495-113">BizTalk converts this to the required version format in an appropriate BizTalk map and validates the destination format.</span></span> <span data-ttu-id="4a495-114">[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]序列化程式則會將訊息轉換成 HL7 編碼的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4a495-114">The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] serializer then converts the message into an HL7-encoded instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a495-115">如果傳入訊息的分隔符號之間沒有衝突，而且中所指定[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態，然後[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會產生通知訊息會使用相同的分隔符號的輸入訊息，並覆寫組態設定。</span><span class="sxs-lookup"><span data-stu-id="4a495-115">If there is a conflict between the delimiters of an inbound message and those specified in the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] configuration, then [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] will generate an ACK message that uses the same delimiters of the inbound message and overrides the configuration settings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a495-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a495-116">See Also</span></span>  
 <span data-ttu-id="4a495-117">[建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span><span class="sxs-lookup"><span data-stu-id="4a495-117">[Creating and Processing Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span></span>  
 <span data-ttu-id="4a495-118">[程式設計手冊](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md) </span><span class="sxs-lookup"><span data-stu-id="4a495-118">[Programming Guide](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md) </span></span>  
 [<span data-ttu-id="4a495-119">ACK 訊息模式</span><span class="sxs-lookup"><span data-stu-id="4a495-119">ACK Message Modes</span></span>](../../adapters-and-accelerators/accelerator-hl7/ack-message-modes.md)