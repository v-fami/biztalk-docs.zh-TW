---
title: "BizTalk Server 的 RosettaNet 雙向動作教學課程的必要條件 |Microsoft 文件"
description: "若要逐步執行 BizTalk Server 中的 RosettaNet 加速器 (BTARN) 的雙向動作教學課程的必要條件"
ms.custom: 
ms.date: 08/09/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1ce8a122-cd16-450a-84bd-bb6beee7af40
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87e2750a16d2c65b5838b6d61f27cbd2b2ff9885
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="prepare-for-the-double-action-tutorial"></a><span data-ttu-id="7ea62-103">準備進行雙向動作教學課程</span><span class="sxs-lookup"><span data-stu-id="7ea62-103">Prepare for the Double Action tutorial</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7ea62-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="7ea62-104">Prerequisites</span></span>
<span data-ttu-id="7ea62-105">再開始本教學課程：</span><span class="sxs-lookup"><span data-stu-id="7ea62-105">Before starting the tutorial:</span></span>
  
-   <span data-ttu-id="7ea62-106">執行 BizTalk Server 的完整安裝和[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]兩部電腦上。</span><span class="sxs-lookup"><span data-stu-id="7ea62-106">Do a full installation of BizTalk Server and [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] on two computers.</span></span> <span data-ttu-id="7ea62-107">如需詳細資訊，請參閱[安裝及設定](install-configure-biztalk-accelerator-for-rosettanet.md)。</span><span class="sxs-lookup"><span data-stu-id="7ea62-107">For more information, see [Install and configure](install-configure-biztalk-accelerator-for-rosettanet.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="7ea62-108">請確定您完全設定 RosettaNet 加速器，包括啟動 BTARN 協調流程。</span><span class="sxs-lookup"><span data-stu-id="7ea62-108">Be sure that you fully configure the RosettaNet accelerator, including starting the BTARN orchestrations.</span></span> <span data-ttu-id="7ea62-109">請參閱[安裝及設定](install-configure-biztalk-accelerator-for-rosettanet.md)。</span><span class="sxs-lookup"><span data-stu-id="7ea62-109">See [Install and configure](install-configure-biztalk-accelerator-for-rosettanet.md).</span></span>
  
-   <span data-ttu-id="7ea62-110">本教學課程會使用兩台電腦模擬真實世界的實例，而不是搭配回送協議使用一台電腦。</span><span class="sxs-lookup"><span data-stu-id="7ea62-110">This tutorial simulates a real-world scenario by using two computers instead of a single computer with a loopback agreement.</span></span> <span data-ttu-id="7ea62-111">每當本教學課程提到電腦名稱時，都會使用預留位置。</span><span class="sxs-lookup"><span data-stu-id="7ea62-111">Whenever this tutorial uses computer names, it uses a placeholder.</span></span> <span data-ttu-id="7ea62-112">該預留位置取代為您選擇的實際電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="7ea62-112">Replace that placeholder with the actual computer name you chose.</span></span> <span data-ttu-id="7ea62-113">例如，如果電腦執行您 Contoso 解決方案名為**Contoso**，在教學課程中的任何取代\\ \\< contoso**_** *電腦*> 具有該電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="7ea62-113">For example, if the computer that is running your Contoso solution is named **Contoso**, replace any occurrences in the tutorial of \\\\<contoso**_***computer*> with that computer name.</span></span>  
  
-   <span data-ttu-id="7ea62-114">本教學課程會在 Contoso 和 Fabrikam 之間，透過使用憑證促成安全通訊。</span><span class="sxs-lookup"><span data-stu-id="7ea62-114">This tutorial promotes secure communication through certificates between Contoso and Fabrikam.</span></span> <span data-ttu-id="7ea62-115">您必須產生任何憑證，您需要，並在其各自的電腦上安裝它們。</span><span class="sxs-lookup"><span data-stu-id="7ea62-115">You must generate any certificates you require, and install them on their respective computers.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7ea62-116">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="7ea62-116">Next steps</span></span> 
  
-   [<span data-ttu-id="7ea62-117">步驟 1： 建立憑證授權單位</span><span class="sxs-lookup"><span data-stu-id="7ea62-117">Step 1: Creating a Certification Authority</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-1-creating-a-certification-authority.md)  
  
-   [<span data-ttu-id="7ea62-118">步驟 2： 建立公開憑證與私用憑證</span><span class="sxs-lookup"><span data-stu-id="7ea62-118">Step 2: Creating Public and Private Certificates</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-2-creating-public-and-private-certificates.md)  
  
-   [<span data-ttu-id="7ea62-119">步驟 3： 匯入公開憑證與私用憑證</span><span class="sxs-lookup"><span data-stu-id="7ea62-119">Step 3: Importing Public and Private Certificates</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-3-importing-public-and-private-certificates.md)  
  
-   [<span data-ttu-id="7ea62-120">步驟 4： 啟用安全通訊端在 IIS 中的圖層</span><span class="sxs-lookup"><span data-stu-id="7ea62-120">Step 4: Enabling Secure Sockets Layer in IIS</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-4-enabling-secure-sockets-layer-in-iis.md)