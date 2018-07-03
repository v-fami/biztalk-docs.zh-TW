---
title: EDI 解決方案架構 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55709a89-7706-4c64-ada3-16951951c943
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6c4ce03c9188a03b47cc2fbe3f67a8be163acdc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009975"
---
# <a name="edi-solution-architecture"></a><span data-ttu-id="729b3-102">EDI 解決方案架構</span><span class="sxs-lookup"><span data-stu-id="729b3-102">EDI Solution Architecture</span></span>
<span data-ttu-id="729b3-103">「電子資料交換」(EDI) 是商務實體以電子方式交換資料的最普遍方法之一。</span><span class="sxs-lookup"><span data-stu-id="729b3-103">Electronic Data Interchange (EDI) is one of the most prevalent means by which business entities exchange data electronically.</span></span> <span data-ttu-id="729b3-104">EDI 的使用限定訊息語法和標準 （包括 ANSI X12 和 UN/EDIFACT），傳訊通訊協定和傳輸。</span><span class="sxs-lookup"><span data-stu-id="729b3-104">EDI usage entails message syntax and standards (including ANSI X12 and UN/EDIFACT), messaging protocol, and transports.</span></span> <span data-ttu-id="729b3-105">以下是 EDI 傳訊的特性：</span><span class="sxs-lookup"><span data-stu-id="729b3-105">The following are characteristics of EDI messaging:</span></span>  
  
- <span data-ttu-id="729b3-106">EDI 傳訊通訊協定可確保資料一定會如預期般抵達，並且會自動偵測和報告損毀或不正確的資料。</span><span class="sxs-lookup"><span data-stu-id="729b3-106">EDI messaging protocols ensure that data always arrives as expected, and corrupted or incorrect data is automatically detected and reported.</span></span>  
  
- <span data-ttu-id="729b3-107">EDI 機制通常會指定資料彙總方式 (批次處理)。</span><span class="sxs-lookup"><span data-stu-id="729b3-107">EDI mechanisms usually specify data aggregation schemes (batching).</span></span>  
  
- <span data-ttu-id="729b3-108">使用者通常會以實作 EDI 指導方針子集或特定實作的方式，自訂 EDI 文件定義。</span><span class="sxs-lookup"><span data-stu-id="729b3-108">Users often customize EDI document definitions by implementing subset or specific implementation of an EDI guideline.</span></span>  
  
  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="729b3-109"> 會使用可剖析和序列化 EDI 訊息的 EDI 專屬接收和傳送管線來處理 EDI 訊息。</span><span class="sxs-lookup"><span data-stu-id="729b3-109"> processes EDI messages using receive and send pipelines specific to EDI that can parse and serialize EDI messages.</span></span> <span data-ttu-id="729b3-110">本節描述 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的 EDI 解決方案架構，包括接收端和傳送端處理的細節、訊息驗證和狀態報告。</span><span class="sxs-lookup"><span data-stu-id="729b3-110">This section describes the architecture of EDI solutions on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], including specifics of receive-side and send-side processing, message validation, and status reporting.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="729b3-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="729b3-111">In This Section</span></span>  
  
-   [<span data-ttu-id="729b3-112">EDI 傳訊</span><span class="sxs-lookup"><span data-stu-id="729b3-112">EDI Messaging</span></span>](../core/edi-messaging.md)  
  
-   [<span data-ttu-id="729b3-113">EDI 處理中協議的角色</span><span class="sxs-lookup"><span data-stu-id="729b3-113">The Role of Agreements in EDI Processing</span></span>](../core/the-role-of-agreements-in-edi-processing.md)  
  
-   [<span data-ttu-id="729b3-114">BizTalk Server 如何接收 EDI 訊息</span><span class="sxs-lookup"><span data-stu-id="729b3-114">How BizTalk Server Receives EDI Messages</span></span>](../core/how-biztalk-server-receives-edi-messages.md)  
  
-   [<span data-ttu-id="729b3-115">BizTalk Server 如何傳送 EDI 訊息</span><span class="sxs-lookup"><span data-stu-id="729b3-115">How BizTalk Server Sends EDI Messages</span></span>](../core/how-biztalk-server-sends-edi-messages.md)  
  
-   [<span data-ttu-id="729b3-116">EDI 訊息驗證</span><span class="sxs-lookup"><span data-stu-id="729b3-116">EDI Message Validation</span></span>](../core/edi-message-validation.md)  
  
-   [<span data-ttu-id="729b3-117">使用 XML 工具延伸模組</span><span class="sxs-lookup"><span data-stu-id="729b3-117">Using the XML Tool Extensions</span></span>](../core/using-the-xml-tool-extensions.md)