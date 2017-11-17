---
title: "訊息佇列的佇列 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [MSMQ adapters], queue paths
- naming conventions, MSMQ adapters
- configuring [MSMQ adapters], naming conventions
- messages, queuing
- MSMQ adapters, troubleshooting
- MSMQ adapters, message queues
- configuring [MSMQ adapters], troubleshooting
- troubleshooting, queue paths [MSMQ adapters]
- naming conventions, queue paths [MSMQ adapters]
- configuring [MSMQ adapters], message queues
ms.assetid: b802348e-8543-4b06-a6e4-149b86139fb1
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9156b6d6fa1374f532efb354e5816c054b83994
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-queuing-queues"></a><span data-ttu-id="6d623-102">訊息佇列的佇列</span><span class="sxs-lookup"><span data-stu-id="6d623-102">Message Queuing Queues</span></span>
<span data-ttu-id="6d623-103">本節描述使用 MSMQ 配接器時如何指定 Microsoft Message Queuing (也稱為 MSMQ) 佇列。</span><span class="sxs-lookup"><span data-stu-id="6d623-103">This section describes how to specify Microsoft Message Queuing (also known as MSMQ) queues when you use the MSMQ adapter.</span></span> <span data-ttu-id="6d623-104">內容不但描述指定路徑的慣例，同時也說明格式名稱在轉譯路徑成為佇列目的地時所扮演的角色。</span><span class="sxs-lookup"><span data-stu-id="6d623-104">It describes the conventions for specifying paths and also describes the role that format names play in translating paths into queue designations.</span></span>  
  
## <a name="queue-path-naming-conventions"></a><span data-ttu-id="6d623-105">佇列路徑命名慣例</span><span class="sxs-lookup"><span data-stu-id="6d623-105">Queue Path Naming Conventions</span></span>  
 <span data-ttu-id="6d623-106">若佇列名稱是指路徑，請使用下表中的命名慣例。</span><span class="sxs-lookup"><span data-stu-id="6d623-106">If the queue name refers to a path, use the naming conventions in the following table.</span></span>  
  
|<span data-ttu-id="6d623-107">**佇列類型**</span><span class="sxs-lookup"><span data-stu-id="6d623-107">**Queue type**</span></span>|<span data-ttu-id="6d623-108">**路徑的語法**</span><span class="sxs-lookup"><span data-stu-id="6d623-108">**Syntax for path**</span></span>|  
|--------------------|-------------------------|  
|<span data-ttu-id="6d623-109">公用佇列</span><span class="sxs-lookup"><span data-stu-id="6d623-109">Public queue</span></span>|<span data-ttu-id="6d623-110">*Computername*\QueueName</span><span class="sxs-lookup"><span data-stu-id="6d623-110">*Computername*\QueueName</span></span>|  
|<span data-ttu-id="6d623-111">私用佇列</span><span class="sxs-lookup"><span data-stu-id="6d623-111">Private queue</span></span>|<span data-ttu-id="6d623-112">*Computername*\Private$\QueueName</span><span class="sxs-lookup"><span data-stu-id="6d623-112">*Computername*\Private$\QueueName</span></span>|  
|<span data-ttu-id="6d623-113">記錄檔佇列</span><span class="sxs-lookup"><span data-stu-id="6d623-113">Journal queue</span></span>|<span data-ttu-id="6d623-114">*Computername*\QueueName\Journal$</span><span class="sxs-lookup"><span data-stu-id="6d623-114">*Computername*\QueueName\Journal$</span></span>|  
|<span data-ttu-id="6d623-115">電腦日誌佇列**附註：**用於只接收佇列。</span><span class="sxs-lookup"><span data-stu-id="6d623-115">Computer journal queue **Note:**  Use for receive queue only.</span></span>|<span data-ttu-id="6d623-116">*Computername*\Journal$</span><span class="sxs-lookup"><span data-stu-id="6d623-116">*Computername*\Journal$</span></span>|  
|<span data-ttu-id="6d623-117">電腦寄不出的信件佇列**附註：**用於只接收佇列。</span><span class="sxs-lookup"><span data-stu-id="6d623-117">Computer dead-letter queue **Note:**  Use for receive queue only.</span></span>|<span data-ttu-id="6d623-118">*Computername*\Deadletter$</span><span class="sxs-lookup"><span data-stu-id="6d623-118">*Computername*\Deadletter$</span></span>|  
|<span data-ttu-id="6d623-119">電腦交易無法寄不出信件佇列**附註：**用於只接收佇列。</span><span class="sxs-lookup"><span data-stu-id="6d623-119">Computer transaction dead-letter queue **Note:**  Use for receive queue only.</span></span>|<span data-ttu-id="6d623-120">*Computername*\XactDeadletter$</span><span class="sxs-lookup"><span data-stu-id="6d623-120">*Computername*\XactDeadletter$</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="6d623-121">佇列的路徑必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="6d623-121">The path of the queue must be unique.</span></span>  
  
 <span data-ttu-id="6d623-122">若佇列名稱是指格式名稱，會採用字串的形式，指示佇列是公用還是私用，並視需要接著為佇列和其他識別項所產生的 GUID。</span><span class="sxs-lookup"><span data-stu-id="6d623-122">If the queue name refers to a format name, it takes the form of a string that indicates whether a queue is public or private, followed by a generated GUID for the queue and other identifiers as needed.</span></span> <span data-ttu-id="6d623-123">使用下表中的命名慣例。</span><span class="sxs-lookup"><span data-stu-id="6d623-123">Use the naming conventions in the following table.</span></span>  
  
|<span data-ttu-id="6d623-124">**格式類型**</span><span class="sxs-lookup"><span data-stu-id="6d623-124">**Format type**</span></span>|<span data-ttu-id="6d623-125">**格式名稱語法**</span><span class="sxs-lookup"><span data-stu-id="6d623-125">**Syntax for format name**</span></span>|  
|---------------------|--------------------------------|  
|<span data-ttu-id="6d623-126">公用</span><span class="sxs-lookup"><span data-stu-id="6d623-126">Public</span></span>|<span data-ttu-id="6d623-127">*使用 FormatName*： 公用 = QueueGUID</span><span class="sxs-lookup"><span data-stu-id="6d623-127">*FormatName*:Public=QueueGUID</span></span>|  
|<span data-ttu-id="6d623-128">直接</span><span class="sxs-lookup"><span data-stu-id="6d623-128">Direct</span></span>|<span data-ttu-id="6d623-129">*使用 FormatName*: DIRECT = SPX:NetworkNumber:HostNumber\QueueName</span><span class="sxs-lookup"><span data-stu-id="6d623-129">*FormatName*:DIRECT=SPX:NetworkNumber:HostNumber\QueueName</span></span><br /><br /> <span data-ttu-id="6d623-130">*使用 FormatName*: DIRECT = TCP:IPAddress\QueueName</span><span class="sxs-lookup"><span data-stu-id="6d623-130">*FormatName*: DIRECT=TCP:IPAddress\QueueName</span></span><br /><br /> <span data-ttu-id="6d623-131">*使用 FormatName*: DIRECT = OS:ComputerName\QueueName</span><span class="sxs-lookup"><span data-stu-id="6d623-131">*FormatName*: DIRECT=OS:ComputerName\QueueName</span></span>|  
  
 <span data-ttu-id="6d623-132">若傳送埠佇列是通訊群組清單，那麼佇列路徑語法是：</span><span class="sxs-lookup"><span data-stu-id="6d623-132">If the send port queue path is a distribution list, then the queue path syntax is:</span></span>  
  
 <span data-ttu-id="6d623-133">DL=DistributionListGUID</span><span class="sxs-lookup"><span data-stu-id="6d623-133">DL=DistributionListGUID</span></span>  
  
 <span data-ttu-id="6d623-134">若傳送或接收佇列路徑是 HTTP 或 HTTPS URL，那麼語法是：</span><span class="sxs-lookup"><span data-stu-id="6d623-134">If the send or receive queue path is an HTTP or HTTPS URL, then the syntax is:</span></span>  
  
 <span data-ttu-id="6d623-135">FormatName:DIRECT = http: / /\<用戶端名稱 > /msmq/\<佇列名稱 ></span><span class="sxs-lookup"><span data-stu-id="6d623-135">FormatName:DIRECT=http://\<client name>/msmq/\<queue name></span></span>  
  
 <span data-ttu-id="6d623-136">FormatName:DIRECT = https: / /\<用戶端名稱 > /msmq/\<佇列名稱 ></span><span class="sxs-lookup"><span data-stu-id="6d623-136">FormatName:DIRECT=https://\<client name>/msmq/\<queue name></span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d623-137">"msmq" 是訊息佇列在 Internet Information Services (IIS) 中建立的虛擬資料夾。</span><span class="sxs-lookup"><span data-stu-id="6d623-137">"msmq" is the virtual folder that Message Queuing creates in Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d623-138">您只能使用 HTTP 傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="6d623-138">You can only use HTTP to send messages.</span></span> <span data-ttu-id="6d623-139">若佇列是使用 HTTP 直接格式名稱所開啟的，您就無法在遠端電腦上的佇列中讀取訊息。</span><span class="sxs-lookup"><span data-stu-id="6d623-139">You cannot read messages in a queue on a remote computer if the queue is opened using an HTTP direct format name.</span></span> <span data-ttu-id="6d623-140">不過，您仍然可以使用沒有 HTTP 的私用或公用佇列路徑，從遠端佇列接收 SOAP (格式化) 訊息。</span><span class="sxs-lookup"><span data-stu-id="6d623-140">However, you can still receive SOAP (formatted) messages from a remote queue by using the private or public queue path without HTTP.</span></span>  
  
 <span data-ttu-id="6d623-141">若佇列名稱指的是系統管理員為佇列所指定的說明性文字標籤，那麼表示這個標籤的佇列路徑語法是：</span><span class="sxs-lookup"><span data-stu-id="6d623-141">If the queue name refers to a descriptive text label that the administrator specified for the queue, then the syntax of the queue path referring to this label is:</span></span>  
  
 <span data-ttu-id="6d623-142">LABEL:MyQueue</span><span class="sxs-lookup"><span data-stu-id="6d623-142">LABEL:MyQueue</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d623-143">標籤不一定是唯一的。</span><span class="sxs-lookup"><span data-stu-id="6d623-143">Labels are not always unique.</span></span> <span data-ttu-id="6d623-144">因此，當您嘗試使用其標籤連接到特定佇列時，若發生名稱衝突，您就會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="6d623-144">Therefore, you will receive an error if a name conflict exists when you try to connect to a specific queue by using its label.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d623-145">標籤是配接器的必要傳輸欄位。</span><span class="sxs-lookup"><span data-stu-id="6d623-145">The label is a required transport field for the adapter.</span></span>  
  
## <a name="role-of-the-format-name"></a><span data-ttu-id="6d623-146">格式名稱的角色</span><span class="sxs-lookup"><span data-stu-id="6d623-146">Role of the Format Name</span></span>  
 <span data-ttu-id="6d623-147">訊息佇列使用格式名稱來識別佇列以及決定存取方式。</span><span class="sxs-lookup"><span data-stu-id="6d623-147">Message Queuing uses the format name to identify a queue and to determine how to access it.</span></span> <span data-ttu-id="6d623-148">訊息佇列會指派格式名稱到佇列。</span><span class="sxs-lookup"><span data-stu-id="6d623-148">Message Queuing assigns the format name to the queue.</span></span>  
  
 <span data-ttu-id="6d623-149">當您使用路徑名稱語法指定佇列時，例如 myMachine\myQueue，訊息佇列會查詢路徑以尋找相關的格式名稱。</span><span class="sxs-lookup"><span data-stu-id="6d623-149">When you specify a queue using the path name syntax, for example myMachine\myQueue, Message Queuing looks up the path to find the associated format name.</span></span> <span data-ttu-id="6d623-150">接著，訊息佇列會使用該格式名稱來存取佇列。</span><span class="sxs-lookup"><span data-stu-id="6d623-150">Message Queuing then uses that format name to access the queue.</span></span> <span data-ttu-id="6d623-151">當您指定格式名稱時，訊息佇列會使用您所使用的格式名稱。</span><span class="sxs-lookup"><span data-stu-id="6d623-151">When you specify the format name, Message Queuing uses the format name you use.</span></span>  
  
 <span data-ttu-id="6d623-152">如需有關格式名稱的詳細資訊，請參閱＜.NET Framework 類別庫說明＞中的＜MessageQueue.FormatName 屬性＞。</span><span class="sxs-lookup"><span data-stu-id="6d623-152">For more information about format names, see "MessageQueue.FormatName Property" in .NET Framework Class Library Help.</span></span>  
  
## <a name="troubleshooting-queue-paths"></a><span data-ttu-id="6d623-153">疑難排解佇列路徑</span><span class="sxs-lookup"><span data-stu-id="6d623-153">Troubleshooting Queue Paths</span></span>  
  
-   <span data-ttu-id="6d623-154">若提供的佇列路徑的語法不符合之前在＜佇列路徑命名慣例＞中所描述的其中一種格式，會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6d623-154">An exception occurs if the syntax of the provided queue path does not match one of the formats described earlier in "Queue Path Naming Conventions."</span></span>  
  
-   <span data-ttu-id="6d623-155">下列字元在佇列路徑中的電腦名稱無效：</span><span class="sxs-lookup"><span data-stu-id="6d623-155">The following are not valid characters for computer names in the queue path:</span></span>  
  
     <span data-ttu-id="6d623-156">\ ; , + "</span><span class="sxs-lookup"><span data-stu-id="6d623-156">\ ; , + "</span></span>  
  
     <span data-ttu-id="6d623-157">若電腦名稱是數字，會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6d623-157">An exception occurs if the computer name is a number.</span></span> <span data-ttu-id="6d623-158">例如： 234\private$ \queue。</span><span class="sxs-lookup"><span data-stu-id="6d623-158">For example: 234\private$\queue.</span></span>  
  
-   <span data-ttu-id="6d623-159">對於電腦無法寄出的信件佇列、電腦記錄檔佇列以及電腦交易無法寄出的信件佇列，若使用者指定任何一個系統佇列做為傳送的目的地佇列，會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6d623-159">For a computer dead-letter queue, computer journal queue, and computer transaction dead-letter queue, an exception occurs if the user specifies any one of the system queues as the destination queue for send.</span></span>  
  
-   <span data-ttu-id="6d623-160">**System.Messaging.MessageQueue.Exists**不適用於遠端佇列。</span><span class="sxs-lookup"><span data-stu-id="6d623-160">**System.Messaging.MessageQueue.Exists** does not work for remote queues.</span></span> <span data-ttu-id="6d623-161">如需詳細資訊，請參閱＜.NET Framework 類別庫說明＞中的＜MessageQueue.Exists 方法＞。</span><span class="sxs-lookup"><span data-stu-id="6d623-161">For more information, see "MessageQueue.Exists Method" in .NET Framework Class Library Help.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d623-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d623-162">See Also</span></span>  
 [<span data-ttu-id="6d623-163">設定 MSMQ 配接器</span><span class="sxs-lookup"><span data-stu-id="6d623-163">Configuring the MSMQ Adapter</span></span>](../core/configuring-the-msmq-adapter.md)