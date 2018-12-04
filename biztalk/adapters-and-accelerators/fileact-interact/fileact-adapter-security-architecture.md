---
title: FileAct 配接器安全性架構 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5faeebd6-5287-4ac4-a1db-e3c055d323d2
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be9997dca0a4b7a5c619848e4ed38cf9099bbc16
ms.sourcegitcommit: be6273d612669adfbb9dc9208aaae0a8437d4017
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2018
ms.locfileid: "52826374"
---
# <a name="fileact-adapter-security-architecture"></a><span data-ttu-id="7be74-102">FileAct 配接器安全性架構</span><span class="sxs-lookup"><span data-stu-id="7be74-102">FileAct Adapter Security Architecture</span></span>
<span data-ttu-id="7be74-103">檔案傳輸和接收的安全性是使用 SNL 及 SAG 中具有憑證] 和 [密碼編譯功能來實作。</span><span class="sxs-lookup"><span data-stu-id="7be74-103">Security for the file transmission and receipt is implemented using the certificate and crypto features inherent in SNL and the SAG.</span></span>  <span data-ttu-id="7be74-104">憑證、 等等的管理完全是 FileAct 配接器的範圍外。</span><span class="sxs-lookup"><span data-stu-id="7be74-104">The management of certificates, etc., is completely outside of the scope of the FileAct Adapter.</span></span> <span data-ttu-id="7be74-105">只要 FileAct 服務 SWIFT 與註冊相關聯的 SNL/SAG 執行個體和 SNL/SAG，配接器上安裝正確的軟體會使用透過 SNL Api 的功能。</span><span class="sxs-lookup"><span data-stu-id="7be74-105">As long as the associated SNL/SAG instance is registered for the FileAct service with SWIFT and the software properly installed on SNL/SAG, the adapter makes use of the facilities through the SNL APIs.</span></span> <span data-ttu-id="7be74-106">FileAct 配接器一定會設定為"Advanced"（最佳做法） FACryptoMode。</span><span class="sxs-lookup"><span data-stu-id="7be74-106">The FileAct Adapter will always set the FACryptoMode to “Advanced” (best practice).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7be74-107">配接器，您可以建立個別的安全性內容時，每個傳送埠。</span><span class="sxs-lookup"><span data-stu-id="7be74-107">For the adapter, you can create a separate security context for  each send port.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7be74-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7be74-108">See Also</span></span>  
 <span data-ttu-id="7be74-109">[FileAct 配接器架構](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="7be74-109">[FileAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md) </span></span>  
 <span data-ttu-id="7be74-110">[FileAct 配接器即時端對端原型](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md) </span><span class="sxs-lookup"><span data-stu-id="7be74-110">[FileAct Adapter Real-Time End-to-End Primitives](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md) </span></span>  
 <span data-ttu-id="7be74-111">[FileAct 配接器即時本機原型](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md) </span><span class="sxs-lookup"><span data-stu-id="7be74-111">[FileAct Adapter Real-Time Local Primitives](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md) </span></span>  
 <span data-ttu-id="7be74-112">[FileAct 配接器儲存和轉寄](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="7be74-112">[FileAct Adapter Store and Forward](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md) </span></span>  
 <span data-ttu-id="7be74-113">[FileAct 配接器檔案和傳輸識別](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md) </span><span class="sxs-lookup"><span data-stu-id="7be74-113">[FileAct Adapter File and Transfer Identification](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md) </span></span>  
 <span data-ttu-id="7be74-114">[FileAct 配接器支援資訊傳輸](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md) </span><span class="sxs-lookup"><span data-stu-id="7be74-114">[FileAct Adapter Supporting Information Transfer](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md) </span></span>  
 <span data-ttu-id="7be74-115">[FileAct 配接器傳遞通知](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md) </span><span class="sxs-lookup"><span data-stu-id="7be74-115">[FileAct Adapter Delivery Notification](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md) </span></span>  
 [<span data-ttu-id="7be74-116">FileAct 配接器狀態監控</span><span class="sxs-lookup"><span data-stu-id="7be74-116">FileAct Adapter Status Monitoring</span></span>](../../adapters-and-accelerators/fileact-interact/fileact-adapter-status-monitoring.md)
