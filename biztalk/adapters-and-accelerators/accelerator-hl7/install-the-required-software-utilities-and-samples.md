---
title: 安裝必要的軟體、 公用程式及範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de0cb89d-08bd-48ec-a149-8929e2608df8
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45f92f4cc994b4139c1c33423cc7a94c9072e226
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36965903"
---
# <a name="install-the-required-software-utilities-and-samples"></a><span data-ttu-id="cede4-102">安裝必要的軟體、 公用程式及範例</span><span class="sxs-lookup"><span data-stu-id="cede4-102">Install the Required Software, Utilities, and Samples</span></span>
<span data-ttu-id="cede4-103">本教學課程需要 Microsoft Windows Server 和自訂的 Microsoft[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]包含 MLLP 測試工具的安裝。</span><span class="sxs-lookup"><span data-stu-id="cede4-103">This tutorial requires Microsoft Windows Server, and a custom Microsoft [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] installation that includes the MLLP Test Tools.</span></span> <span data-ttu-id="cede4-104">此外，您應該先熟悉[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]在 Microsoft 的開發[!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)]並[了解 HL7 加速器以及可用的 BizTalk 工具](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md)。</span><span class="sxs-lookup"><span data-stu-id="cede4-104">Additionally, you should be familiar with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] development in Microsoft [!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)] and [Learn the HL7 accelerator and the BizTalk tools available](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md).</span></span>
  
 <span data-ttu-id="cede4-105">您必須具備下列公用程式和安裝在您的電腦上的範例：</span><span class="sxs-lookup"><span data-stu-id="cede4-105">You must have the following utilities and samples installed on your computer:</span></span>  
  
- <span data-ttu-id="cede4-106">**MllpSend 工具**</span><span class="sxs-lookup"><span data-stu-id="cede4-106">**MllpSend Tool**</span></span>  
  
   <span data-ttu-id="cede4-107">此命令列公用程式會傳送一則訊息透過最少的較低層通訊協定 (MLLP) 通訊協定來 MLLP 接收位置。</span><span class="sxs-lookup"><span data-stu-id="cede4-107">This command-line utility sends a message over the Minimal Lower Layer Protocol (MLLP) protocol to an MLLP receive location.</span></span> <span data-ttu-id="cede4-108">您可以使用它來測試您教學課程的結果。</span><span class="sxs-lookup"><span data-stu-id="cede4-108">You use it to test your tutorial results.</span></span> <span data-ttu-id="cede4-109">如需詳細資訊，請參閱 < [MllpSend 工具](../../adapters-and-accelerators/accelerator-hl7/mllpsend-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="cede4-109">For more information, see [MllpSend Tool](../../adapters-and-accelerators/accelerator-hl7/mllpsend-tool.md).</span></span>  
  
- <span data-ttu-id="cede4-110">**MllpPReceive 工具**</span><span class="sxs-lookup"><span data-stu-id="cede4-110">**MllpPReceive Tool**</span></span>  
  
   <span data-ttu-id="cede4-111">此命令列公用程式會透過 MLLP 通訊協定，做為接收位置接聽程式接收訊息。</span><span class="sxs-lookup"><span data-stu-id="cede4-111">This command-line utility receives messages over the MLLP protocol, serving as a receive-location listener.</span></span> <span data-ttu-id="cede4-112">您可以使用它來測試您教學課程的結果，顯示訊息和接收的通知。</span><span class="sxs-lookup"><span data-stu-id="cede4-112">You use it to test your tutorial results, displaying messages and acknowledgments received.</span></span> <span data-ttu-id="cede4-113">如需詳細資訊，請參閱 < [MllpReceive 工具](../../adapters-and-accelerators/accelerator-hl7/mllpreceive-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="cede4-113">For more information, see [MllpReceive Tool](../../adapters-and-accelerators/accelerator-hl7/mllpreceive-tool.md).</span></span>  
  
- <span data-ttu-id="cede4-114">**範例應用程式接受 ACK.txt**</span><span class="sxs-lookup"><span data-stu-id="cede4-114">**Sample Application Accept ACK.txt**</span></span>  
  
   <span data-ttu-id="cede4-115">此範例檔案包含文字的應用程式接受通知訊息。</span><span class="sxs-lookup"><span data-stu-id="cede4-115">This sample file contains the text of an application-accept acknowledgment message.</span></span> <span data-ttu-id="cede4-116">此範例適用於 MllpReceive 工具，可接收並顯示訊息，然後送回 st2 範例檔案中。</span><span class="sxs-lookup"><span data-stu-id="cede4-116">The sample works with the MllpReceive tool, which receives and displays messages, then sends back the acknowledgment(s) in the sample file.</span></span>  
  
  <span data-ttu-id="cede4-117">您需要安裝兩個工具和範例檔案，藉由使用 BTAHL7 自訂安裝程序。</span><span class="sxs-lookup"><span data-stu-id="cede4-117">You need to install the two tools and the sample file by using the BTAHL7 Custom installation process.</span></span> <span data-ttu-id="cede4-118">一般安裝程序不會安裝這些工具。</span><span class="sxs-lookup"><span data-stu-id="cede4-118">The Typical installation process does not install these tools.</span></span> <span data-ttu-id="cede4-119">若要安裝這些工具，請在執行 BTAHL7 自訂安裝中，**自訂安裝**畫面上，選取**MLLP 測試工具**從**配接器**資料夾，然後選取**測試執行個體**從**成品**資料夾。</span><span class="sxs-lookup"><span data-stu-id="cede4-119">To install these tools, run the BTAHL7 custom installation, at the **Custom Setup** screen, select **MLLP Test Tool** from the **Adapter** folder, and select **Test Instances** from the **Artifacts** folder.</span></span> <span data-ttu-id="cede4-120">如需詳細資訊，請參閱 <<c0> [ 安裝 BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md)。</span><span class="sxs-lookup"><span data-stu-id="cede4-120">For more information, see [Install BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cede4-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cede4-121">See Also</span></span>  
 [<span data-ttu-id="cede4-122">準備使用批次處理教學課程</span><span class="sxs-lookup"><span data-stu-id="cede4-122">Preparing to Use the Batching Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-batching-tutorial.md)