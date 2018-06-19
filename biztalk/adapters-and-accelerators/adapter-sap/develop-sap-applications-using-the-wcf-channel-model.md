---
title: 開發 SAP 應用程式使用 WCF 通道模型 |Microsoft 文件
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
ms.openlocfilehash: 13015cb042d26c946abfa3c99a4f67034b8d9708
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216022"
---
# <a name="develop-sap-applications-using-the-wcf-channel-model"></a><span data-ttu-id="fa319-102">開發 SAP 應用程式使用 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="fa319-102">Develop SAP applications using the WCF Channel Model</span></span>
<span data-ttu-id="fa319-103">您可以使用[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]使用通道模型[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]直接透過 SAP 繫結的通道執行個體傳送 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="fa319-103">You can use the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] channel model to consume the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] by sending XML messages directly over a channel instance created with the SAP Binding.</span></span>  
  
 <span data-ttu-id="fa319-104">使用 WCF 通道模型，透過使用強型別類別和方法的 WCF 服務模型會公開的其中一個優點是通道模型提供更細微的控制，透過您在 SAP 系統執行的作業。</span><span class="sxs-lookup"><span data-stu-id="fa319-104">One advantage of using the WCF channel model over using the strongly-typed classes and methods that the WCF service model exposes is that the channel model provides more fine-grained control over the operations that you perform on the SAP system.</span></span> <span data-ttu-id="fa319-105">為什麼？</span><span class="sxs-lookup"><span data-stu-id="fa319-105">Why?</span></span> <span data-ttu-id="fa319-106">WCF 通道模型中直接控制您透過通道傳送訊息的內容。</span><span class="sxs-lookup"><span data-stu-id="fa319-106">In the WCF channel model you directly control the contents of the messages that you send over the channel.</span></span>  
  
 <span data-ttu-id="fa319-107">WCF 通道模型提供的 WCF 服務模型透過另一個主要優點是更廣泛支援資料流。</span><span class="sxs-lookup"><span data-stu-id="fa319-107">Another key advantage that the WCF channel model provides over the WCF service model is more comprehensive support for data streaming.</span></span> <span data-ttu-id="fa319-108">使用 WCF 通道模型，您可以執行：</span><span class="sxs-lookup"><span data-stu-id="fa319-108">By using the WCF channel model you can perform:</span></span>  
  
-   <span data-ttu-id="fa319-109">您的程式碼與配接器之間交換的所有訊息資料流都處理的訊息節點。</span><span class="sxs-lookup"><span data-stu-id="fa319-109">Message node streaming on all messages exchanged between your code and the adapter.</span></span>  
  
-   <span data-ttu-id="fa319-110">資料流處理的 SendIdoc 和 ReceiveIdoc 作業訊息節點值。</span><span class="sxs-lookup"><span data-stu-id="fa319-110">Message node-value streaming on the SendIdoc and ReceiveIdoc operations.</span></span>  
  
 <span data-ttu-id="fa319-111">這是因為 WCF 通道模型中您直接控制如何在您傳送至配接器的訊息上提供訊息內文和使用您從配接器接收的訊息上的訊息本文的方式。</span><span class="sxs-lookup"><span data-stu-id="fa319-111">This is because in the WCF channel model you directly control how you provide the message body on messages that you send to the adapter and how you consume the message body on messages that you receive from the adapter.</span></span>  
  
 <span data-ttu-id="fa319-112">相反地，配接器不提供支援的 WCF 服務模型中的資料流。</span><span class="sxs-lookup"><span data-stu-id="fa319-112">In contrast, the adapter provides no support for streaming in the WCF service model.</span></span> <span data-ttu-id="fa319-113">因為在 WCF 服務模型中，WCF 執行階段序列化和還原序列化的 XML 和 managed 程式碼的物件表示法之間的訊息，進行完整的記憶體中複本的每個您配接器與交換的訊息。</span><span class="sxs-lookup"><span data-stu-id="fa319-113">Because, in the WCF service model, the WCF runtime serializes and deserializes messages between their XML and managed code object representations, a complete in-memory copy of each message that you exchange with the adapter is made.</span></span>  
  
 <span data-ttu-id="fa319-114">本主題中的各節說明如何執行作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]使用 WCF 通道模型。</span><span class="sxs-lookup"><span data-stu-id="fa319-114">The sections in this topic explain how to perform operations on the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] by using the WCF channel model.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fa319-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="fa319-115">In This Section</span></span>  
  
-   [<span data-ttu-id="fa319-116">SAP 配接器的 WCF 通道模型概觀</span><span class="sxs-lookup"><span data-stu-id="fa319-116">Overview of the WCF Channel Model with the SAP Adapter</span></span>](../../adapters-and-accelerators/adapter-sap/overview-of-the-wcf-channel-model-with-the-sap-adapter.md)  
  
-   [<span data-ttu-id="fa319-117">建立使用 SAP 的通道</span><span class="sxs-lookup"><span data-stu-id="fa319-117">Create a channel using SAP</span></span>](../../adapters-and-accelerators/adapter-sap/create-a-channel-using-sap.md)  
  
-   [<span data-ttu-id="fa319-118">叫用 SAP 系統上的作業使用的 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="fa319-118">Invoking Operations on the SAP System by Using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md)  
  
-   [<span data-ttu-id="fa319-119">接收從 SAP 系統的輸入的作業使用的 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="fa319-119">Receiving Inbound Operations from the SAP System by Using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md) 
  
-   [<span data-ttu-id="fa319-120">使用 WCF 通道模型的 SAP 中的資料流處理一般檔案 Idoc</span><span class="sxs-lookup"><span data-stu-id="fa319-120">Streaming Flat-File IDOCs in SAP using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md)