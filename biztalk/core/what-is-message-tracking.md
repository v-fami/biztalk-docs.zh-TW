---
title: 什麼是訊息追蹤？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- HAT, metadata
- HAT, messages
- messages, tracking
- data, HAT
- metadata, tracking
- tracking, metadata
- HAT, data security
- tracking, messages
- configuring [HAT tracking], messages
- data, security
ms.assetid: 51cec59d-b411-4d8f-b771-7b2cf0f38945
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d76a4bd4133906a7949fac9e63816168506f412
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25974636"
---
# <a name="what-is-message-tracking"></a><span data-ttu-id="b74cf-103">什麼是訊息追蹤？</span><span class="sxs-lookup"><span data-stu-id="b74cf-103">What is Message Tracking?</span></span>
<span data-ttu-id="b74cf-104">訊息是資料的電子執行個體，通常在兩個執行的商務程序或應用程式之間進行交換。</span><span class="sxs-lookup"><span data-stu-id="b74cf-104">A message is an electronic instance of data, as typically exchanged between two running business processes or applications.</span></span> <span data-ttu-id="b74cf-105">訊息執行個體是由訊息內文、訊息屬性和中繼資料組成的。</span><span class="sxs-lookup"><span data-stu-id="b74cf-105">A message instance is made up of a message body, message properties, and metadata.</span></span>  
  
 <span data-ttu-id="b74cf-106">您可以使用 BizTalk Server 管理主控台來啟用訊息內文和訊息屬性追蹤。</span><span class="sxs-lookup"><span data-stu-id="b74cf-106">You can use the BizTalk Server Administration Console to enable message body and message property tracking.</span></span> <span data-ttu-id="b74cf-107">在那裡，您也可以檢視追蹤的訊息內文，包括結構描述資訊、強式名稱和產生之訊息的所有升級屬性。</span><span class="sxs-lookup"><span data-stu-id="b74cf-107">There you can also view the tracked message body, including schema information, strong name, and all the promoted properties for the generated message.</span></span>  
  
## <a name="message-body"></a><span data-ttu-id="b74cf-108">訊息內文</span><span class="sxs-lookup"><span data-stu-id="b74cf-108">Message Body</span></span>  
 <span data-ttu-id="b74cf-109">追蹤訊息內文可以提供已傳送和已接收訊息的記錄。</span><span class="sxs-lookup"><span data-stu-id="b74cf-109">Tracking the message body provides a record of messages sent and received.</span></span> <span data-ttu-id="b74cf-110">您必須開啟訊息內文追蹤，才能在服務執行個體處理完成後儲存訊息。</span><span class="sxs-lookup"><span data-stu-id="b74cf-110">You must have message body tracking turned on in order to save messages after service instances processing is complete.</span></span> <span data-ttu-id="b74cf-111">設定完追蹤選項後，可能需要幾分鐘的時間才能檢視訊息。</span><span class="sxs-lookup"><span data-stu-id="b74cf-111">After you have set the tracking options, it can take a few minutes before you can view the messages.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b74cf-112">必須在所有 MessageBox 資料庫上執行 SQL Server Agent 服務。</span><span class="sxs-lookup"><span data-stu-id="b74cf-112">The SQL Server Agent service must be running on all MessageBox databases.</span></span> <span data-ttu-id="b74cf-113">TrackedMessages_Copy_\<MessageBoxName\>工作讓訊息內文追蹤查詢和 WMI。</span><span class="sxs-lookup"><span data-stu-id="b74cf-113">The TrackedMessages_Copy_\<MessageBoxName\> job makes message bodies available to tracking queries and WMI.</span></span> <span data-ttu-id="b74cf-114">若要有效率地複製訊息內文，保留在 MessageBox 資料庫中的人員，並定期複製到 BizTalk 追蹤 (BizTalkDTADb) 資料庫 TrackedMessages_Copy_\<MessageBoxName\>作業。</span><span class="sxs-lookup"><span data-stu-id="b74cf-114">To efficiently copy the message bodies, they remain in the MessageBox database and are periodically copied to the BizTalk Tracking (BizTalkDTADb) database by the TrackedMessages_Copy_\<MessageBoxName\> job.</span></span> <span data-ttu-id="b74cf-115">執行 SQL Server Agent 服務也是讓封存和清除這兩個程序正常運作的必要條件。</span><span class="sxs-lookup"><span data-stu-id="b74cf-115">Having the SQL Server Agent service running is also a prerequisite for the archiving and purging process to work correctly.</span></span>  
  
 <span data-ttu-id="b74cf-116">透過已追蹤訊息可以提供確認回條、進行疑難排解，並且在過去的交易中執行資料採礦。</span><span class="sxs-lookup"><span data-stu-id="b74cf-116">You can use tracked messages to provide confirmation of receipt, to enable troubleshooting, and to allow data mining of historical transactions.</span></span> <span data-ttu-id="b74cf-117">您可以於連接埠、管線和協調流程的輸入和輸出追蹤訊息內文。</span><span class="sxs-lookup"><span data-stu-id="b74cf-117">You can track the message bodies at the input and output of ports, pipelines, and orchestrations.</span></span> <span data-ttu-id="b74cf-118">您可以使用 BizTalk Server 管理主控台、「作業」物件模型 (OM) (建議) 或透過 Windows Management Instrumentation (WMI) 應用程式發展介面 (API) 來復原這些訊息。</span><span class="sxs-lookup"><span data-stu-id="b74cf-118">You can recover these messages using the BizTalk Server Administration Console, using the Operations object model (OM) (recommended) or through Windows Management Instrumentation (WMI) application programming interfaces (APIs).</span></span>  
  
 <span data-ttu-id="b74cf-119">BizTalk Server 不會追蹤沒有成功通過其中一個追蹤點的訊息。</span><span class="sxs-lookup"><span data-stu-id="b74cf-119">BizTalk Server does not track messages that do not successfully make it through one of the tracking points.</span></span> <span data-ttu-id="b74cf-120">在某些情況下，例如無效，因為當擱置訊息，或如果沒有主應用程式等待訊息-它可能會放置於 「 擱置 」 佇列沒有正在追蹤。</span><span class="sxs-lookup"><span data-stu-id="b74cf-120">In some cases—such as when a message is suspended because it is invalid, or if no host is expecting the message—it may be placed in the Suspended queue without being tracked.</span></span> <span data-ttu-id="b74cf-121">若終止此訊息，將不會有任何關於此訊息的記錄。</span><span class="sxs-lookup"><span data-stu-id="b74cf-121">If you terminate this message there will be no record of it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b74cf-122">訊息內文追蹤不對等於合法追蹤，而且也不支援不可否認性。</span><span class="sxs-lookup"><span data-stu-id="b74cf-122">Message body tracking is not a substitute for legally binding auditing, and does not support nonrepudiation.</span></span>  
  
## <a name="message-properties"></a><span data-ttu-id="b74cf-123">訊息屬性</span><span class="sxs-lookup"><span data-stu-id="b74cf-123">Message Properties</span></span>  
 <span data-ttu-id="b74cf-124">訊息屬性中包括升級屬性、路由資訊以及交易夥伴資料。</span><span class="sxs-lookup"><span data-stu-id="b74cf-124">Message properties include promoted properties, routing information, and trading partner data.</span></span> <span data-ttu-id="b74cf-125">訊息屬性追蹤在結果清單中為每個訊息提供升級屬性的記錄，讓您可從已追蹤的數千個訊息中找到特定的訊息。</span><span class="sxs-lookup"><span data-stu-id="b74cf-125">Message property tracking enables you to locate a specific message from the thousands that you may have tracked, by providing a record of promoted properties for each message in the results list.</span></span> <span data-ttu-id="b74cf-126">您便可使用其中一個屬性追蹤訊息本身的子集。</span><span class="sxs-lookup"><span data-stu-id="b74cf-126">You can then track a subset of the message itself, using one of these properties.</span></span>  
  
 <span data-ttu-id="b74cf-127">若要追蹤內容屬性，請定義內容中使用的命名空間屬性結構描述來儲存屬性。</span><span class="sxs-lookup"><span data-stu-id="b74cf-127">To track context properties, you define a property schema for the namespace used in the context to store the properties.</span></span> <span data-ttu-id="b74cf-128">在此檢視中可以選取要追蹤的內容屬性。BizTalk Server 追蹤這些屬性的方式，與追蹤升級訊息屬性的方式相同。</span><span class="sxs-lookup"><span data-stu-id="b74cf-128">From there, you can select the context properties you want to track. BizTalk Server tracks them in the same way it tracks promoted message properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b74cf-129">請確定您在結構描述中為屬性指定不同的名稱。</span><span class="sxs-lookup"><span data-stu-id="b74cf-129">Make sure you give different names to the properties in the schema.</span></span> <span data-ttu-id="b74cf-130">若建立重複名稱，會出現錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="b74cf-130">An error message appears if you create duplicate names.</span></span>  
  
 <span data-ttu-id="b74cf-131">例如，您可以使用「結構描述編輯器」升級 Purchase Order 結構描述的 PO Number 欄位。</span><span class="sxs-lookup"><span data-stu-id="b74cf-131">For example, you could use the Schema Editor to promote the PO Number field from a Purchase Order schema.</span></span> <span data-ttu-id="b74cf-132">然後，使用 [尋找訊息] 檢視，即可找到包含該追蹤欄位之特定值的訊息執行個體，如 PO Number = 16995。</span><span class="sxs-lookup"><span data-stu-id="b74cf-132">Then, using the Find Message View, you could find the message instances that contain a particular value for that tracked field, such as PO Number = 16995.</span></span>  
  
 <span data-ttu-id="b74cf-133">訊息屬性追蹤所產生的負擔遠低於訊息內文追蹤，因為「訊息屬性追蹤」只會追蹤選取的欄位。</span><span class="sxs-lookup"><span data-stu-id="b74cf-133">Message property tracking creates much less overhead than message body tracking, because message property tracking only tracks the selected fields.</span></span> <span data-ttu-id="b74cf-134">設定完訊息屬性的追蹤選項後，可能需要幾分鐘的時間才能檢視屬性。</span><span class="sxs-lookup"><span data-stu-id="b74cf-134">After you set the tracking options for the message property, it can take a few minutes before you can view the properties.</span></span>  
  
## <a name="metadata"></a><span data-ttu-id="b74cf-135">中繼資料</span><span class="sxs-lookup"><span data-stu-id="b74cf-135">Metadata</span></span>  
 <span data-ttu-id="b74cf-136">中繼資料像是訊息執行個體識別項、協調流程或管線記錄訊息，也就是協調流程或管線記錄訊息以及其他相關追蹤詳細資料的地方。</span><span class="sxs-lookup"><span data-stu-id="b74cf-136">Metadata, such as the message instance identifier, the orchestration or pipeline logging the message, the point at which the orchestration or pipeline logs the message, and other relevant tracking details.</span></span> <span data-ttu-id="b74cf-137">為使 MessageBox 資料庫中的訊息可以路由到商務程序，訊息中必須包含訊息類型及來源等內容屬性。</span><span class="sxs-lookup"><span data-stu-id="b74cf-137">For a message in the MessageBox database to route to a business process, it must contain context properties such as message type and origin.</span></span> <span data-ttu-id="b74cf-138">這些屬性即成為中繼資料。</span><span class="sxs-lookup"><span data-stu-id="b74cf-138">These properties become metadata.</span></span> <span data-ttu-id="b74cf-139">訊息與服務執行個體追蹤會使用訂閱準則，對這些中繼資料進行查詢。</span><span class="sxs-lookup"><span data-stu-id="b74cf-139">Message and service instance tracking uses subscription criteria to query against this metadata.</span></span>  
  
 <span data-ttu-id="b74cf-140">透過 BizTalk Server 管理主控台，您可以藉由選取特定的系統結構描述來升級內容屬性。</span><span class="sxs-lookup"><span data-stu-id="b74cf-140">Through the BizTalk Server Administration Console, you can promote context properties by selecting the particular system schema.</span></span> <span data-ttu-id="b74cf-141">系統結構描述位於 Applications\BizTalk.System\Schemas 節點。</span><span class="sxs-lookup"><span data-stu-id="b74cf-141">The system schemas are located in the Applications\BizTalk.System\Schemas node.</span></span> <span data-ttu-id="b74cf-142">BizTalk Server 會全域追蹤這些內容屬性 — 也就是所有訊息現在會都追蹤特定的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="b74cf-142">BizTalk Server tracks these context properties globally—that is, all messages now track the particular context property.</span></span> <span data-ttu-id="b74cf-143">這種作法可能會大幅增加 BizTalk 追蹤資料庫的大小。</span><span class="sxs-lookup"><span data-stu-id="b74cf-143">This may significantly increase the size of the BizTalk Tracking database.</span></span>  
  
## <a name="sensitive-data"></a><span data-ttu-id="b74cf-144">機密資料</span><span class="sxs-lookup"><span data-stu-id="b74cf-144">Sensitive Data</span></span>  
 <span data-ttu-id="b74cf-145">您可以保全以下資料，確保這些資料不會出現在對應的結構描述屬性視窗中，如此一來就不能加以追蹤。</span><span class="sxs-lookup"><span data-stu-id="b74cf-145">You can secure the following data ensuring that it does not appear in corresponding schemas property window and therefore becomes unavailable for tracking.</span></span>  
  
-   <span data-ttu-id="b74cf-146">套用**isSensitive**屬性至屬性結構描述中的任何機密屬性，讓它不再顯示在訊息屬性追蹤組態選項。</span><span class="sxs-lookup"><span data-stu-id="b74cf-146">Apply the **isSensitive** attribute to any sensitive properties in a property schema, so that it is no longer visible in the Message Property tracking configuration selections.</span></span>  
  
-   <span data-ttu-id="b74cf-147">所有現成傳輸都包含標示為機密的密碼，因此無法追蹤這些傳輸。</span><span class="sxs-lookup"><span data-stu-id="b74cf-147">All out-of-box transports contain passwords marked as sensitive, so the transports cannot be tracked.</span></span>  
  
-   <span data-ttu-id="b74cf-148">此外，這些機密屬性不再存在於「管理」資料庫內，所以若您直接在資料庫中設定追蹤選項，就不能追蹤這些屬性。</span><span class="sxs-lookup"><span data-stu-id="b74cf-148">In addition, these sensitive properties are no longer in the Management database, so if you are setting tracking options directly in the database, they are unavailable for tracking.</span></span>  
  
-   <span data-ttu-id="b74cf-149">如果您追蹤網路上輸出的訊息內文，訊息追蹤會從已追蹤訊息內文的捷徑移除所有傳輸屬性。</span><span class="sxs-lookup"><span data-stu-id="b74cf-149">If you track outbound on-the-wire message bodies, message tracking removes all the transport properties from the shortcut of the tracked message body.</span></span> <span data-ttu-id="b74cf-150">因此，訊息追蹤除了從已追蹤訊息內文的捷徑移除所有的輸出傳輸屬性外，也會從輸入傳輸移除屬性。</span><span class="sxs-lookup"><span data-stu-id="b74cf-150">Therefore, in addition to removing outbound transport properties from the shortcut of the tracked message body, message tracking also removes properties from inbound transports.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="b74cf-151">升級的屬性可以包含機密資料。</span><span class="sxs-lookup"><span data-stu-id="b74cf-151">A promoted property can contain sensitive data.</span></span> <span data-ttu-id="b74cf-152">如果追蹤查詢，從 [群組中樞] 頁面會追蹤用來包含機密資料的屬性，以執行追蹤查詢的權限的任何使用者可以檢視這項資料。</span><span class="sxs-lookup"><span data-stu-id="b74cf-152">If tracking queries from the Group Hub page track a property which includes sensitive data, any user with permissions to run the tracking queries can view this data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b74cf-153">請參閱</span><span class="sxs-lookup"><span data-stu-id="b74cf-153">See Also</span></span>  
 [<span data-ttu-id="b74cf-154">使用 BizTalk Server 管理主控台設定追蹤</span><span class="sxs-lookup"><span data-stu-id="b74cf-154">Configuring Tracking Using the BizTalk Server Administration Console</span></span>](http://msdn.microsoft.com/en-us/49b7f9d3-60b5-41bd-ba8b-029253926bef)