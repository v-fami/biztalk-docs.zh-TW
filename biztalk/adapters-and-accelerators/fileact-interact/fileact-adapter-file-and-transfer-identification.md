---
title: FileAct 配接器檔案和傳輸識別 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6a9aaff1-8816-42cf-b100-fedf964caaf5
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5340f9ad739009ff1cb1257365ceeeb7459511a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223150"
---
# <a name="fileact-adapter-file-and-transfer-identification"></a><span data-ttu-id="b4007-102">FileAct 配接器檔案和傳輸識別碼</span><span class="sxs-lookup"><span data-stu-id="b4007-102">FileAct Adapter File and Transfer Identification</span></span>
<span data-ttu-id="b4007-103">A4SWIFT FileAct 配接器可讓開發人員提供在執行階段的檔案和傳輸識別特性。</span><span class="sxs-lookup"><span data-stu-id="b4007-103">The A4SWIFT FileAct adapter permits the developer to supply file and transfer identification specifics at runtime.</span></span> <span data-ttu-id="b4007-104">這些參數包括：</span><span class="sxs-lookup"><span data-stu-id="b4007-104">These parameters include the following:</span></span>  
  
-   <span data-ttu-id="b4007-105">**實體檔案名稱**– 完整路徑和要讀取或寫入檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="b4007-105">**Physical file name** – the full path and name of the file to be read or written.</span></span> <span data-ttu-id="b4007-106">這個參數絕不會傳遞，並為本機檔案處理常式元件。</span><span class="sxs-lookup"><span data-stu-id="b4007-106">This parameter is never passed, and is local to the file handler component.</span></span>  
  
-   <span data-ttu-id="b4007-107">**邏輯檔案名稱**– SWIFTNet 之間傳遞從傳送至接收應用程式的應用程式的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="b4007-107">**Logical file name** – the file name passed from the sending application to the receiving application across SWIFTNet.</span></span> <span data-ttu-id="b4007-108">這是選擇性，而且，如果未提供，會使用不含路徑的實體檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="b4007-108">This is optional, and, if not supplied, the physical file name without the path is used.</span></span>  
  
-   <span data-ttu-id="b4007-109">**檔案傳輸事件端點**– 基本訂閱事件中指定應用程式處理的檔案傳輸事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="b4007-109">**File transfer event endpoint** – the name specified in the Subscribe Event primitive by the application handling the file transfer events.</span></span> <span data-ttu-id="b4007-110">這個參數會連結至應用程式，用於接收事件報告的檔案傳輸。</span><span class="sxs-lookup"><span data-stu-id="b4007-110">This parameter links the file transfer to the application which receives the event reports.</span></span>  
  
-   <span data-ttu-id="b4007-111">**檔案傳輸參考**– 語彙基元字串所建立和使用的傳輸的控制代碼之 FileAct 子系統本身。</span><span class="sxs-lookup"><span data-stu-id="b4007-111">**File Transfer Reference** – a token string created and used by the FileAct subsystem as a handle on the transfer, itself.</span></span> <span data-ttu-id="b4007-112">FileAct 配接器是而言，這是只將此傳輸，唯一字串。</span><span class="sxs-lookup"><span data-stu-id="b4007-112">This is simply a string unique to this transfer, as far as the FileAct adapter is concerned.</span></span>  
  
-   <span data-ttu-id="b4007-113">**將金鑰傳輸**– 應用程式識別為傳輸時所指派的字串中止用途。</span><span class="sxs-lookup"><span data-stu-id="b4007-113">**Transfer Key** – a string assigned by the application to identify the transfer for abort purposes.</span></span> <span data-ttu-id="b4007-114">如果未提供應用程式，這是與檔案相關聯的 GUID。</span><span class="sxs-lookup"><span data-stu-id="b4007-114">If not provided by the application, this is the GUID associated with the file.</span></span>  
  
-   <span data-ttu-id="b4007-115">**傳送資料分割**– 用來與多項傳輸的字串。</span><span class="sxs-lookup"><span data-stu-id="b4007-115">**Transfer Partition** – a string used to relate multiple transfers.</span></span> <span data-ttu-id="b4007-116">如果未提供開發人員的呼叫中，這將會是"Application Name"指定當定義相關的傳送或接收位置。</span><span class="sxs-lookup"><span data-stu-id="b4007-116">If not supplied in the calls by the developer, this will be the “Application Name” specified when defining the relevant send or receive location.</span></span>  
  
-   <span data-ttu-id="b4007-117">**使用者參考**– 來唯一識別傳送不可否認性的應用程式所定義的字串。</span><span class="sxs-lookup"><span data-stu-id="b4007-117">**User Reference** – a string defined by the application to uniquely identify the transfer for non-repudiation.</span></span> <span data-ttu-id="b4007-118">如果未提供應用程式，這會是與檔案相關聯的 GUID。</span><span class="sxs-lookup"><span data-stu-id="b4007-118">If not provided by the application, this will be the GUID associated with the file.</span></span>  
  
-   <span data-ttu-id="b4007-119">**訊息識別碼**– 唯一定義的初始要求或回應的識別項。</span><span class="sxs-lookup"><span data-stu-id="b4007-119">**Message ID** – the identifier uniquely defining the initial request or response.</span></span> <span data-ttu-id="b4007-120">這是適當的要求或回應訊息相關聯的 GUID 和傳送配接器所產生。</span><span class="sxs-lookup"><span data-stu-id="b4007-120">This is the GUID associated with the appropriate request or response message, as generated by the sending adapter.</span></span> <span data-ttu-id="b4007-121">因此，用戶端產生要求的訊息識別碼，伺服器會回應。</span><span class="sxs-lookup"><span data-stu-id="b4007-121">Thus, the client generates the Message ID for requests and the server does so for responses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4007-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4007-122">See Also</span></span>  
 <span data-ttu-id="b4007-123">[FileAct 配接器架構](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="b4007-123">[FileAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md) </span></span>  
 <span data-ttu-id="b4007-124">[FileAct 配接器即時的端對端原型](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md) </span><span class="sxs-lookup"><span data-stu-id="b4007-124">[FileAct Adapter Real-Time End-to-End Primitives](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md) </span></span>  
 <span data-ttu-id="b4007-125">[FileAct 配接器即時區域基本型別](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md) </span><span class="sxs-lookup"><span data-stu-id="b4007-125">[FileAct Adapter Real-Time Local Primitives](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md) </span></span>  
 <span data-ttu-id="b4007-126">[FileAct 配接器儲存與轉送](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="b4007-126">[FileAct Adapter Store and Forward](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md) </span></span>  
 <span data-ttu-id="b4007-127">[FileAct 配接器安全性架構](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="b4007-127">[FileAct Adapter Security Architecture](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md) </span></span>  
 <span data-ttu-id="b4007-128">[FileAct 配接器支援資訊傳輸](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md) </span><span class="sxs-lookup"><span data-stu-id="b4007-128">[FileAct Adapter Supporting Information Transfer](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md) </span></span>  
 <span data-ttu-id="b4007-129">[FileAct 配接器傳遞通知](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md) </span><span class="sxs-lookup"><span data-stu-id="b4007-129">[FileAct Adapter Delivery Notification](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md) </span></span>  
 [<span data-ttu-id="b4007-130">FileAct 配接器狀態監視</span><span class="sxs-lookup"><span data-stu-id="b4007-130">FileAct Adapter Status Monitoring</span></span>](../../adapters-and-accelerators/fileact-interact/fileact-adapter-status-monitoring.md)