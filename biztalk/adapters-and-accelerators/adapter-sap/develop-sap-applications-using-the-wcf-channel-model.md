---
title: 開發使用 WCF 通道模型的 SAP 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF channel model, developing applications by using
ms.assetid: 1ce70c8b-5eeb-4585-97af-b0a7b4398dac
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2bce6ad43b6efce111a2801ba7a5b44e73dce1a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013127"
---
# <a name="develop-sap-applications-using-the-wcf-channel-model"></a><span data-ttu-id="25584-102">開發使用 WCF 通道模型的 SAP 應用程式</span><span class="sxs-lookup"><span data-stu-id="25584-102">Develop SAP applications using the WCF Channel Model</span></span>
<span data-ttu-id="25584-103">您可以使用[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]通道模型使用[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]直接透過通道執行個體的 SAP 繫結傳送 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="25584-103">You can use the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] channel model to consume the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] by sending XML messages directly over a channel instance created with the SAP Binding.</span></span>  
  
 <span data-ttu-id="25584-104">透過使用強型別類別與 WCF 服務模型會公開的方法中使用 WCF 通道模型的優點之一是通道模型提供更精密地控制您執行 SAP 系統的作業。</span><span class="sxs-lookup"><span data-stu-id="25584-104">One advantage of using the WCF channel model over using the strongly-typed classes and methods that the WCF service model exposes is that the channel model provides more fine-grained control over the operations that you perform on the SAP system.</span></span> <span data-ttu-id="25584-105">為什麼？</span><span class="sxs-lookup"><span data-stu-id="25584-105">Why?</span></span> <span data-ttu-id="25584-106">WCF 通道模型中您可以直接控制您透過通道傳送訊息的內容。</span><span class="sxs-lookup"><span data-stu-id="25584-106">In the WCF channel model you directly control the contents of the messages that you send over the channel.</span></span>  
  
 <span data-ttu-id="25584-107">透過 WCF 服務模型的 WCF 通道模型提供的另一個主要優點是對資料流的更完整支援。</span><span class="sxs-lookup"><span data-stu-id="25584-107">Another key advantage that the WCF channel model provides over the WCF service model is more comprehensive support for data streaming.</span></span> <span data-ttu-id="25584-108">使用 WCF 通道模型，您可以執行：</span><span class="sxs-lookup"><span data-stu-id="25584-108">By using the WCF channel model you can perform:</span></span>  
  
- <span data-ttu-id="25584-109">您的程式碼與配接器之間交換的所有訊息資料流都處理訊息的節點。</span><span class="sxs-lookup"><span data-stu-id="25584-109">Message node streaming on all messages exchanged between your code and the adapter.</span></span>  
  
- <span data-ttu-id="25584-110">資料流處理的 SendIdoc 和 ReceiveIdoc 作業訊息節點值。</span><span class="sxs-lookup"><span data-stu-id="25584-110">Message node-value streaming on the SendIdoc and ReceiveIdoc operations.</span></span>  
  
  <span data-ttu-id="25584-111">這是因為 WCF 通道模型中您直接控制如何在您傳送至配接器的訊息上提供訊息內文，以及您如何使用訊息本文上您從配接器接收的訊息。</span><span class="sxs-lookup"><span data-stu-id="25584-111">This is because in the WCF channel model you directly control how you provide the message body on messages that you send to the adapter and how you consume the message body on messages that you receive from the adapter.</span></span>  
  
  <span data-ttu-id="25584-112">相反地，配接器不提供支援的 WCF 服務模型中的串流。</span><span class="sxs-lookup"><span data-stu-id="25584-112">In contrast, the adapter provides no support for streaming in the WCF service model.</span></span> <span data-ttu-id="25584-113">因為在 WCF 服務模型中，WCF 執行階段序列化和還原序列化其 XML 與 managed 程式碼物件的表示法之間的訊息，會使用完整的記憶體中複本的每個您配接器與交換的訊息。</span><span class="sxs-lookup"><span data-stu-id="25584-113">Because, in the WCF service model, the WCF runtime serializes and deserializes messages between their XML and managed code object representations, a complete in-memory copy of each message that you exchange with the adapter is made.</span></span>  
  
  <span data-ttu-id="25584-114">本主題中的各節說明如何執行作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]使用 WCF 通道模型。</span><span class="sxs-lookup"><span data-stu-id="25584-114">The sections in this topic explain how to perform operations on the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] by using the WCF channel model.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="25584-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="25584-115">In This Section</span></span>  
  
-   [<span data-ttu-id="25584-116">SAP 配接器使用 WCF 通道模型概觀</span><span class="sxs-lookup"><span data-stu-id="25584-116">Overview of the WCF Channel Model with the SAP Adapter</span></span>](../../adapters-and-accelerators/adapter-sap/overview-of-the-wcf-channel-model-with-the-sap-adapter.md)  
  
-   [<span data-ttu-id="25584-117">建立通道，使用 SAP</span><span class="sxs-lookup"><span data-stu-id="25584-117">Create a channel using SAP</span></span>](../../adapters-and-accelerators/adapter-sap/create-a-channel-using-sap.md)  
  
-   [<span data-ttu-id="25584-118">使用 WCF 通道模型叫用 SAP 系統上的作業</span><span class="sxs-lookup"><span data-stu-id="25584-118">Invoking Operations on the SAP System by Using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md)  
  
-   [<span data-ttu-id="25584-119">從 SAP 系統接收輸入的作業，使用 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="25584-119">Receiving Inbound Operations from the SAP System by Using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md) 
  
-   [<span data-ttu-id="25584-120">資料流中使用 WCF 通道模型的 SAP 的一般檔案 Idoc</span><span class="sxs-lookup"><span data-stu-id="25584-120">Streaming Flat-File IDOCs in SAP using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md)