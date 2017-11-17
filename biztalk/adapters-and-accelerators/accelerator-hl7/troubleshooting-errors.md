---
title: "疑難排解錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors, troubleshooting
- troubleshooting, errors
ms.assetid: 08cc95a3-4be9-450f-a015-e031011158f7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ae7ad99b699da29d4d8680375f88e4d4a74ff66a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-errors"></a><span data-ttu-id="cd387-102">疑難排解錯誤</span><span class="sxs-lookup"><span data-stu-id="cd387-102">Troubleshooting Errors</span></span>
<span data-ttu-id="cd387-103">本節說明的相關問題[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="cd387-103">This section addresses issues related to [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] generated errors.</span></span>  
  
## <a name="the-mllp-adapter-can-run-only-on-a-single-host-instance"></a><span data-ttu-id="cd387-104">MLLP 配接器可以只在單一主控件執行個體上執行</span><span class="sxs-lookup"><span data-stu-id="cd387-104">The MLLP adapter can run only on a single host instance</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="cd387-105">徵兆</span><span class="sxs-lookup"><span data-stu-id="cd387-105">Symptom</span></span>  
 <span data-ttu-id="cd387-106">您無法啟用與傳輸類型為 MLLP 的接收位置和不同的接收處理常式比另一個現有的接收位置。</span><span class="sxs-lookup"><span data-stu-id="cd387-106">You cannot enable a receive location with a transport type of MLLP and a different receive handler than another existing receive location.</span></span> <span data-ttu-id="cd387-107">此外，您無法登錄並啟動傳送埠使用不同的傳送處理常式，比另一個現有的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="cd387-107">In addition, you cannot enlist and start a send port with a different send handler than another existing send port.</span></span>  
  
<span data-ttu-id="cd387-108">**可能的原因**： 您只能使用一個 MLLP 接收 （或傳送） 在單一伺服器上的處理常式。</span><span class="sxs-lookup"><span data-stu-id="cd387-108">**Possible Cause** : You can only use one MLLP receive (or send) handler on a single server.</span></span> <span data-ttu-id="cd387-109">此外，URI 指定的接收位置 （或傳送埠） （MLLP 傳輸屬性中的主機名稱） 必須是"localhost"或伺服器名稱，其中的主控件執行個體就會接收 （或傳送） 配接器處理常式正在執行。</span><span class="sxs-lookup"><span data-stu-id="cd387-109">In addition, the URI designated for the receive location (or send port) (the Host name in the MLLP Transport Properties) must either be "localhost" or the server name where the host instance for the receive (or send) adapter handler is running.</span></span>  
  
<span data-ttu-id="cd387-110">**解析**： 單一伺服器上的所有 MLLP 的接收位置 （或傳送埠） 指定相同的接收 （或傳送） 處理常式。</span><span class="sxs-lookup"><span data-stu-id="cd387-110">**Resolution** : Designate the same receive (or send) handler for all MLLP receive locations (or send ports) on a single server.</span></span>  
  
## <a name="msh-and-ack-schemas-must-be-added-to-only-one-project"></a><span data-ttu-id="cd387-111">MSH 和通知結構描述必須加入至只有一個專案</span><span class="sxs-lookup"><span data-stu-id="cd387-111">MSH and ACK schemas must be added to only one project</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="cd387-112">徵兆</span><span class="sxs-lookup"><span data-stu-id="cd387-112">Symptom</span></span>  
 <span data-ttu-id="cd387-113">當您嘗試建置專案時，會取得其中一種下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="cd387-113">When you attempt to build a project, you get one of the following errors:</span></span>  
  
`Error: Cannot locate document specification as multiple schemas match the message type "http://microsoft.com/HealthCare/HL7/2X#MSH_24_GLO_DEF"`
  
`Schema http://microsoft.com/HealthCare/HL7/2X#MSH_24_GLO_DEF not found`
  
<span data-ttu-id="cd387-114">**可能的原因**: MSH 和通知結構描述 （MSH_25_GLO_DEF.xsd 和 ACK_24_GLO_DEF.xsd） 已部署多個專案中。</span><span class="sxs-lookup"><span data-stu-id="cd387-114">**Possible Cause** : The MSH and ACK schemas (MSH_25_GLO_DEF.xsd and ACK_24_GLO_DEF.xsd) have been deployed in multiple projects.</span></span>  
  
<span data-ttu-id="cd387-115">**解析**： 請確認 MSH_25_GLO_DEF.xsd 和 ACK_24_GLO_DEF.xsd 有已新增至只有一個專案。</span><span class="sxs-lookup"><span data-stu-id="cd387-115">**Resolution** : Ensure that MSH_25_GLO_DEF.xsd and ACK_24_GLO_DEF.xsd have been added to only one project.</span></span>  
  
## <a name="exception-of-type-systemoutofmemoryexception-has-thrown-an-error-in-the-event-log"></a><span data-ttu-id="cd387-116">型別 System.OutOfMemoryException 已擲回例外狀況錯誤事件記錄檔中</span><span class="sxs-lookup"><span data-stu-id="cd387-116">Exception of type System.OutOfMemoryException has thrown an error in the Event Log</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="cd387-117">徵兆</span><span class="sxs-lookup"><span data-stu-id="cd387-117">Symptom</span></span>  
 <span data-ttu-id="cd387-118">您可以取得下列或類似的錯誤事件記錄檔中：</span><span class="sxs-lookup"><span data-stu-id="cd387-118">You get the following or similar error in the Event Log:</span></span>  
  
`Exception of type System.OutOfMemoryException has thrown an error.`
  
<span data-ttu-id="cd387-119">**可能的原因**： 處理大量訊息，有些時[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]引擎元件可能會出現記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="cd387-119">**Possible Cause** : While processing a large number of messages, some [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] engine components may exhibit memory leaks.</span></span>  
  
<span data-ttu-id="cd387-120">**解析**： 重新啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cd387-120">**Resolution** : Restart [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="header-serialization-generates-an-error-in-the-event-viewer"></a><span data-ttu-id="cd387-121">標頭序列化事件檢視器中會產生錯誤</span><span class="sxs-lookup"><span data-stu-id="cd387-121">Header serialization generates an error in the Event Viewer</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="cd387-122">徵兆</span><span class="sxs-lookup"><span data-stu-id="cd387-122">Symptom</span></span>  
 <span data-ttu-id="cd387-123">即使 「 狀況與活動追蹤 (HAT) 工具中的訊息表示成功，您可以取得事件記錄檔中的下列或類似的錯誤：</span><span class="sxs-lookup"><span data-stu-id="cd387-123">You get the following or similar error in the Event Log, even though the message in the Health and Activity Tracking (HAT) tool indicates success:</span></span>  
  
`An error happened in the header during serialization.`
  
<span data-ttu-id="cd387-124">**可能的原因**： 訊息標頭轉換值未正確設定[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管。</span><span class="sxs-lookup"><span data-stu-id="cd387-124">**Possible Cause** : The message header transformation value is not set correctly in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.</span></span>  
  
<span data-ttu-id="cd387-125">**解析**： 確認 MSH 對應中的值[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管。</span><span class="sxs-lookup"><span data-stu-id="cd387-125">**Resolution** : Verify MSH map values in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.</span></span>  
  
## <a name="duplicate-event-id-4133-serializer-errors-are-logged"></a><span data-ttu-id="cd387-126">重複的事件識別碼 4133 序列化程式錯誤記錄</span><span class="sxs-lookup"><span data-stu-id="cd387-126">Duplicate Event ID 4133 serializer errors are logged</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="cd387-127">徵兆</span><span class="sxs-lookup"><span data-stu-id="cd387-127">Symptom</span></span>  
 <span data-ttu-id="cd387-128">事件識別碼 4133 – 」 錯誤是發生在標頭在序列化期間 」 就會發生兩次的訊息 MSH11 值不是有效的每個執行個體。</span><span class="sxs-lookup"><span data-stu-id="cd387-128">Event ID 4133 – "Error happened in header during serialization" occurs twice for every instance of a message with a MSH11 value that is not valid.</span></span>  
  
<span data-ttu-id="cd387-129">**可能的原因**： 沒有事件記錄檔中的重複錯誤處理兩個通知 （認可和應用程式通知） 時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="cd387-129">**Possible Cause** : An error occurred while processing two acknowledgments (Commit and Application ACKs) without duplicate errors in the Event Log.</span></span> <span data-ttu-id="cd387-130">相反地，您會收到一個事件識別碼 4133 每兩個認可。</span><span class="sxs-lookup"><span data-stu-id="cd387-130">Instead, you receive one Event ID 4133 for each of the two ACKs.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="cd387-131">它會產生每個通知建立記錄項目。</span><span class="sxs-lookup"><span data-stu-id="cd387-131"> creates a log entry for each ACK it generates.</span></span>  
  
<span data-ttu-id="cd387-132">**解析**： 請確定您的郵件擁有正確格式化，並填入 MSH11 欄位。</span><span class="sxs-lookup"><span data-stu-id="cd387-132">**Resolution** : Ensure that your messages have a correctly formatted and populated MSH11 field.</span></span>  
  
## <a name="send-pipeline-generates-an-error-when-using-the-2-way-mllp-adapter"></a><span data-ttu-id="cd387-133">傳送管線會使用 2 方式 MLLP 配接器時，會產生錯誤</span><span class="sxs-lookup"><span data-stu-id="cd387-133">Send pipeline generates an error when using the 2-way MLLP adapter</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="cd387-134">徵兆</span><span class="sxs-lookup"><span data-stu-id="cd387-134">Symptom</span></span>  
 <span data-ttu-id="cd387-135">您可以取得下列或類似的錯誤事件記錄檔中：</span><span class="sxs-lookup"><span data-stu-id="cd387-135">You get the following or similar error in the Event Log:</span></span>  
  
`There was a failure executing the send pipeline: "[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2XPipelines.[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2XSendPipeline" Source: "[!INCLUDE[btsCoName](../../includes/btsconame-md.md)].Solutions.[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].HL72fAsm" Send Port: "<*host name: port number*>" Reason: Message does not contain a part with name MSHSegment.`
  
<span data-ttu-id="cd387-136">**可能的原因**： 接收的應用程式未使用通知來回應和[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]預期從接收的應用程式的回應。</span><span class="sxs-lookup"><span data-stu-id="cd387-136">**Possible Cause** : The receiving application does not respond with an Acknowledgment and [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is expecting a response from the receiving application.</span></span>  
  
<span data-ttu-id="cd387-137">**解析**： 這是根據設計，而且您可以忽略的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="cd387-137">**Resolution** : This is by design, and you can ignore the error message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd387-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd387-138">See Also</span></span>  
 [<span data-ttu-id="cd387-139">HL7 中的疑難排解和已知問題</span><span class="sxs-lookup"><span data-stu-id="cd387-139">Troubleshooting and known issues in HL7</span></span>](../../adapters-and-accelerators/accelerator-hl7/troubleshooting-and-known-issues-in-hl7.md)