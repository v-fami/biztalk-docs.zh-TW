---
title: 開發 BizTalk 應用程式使用 Siebel 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 08/02/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BizTalk applications, developing
- developing, BizTalk applications
- CBR
- Content-Based Routing
ms.assetid: 1a2a9765-305c-44b2-aed7-5437725e4c19
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8267c07027d9994b0115ebaf49fde96e76f2716
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22221926"
---
# <a name="develop-biztalk-applications-using-the-siebel-adapter"></a><span data-ttu-id="d0513-102">開發 BizTalk 應用程式使用 Siebel 配接器</span><span class="sxs-lookup"><span data-stu-id="d0513-102">Develop BizTalk applications using the Siebel adapter</span></span>

## <a name="overview"></a><span data-ttu-id="d0513-103">概觀</span><span class="sxs-lookup"><span data-stu-id="d0513-103">Overview</span></span>
<span data-ttu-id="d0513-104">建立 BizTalk 專案中的開發 BizTalk 應用程式牽涉到[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]和使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]產生 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="d0513-104">Developing BizTalk applications involves creating a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to generate XML schema.</span></span> <span data-ttu-id="d0513-105">一旦您已經產生結構描述，您可以使用以內容為基礎的路由 (CBR)，或建立 BizTalk 協調流程傳送和接收符合產生結構描述的訊息。</span><span class="sxs-lookup"><span data-stu-id="d0513-105">Once you have generated the schema, you can either use Content-Based Routing (CBR) or create BizTalk orchestrations to send and receive messages that conform to the generated schema.</span></span>  
  
 <span data-ttu-id="d0513-106">CBR 可用在案例中傳送到 Siebel 系統的訊息不需要任何大量的處理。</span><span class="sxs-lookup"><span data-stu-id="d0513-106">CBR can be used in scenarios where the messages being sent to a Siebel system do not require any intensive processing.</span></span> <span data-ttu-id="d0513-107">比方說，如果您知道接收埠會接收僅特定類型的訊息，您可以加入篩選條件要比對篩選條件運算式至傳送埠將訊息路由傳送埠。</span><span class="sxs-lookup"><span data-stu-id="d0513-107">For example, if you know that the receive port will be receiving messages only of a certain type, you can add a filter to the send port to route the messages matching the filter expression to the send port.</span></span>  
  
 <span data-ttu-id="d0513-108">在 BizTalk 協調流程，建立傳送和接收埠以傳送和接收訊息的[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，這會將訊息傳送至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d0513-108">In BizTalk orchestrations, you create send and receive ports to send and receive messages to and from the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], which in turn sends the messages to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="d0513-109">本節提供使用 BizTalk 協調流程使用 Siebel 系統上執行作業的相關資訊[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d0513-109">This section provides information about using BizTalk orchestrations to perform operations on a Siebel system using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span> <span data-ttu-id="d0513-110">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]接著會採用[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，能夠與 WCF 繫結互動。</span><span class="sxs-lookup"><span data-stu-id="d0513-110">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] in turn uses the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)] that can interact with a WCF binding.</span></span>  

## <a name="before-you-begin"></a><span data-ttu-id="d0513-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="d0513-111">Before you begin</span></span>  

* <span data-ttu-id="d0513-112">若要使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]與 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，一律將**EnableBizTalkCompatibilityMode**內容繫結至**True**。</span><span class="sxs-lookup"><span data-stu-id="d0513-112">To use the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], always set the **EnableBizTalkCompatibilityMode** binding property to **True**.</span></span> <span data-ttu-id="d0513-113">如需步驟，請參閱[siebel 設定繫結屬性](../../adapters-and-accelerators/adapter-siebel/configure-the-binding-properties-for-siebel.md)。</span><span class="sxs-lookup"><span data-stu-id="d0513-113">For the steps, see [Configure the binding properties for Siebel](../../adapters-and-accelerators/adapter-siebel/configure-the-binding-properties-for-siebel.md).</span></span>
  
* <span data-ttu-id="d0513-114">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]自動未列在 BizTalk Server 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="d0513-114">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] shipped with [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] is not automatically listed in the BizTalk Server Administration console.</span></span> <span data-ttu-id="d0513-115">這是因為[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]是 WCF 自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="d0513-115">This is because the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is a WCF custom binding.</span></span> 

* <span data-ttu-id="d0513-116">產生中繼資料，請使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d0513-116">To generate metadata, use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].</span></span> <span data-ttu-id="d0513-117">請勿使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d0513-117">Do not use the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span> <span data-ttu-id="d0513-118">如需使用指示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，請參閱[取得 Visual Studio 中的 Siebel 作業的中繼資料](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="d0513-118">For instructions on using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], see [Get Metadata for Siebel Operations in Visual Studio](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md).</span></span>   

  
## <a name="see-also"></a><span data-ttu-id="d0513-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0513-119">See Also</span></span>  
[<span data-ttu-id="d0513-120">開發 Siebel 應用程式</span><span class="sxs-lookup"><span data-stu-id="d0513-120">Develop your Siebel applications</span></span>](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)