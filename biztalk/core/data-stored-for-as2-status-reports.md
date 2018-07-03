---
title: AS2 狀態報告的儲存的資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6aa4077-3768-436b-99b9-d203a86a7e69
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f14fc95dfba5e29089653ef02dddd1b0b366ff8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012513"
---
# <a name="data-stored-for-as2-status-reports"></a><span data-ttu-id="775b6-102">AS2 狀態報告的儲存資料</span><span class="sxs-lookup"><span data-stu-id="775b6-102">Data Stored for AS2 Status Reports</span></span>
<span data-ttu-id="775b6-103">AS2 狀態報告中有兩個層級的報告： 第一個 if**開啟報告**協議中選取屬性 (從**一般屬性**頁面**一般**索引標籤中**協議屬性**對話方塊)，而第二個如果針對協議選取不可否認性資料庫儲存體屬性。</span><span class="sxs-lookup"><span data-stu-id="775b6-103">Two levels of reporting are available in AS2 status reporting: the first if the **Turn ON Reporting** property is selected for an agreement (from the **General Properties** page of the **General** tab in the **Agreement Properties** dialog box), and the second if a non-repudiation database storage property is selected for an agreement.</span></span>  
  
## <a name="data-stored-if-as2-reporting-is-activated"></a><span data-ttu-id="775b6-104">啟動 AS2 報告時所儲存的資料</span><span class="sxs-lookup"><span data-stu-id="775b6-104">Data Stored If AS2 Reporting Is Activated</span></span>  
 <span data-ttu-id="775b6-105">如果**開啟報告**協議中，選取屬性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會保留記錄的所有已傳送或接收 AS2 訊息和 Mdn。</span><span class="sxs-lookup"><span data-stu-id="775b6-105">If the **Turn ON Reporting** property is selected for an agreement, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will keep a record of all sent or received AS2 messages and MDNs.</span></span>  
  
 <span data-ttu-id="775b6-106">對於已接收的 AS2 訊息，BizTalk Server 會儲存下列資訊：</span><span class="sxs-lookup"><span data-stu-id="775b6-106">For a received AS2 message, BizTalk Server will store the following information:</span></span>  
  
- <span data-ttu-id="775b6-107">AS2 訊息的記錄。</span><span class="sxs-lookup"><span data-stu-id="775b6-107">A record of the AS2 message.</span></span>  
  
  <span data-ttu-id="775b6-108">對於已接收或傳送的 MDN 訊息 (同步或非同步)，BizTalk Server 會儲存下列資訊：</span><span class="sxs-lookup"><span data-stu-id="775b6-108">For a received or sent MDN (synchronous or asynchronous), BizTalk Server will store the following information:</span></span>  
  
- <span data-ttu-id="775b6-109">MDN 的記錄。</span><span class="sxs-lookup"><span data-stu-id="775b6-109">A record of the MDN.</span></span>  
  
  <span data-ttu-id="775b6-110">狀態報告 UI 會啟用 AS2 訊息記錄與適當 MDN 記錄的相互關聯。</span><span class="sxs-lookup"><span data-stu-id="775b6-110">The status reporting UI enables correlation of the AS2 message record to the appropriate MDN record.</span></span>  
  
## <a name="data-stored-if-resend-as2-message-if-mdn-not-received-is-enabled"></a><span data-ttu-id="775b6-111">已啟用若未收到 MDN 則重新傳送 AS2 訊息時所儲存的資料</span><span class="sxs-lookup"><span data-stu-id="775b6-111">Data Stored If Resend AS2 Message If MDN Not Received Is Enabled</span></span>  
 <span data-ttu-id="775b6-112">如果**重新傳送 AS2 訊息，若未收到 MDN**協議中，選取屬性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會記錄下列資訊：</span><span class="sxs-lookup"><span data-stu-id="775b6-112">If the **Resend AS2 message if MDN not received** property is selected for an agreement, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will record the following information:</span></span>  
  
-   <span data-ttu-id="775b6-113">每一次嘗試重新傳送的時間</span><span class="sxs-lookup"><span data-stu-id="775b6-113">Time of each resend attempt</span></span>  
  
-   <span data-ttu-id="775b6-114">每一次嘗試重新傳送的狀態</span><span class="sxs-lookup"><span data-stu-id="775b6-114">Status of each resend attempt</span></span>  
  
-   <span data-ttu-id="775b6-115">每一次嘗試重新傳送的索引</span><span class="sxs-lookup"><span data-stu-id="775b6-115">Index of each resend attempt</span></span>  
  
## <a name="data-stored-if-non-repudiation-database-storage-is-enabled"></a><span data-ttu-id="775b6-116">啟用不可否認性的資料庫儲存時所儲存的資料</span><span class="sxs-lookup"><span data-stu-id="775b6-116">Data Stored If Non-Repudiation Database Storage Is Enabled</span></span>  
 <span data-ttu-id="775b6-117">不可否認性的資料庫儲存是透過選取下列協議屬性加以啟用：</span><span class="sxs-lookup"><span data-stu-id="775b6-117">Non-repudiation database storage is enabled by the following agreement properties is selected:</span></span>  
  
- <span data-ttu-id="775b6-118">為輸出的編碼 AS2 訊息啟用 NRR</span><span class="sxs-lookup"><span data-stu-id="775b6-118">NRR enabled for outbound encoded AS2 messages</span></span>  
  
- <span data-ttu-id="775b6-119">為輸出的解碼 AS2 訊息啟用 NRR</span><span class="sxs-lookup"><span data-stu-id="775b6-119">NRR enabled for outbound decoded AS2 messages</span></span>  
  
- <span data-ttu-id="775b6-120">為輸入的 MDN 啟用 NRR</span><span class="sxs-lookup"><span data-stu-id="775b6-120">NRR enabled for inbound MDN</span></span>  
  
- <span data-ttu-id="775b6-121">為輸入的編碼 AS2 訊息啟用 NRR</span><span class="sxs-lookup"><span data-stu-id="775b6-121">NRR enabled for inbound encoded AS2 messages</span></span>  
  
- <span data-ttu-id="775b6-122">為輸入的解碼 AS2 訊息啟用 NRR</span><span class="sxs-lookup"><span data-stu-id="775b6-122">NRR enabled for inbound decoded AS2 messages</span></span>  
  
- <span data-ttu-id="775b6-123">為輸出的 MDN 啟用 NRR</span><span class="sxs-lookup"><span data-stu-id="775b6-123">NRR enabled for outbound MDN</span></span>  
  
  <span data-ttu-id="775b6-124">如果選取一個或多個上述屬性，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會儲存下列資訊：</span><span class="sxs-lookup"><span data-stu-id="775b6-124">If one or more of the above properties is selected, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will store the following information:</span></span>  
  
- <span data-ttu-id="775b6-125">任何 AS2 訊息的內容和任何 MDN (無論是否具有 AS2 標頭) 的內容。</span><span class="sxs-lookup"><span data-stu-id="775b6-125">The content of any AS2 message and the content of any MDN (with or without AS2 headers).</span></span>  
  
## <a name="data-stored-for-edi-over-as2"></a><span data-ttu-id="775b6-126">透過 AS2 傳送或接收 EDI 時所儲存的資料</span><span class="sxs-lookup"><span data-stu-id="775b6-126">Data Stored For EDI Over AS2</span></span>  
 <span data-ttu-id="775b6-127">如果**開啟報告**針對 EDI 協議，以及 AS2 協議中，選取屬性，則您可以將 AS2 訊息記錄 （包含 EDI 內容） 與 EDI 訊息記錄相互關聯。</span><span class="sxs-lookup"><span data-stu-id="775b6-127">If the **Turn ON Reporting** property is selected both for an EDI agreement as well as an AS2 agreement, then you can correlate an AS2 message record (containing EDI payload) with an EDI message record.</span></span>  
  
 <span data-ttu-id="775b6-128">如果有啟用交易集儲存區，您就可以在狀態報告 UI 中顯示交易集詳細資料和 AS2 訊息內容詳細資料。</span><span class="sxs-lookup"><span data-stu-id="775b6-128">If transaction set storage is enabled, you can display transaction set details and AS2 message content details in the status reporting UI.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="775b6-129">您必須使用 AS2EdiReceive 或 AS2EdiSend 管線，才能存取這些報告。</span><span class="sxs-lookup"><span data-stu-id="775b6-129">You must use the AS2EdiReceive or AS2EdiSend pipeline to have access to these reports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="775b6-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="775b6-130">See Also</span></span>  
 <span data-ttu-id="775b6-131">[儲存 EDI 和 AS2 狀態報告的資料](../core/data-stored-for-edi-and-as2-status-reports.md) </span><span class="sxs-lookup"><span data-stu-id="775b6-131">[Data Stored for EDI and AS2 Status Reports](../core/data-stored-for-edi-and-as2-status-reports.md) </span></span>  
 <span data-ttu-id="775b6-132">[EDI 狀態報告的儲存資料](../core/data-stored-for-edi-status-reports.md) </span><span class="sxs-lookup"><span data-stu-id="775b6-132">[Data Stored for EDI Status Reports](../core/data-stored-for-edi-status-reports.md) </span></span>  
 [<span data-ttu-id="775b6-133">批次狀態報告的儲存資料</span><span class="sxs-lookup"><span data-stu-id="775b6-133">Data Stored for Batching Status Reports</span></span>](../core/data-stored-for-batching-status-reports.md)