---
title: SAP 配接器支援哪些作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapters, performing operations
ms.assetid: 4b676336-526d-42b9-9ff2-1a4f27df1a78
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee217572e0bf56e7a4f7e4810421befeb08bfc3e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216046"
---
# <a name="what-operations-are-supported-by-the-sap-adapter"></a><span data-ttu-id="e7775-102">SAP 配接器支援哪些作業</span><span class="sxs-lookup"><span data-stu-id="e7775-102">What operations are supported by the SAP adapter</span></span>
<span data-ttu-id="e7775-103">建立 BizTalk 專案、 使用 WCF 通道模型，或使用 WCF 服務模型配接器用戶端可以執行 SAP 系統上的作業。</span><span class="sxs-lookup"><span data-stu-id="e7775-103">Adapter clients can perform operations on the SAP system by creating BizTalk projects, by using the WCF channel model, or by using the WCF service model.</span></span> <span data-ttu-id="e7775-104">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會公開應用程式可以在其上叫用，接著，可以呼叫應用程式上的作業。</span><span class="sxs-lookup"><span data-stu-id="e7775-104">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] exposes operations that applications can invoke on it and that it can, in turn, invoke on applications.</span></span> <span data-ttu-id="e7775-105">這些作業會叫用透過通道傳送 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="e7775-105">These operations are invoked by sending SOAP messages over a channel.</span></span> <span data-ttu-id="e7775-106">如果需要回應，它會傳回 SOAP 訊息中透過相同的通道。</span><span class="sxs-lookup"><span data-stu-id="e7775-106">If a response is required, it is returned in a SOAP message over the same channel.</span></span> <span data-ttu-id="e7775-107">訊息結構和與每個作業相關聯的 SOAP 動作的相關資訊，請參閱[訊息和訊息結構描述，BizTalk adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="e7775-107">For information about the message structure and the SOAP action associated with each operation, see [Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md).</span></span>  
  
 <span data-ttu-id="e7775-108">本節提供有關支援的 SAP 系統使用的作業資訊[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e7775-108">This section provides information about the operations supported on the SAP system using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e7775-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="e7775-109">In This Section</span></span>  
  
-   [<span data-ttu-id="e7775-110">作業中 SAP Rfc</span><span class="sxs-lookup"><span data-stu-id="e7775-110">Operations on RFCs in SAP</span></span>](../../adapters-and-accelerators/adapter-sap/operations-on-rfcs-in-sap.md)  
  
-   [<span data-ttu-id="e7775-111">TRFCs SAP 中的作業</span><span class="sxs-lookup"><span data-stu-id="e7775-111">Operations on tRFCs in SAP</span></span>](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md)  
  
-   [<span data-ttu-id="e7775-112">SAP 中的 Bapi 的作業</span><span class="sxs-lookup"><span data-stu-id="e7775-112">Operations on BAPIs in SAP</span></span>](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md)  
  
-   [<span data-ttu-id="e7775-113">在 SAP Idoc 的作業</span><span class="sxs-lookup"><span data-stu-id="e7775-113">Operations on IDOCs in SAP</span></span>](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md)