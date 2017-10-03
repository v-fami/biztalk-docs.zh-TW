---
title: "FileAct 配接器支援資訊傳輸 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fc27561-9abb-4496-9db7-f221a6c90738
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5aefba5fe85a8a275d3b2050d8c08cc98f74d06
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="fileact-adapter-supporting-information-transfer"></a><span data-ttu-id="ac095-102">FileAct 配接器支援資訊傳輸</span><span class="sxs-lookup"><span data-stu-id="ac095-102">FileAct Adapter Supporting Information Transfer</span></span>
<span data-ttu-id="ac095-103">FileAct 配接器允許選擇性的支援資訊的檔案傳輸。</span><span class="sxs-lookup"><span data-stu-id="ac095-103">The FileAct adapter permits the optional transfer of supporting information with files.</span></span> <span data-ttu-id="ac095-104">這項資訊會傳送一種應用程式。</span><span class="sxs-lookup"><span data-stu-id="ac095-104">This information is transferred at the discretion of the application.</span></span> <span data-ttu-id="ac095-105">配接器不會進行這項資訊在起始端除了驗證它的正確格式的任何特殊處理。</span><span class="sxs-lookup"><span data-stu-id="ac095-105">The adapter does not do any special processing of this information on the originating side except to validate that it is in the correct format.</span></span> <span data-ttu-id="ac095-106">構成的支援資訊的元件包括：</span><span class="sxs-lookup"><span data-stu-id="ac095-106">The elements which comprise supporting information include:</span></span>  
  
-   <span data-ttu-id="ac095-107">檔案描述和檔案資訊</span><span class="sxs-lookup"><span data-stu-id="ac095-107">File description and file information</span></span>  
  
-   <span data-ttu-id="ac095-108">描述，然後傳輸資訊</span><span class="sxs-lookup"><span data-stu-id="ac095-108">Transfer description and transfer information</span></span>  
  
-   <span data-ttu-id="ac095-109">通知的描述，並通知資訊</span><span class="sxs-lookup"><span data-stu-id="ac095-109">Acknowledgement description and acknowledgement information</span></span>  
  
-   <span data-ttu-id="ac095-110">拒絕描述和拒絕資訊</span><span class="sxs-lookup"><span data-stu-id="ac095-110">Rejection description and reject information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac095-111">其中一個元件的檔案資訊定義壓縮和解壓縮功能。</span><span class="sxs-lookup"><span data-stu-id="ac095-111">One of the components of file information defines compression and decompression.</span></span> <span data-ttu-id="ac095-112">壓縮和解壓縮負責管理的應用程式，而不是配接器。</span><span class="sxs-lookup"><span data-stu-id="ac095-112">Compression and decompression are the responsibility of the application, not the adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac095-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac095-113">See Also</span></span>  
 <span data-ttu-id="ac095-114">[FileAct 配接器架構](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="ac095-114">[FileAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md) </span></span>  
 <span data-ttu-id="ac095-115">[FileAct 配接器即時的端對端原型](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md) </span><span class="sxs-lookup"><span data-stu-id="ac095-115">[FileAct Adapter Real-Time End-to-End Primitives](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md) </span></span>  
 <span data-ttu-id="ac095-116">[FileAct 配接器即時區域基本型別](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md) </span><span class="sxs-lookup"><span data-stu-id="ac095-116">[FileAct Adapter Real-Time Local Primitives](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md) </span></span>  
 <span data-ttu-id="ac095-117">[FileAct 配接器儲存與轉送](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="ac095-117">[FileAct Adapter Store and Forward](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md) </span></span>  
 <span data-ttu-id="ac095-118">[FileAct 配接器安全性架構](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="ac095-118">[FileAct Adapter Security Architecture](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md) </span></span>  
 <span data-ttu-id="ac095-119">[FileAct 配接器檔案和傳輸識別碼](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md) </span><span class="sxs-lookup"><span data-stu-id="ac095-119">[FileAct Adapter File and Transfer Identification](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md) </span></span>  
 <span data-ttu-id="ac095-120">[FileAct 配接器傳遞通知](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md) </span><span class="sxs-lookup"><span data-stu-id="ac095-120">[FileAct Adapter Delivery Notification](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md) </span></span>  
 [<span data-ttu-id="ac095-121">FileAct 配接器狀態監視</span><span class="sxs-lookup"><span data-stu-id="ac095-121">FileAct Adapter Status Monitoring</span></span>](../../adapters-and-accelerators/fileact-interact/fileact-adapter-status-monitoring.md)