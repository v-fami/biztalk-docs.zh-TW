---
title: "BizTalk Server 的 RosettaNet 私用程序教學課程的必要條件 |Microsoft 文件"
description: "若要逐步執行 RosettaNet 加速器 (BTARN)，以在 BizTalk Server 中的私用程序教學課程的必要條件"
caps.latest.revision: "7"
author: MandiOhlinger
manager: anneta
ms.custom: 
ms.date: 08/09/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89631ce3-f5af-4d30-b22f-6d20f595295f
ms.author: mandia
ms.openlocfilehash: 4da7190c7212f74a90689ca403d899eb1a849cc5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="prepare-for-the-private-process-tutorial"></a><span data-ttu-id="708c8-103">準備私用程序教學課程</span><span class="sxs-lookup"><span data-stu-id="708c8-103">Prepare for the Private Process tutorial</span></span>

## <a name="prerequisites"></a><span data-ttu-id="708c8-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="708c8-104">Prerequisites</span></span>
<span data-ttu-id="708c8-105">再開始本教學課程：</span><span class="sxs-lookup"><span data-stu-id="708c8-105">Before starting the tutorial:</span></span>
  
-   <span data-ttu-id="708c8-106">執行 BizTalk Server 的完整安裝和[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]兩部電腦上。</span><span class="sxs-lookup"><span data-stu-id="708c8-106">Do a full installation of BizTalk Server and [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] on two computers.</span></span> <span data-ttu-id="708c8-107">如需詳細資訊，請參閱[安裝及設定](install-configure-biztalk-accelerator-for-rosettanet.md)。</span><span class="sxs-lookup"><span data-stu-id="708c8-107">For more information, see [Install and configure](install-configure-biztalk-accelerator-for-rosettanet.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="708c8-108">請確定您完全設定 RosettaNet 加速器，包括啟動 BTARN 協調流程。</span><span class="sxs-lookup"><span data-stu-id="708c8-108">Be sure that you fully configure the RosettaNet accelerator, including starting the BTARN orchestrations.</span></span> <span data-ttu-id="708c8-109">請參閱[安裝及設定](install-configure-biztalk-accelerator-for-rosettanet.md)。</span><span class="sxs-lookup"><span data-stu-id="708c8-109">See [Install and configure](install-configure-biztalk-accelerator-for-rosettanet.md).</span></span> <span data-ttu-id="708c8-110">您也必須新增[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]虛擬目錄 （包含 btarnhttpreceive） 至 Microsoft Windows® SharePoint™ Services 受管理的路徑排除清單。</span><span class="sxs-lookup"><span data-stu-id="708c8-110">You may also have to add the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] virtual directories (including btarnhttpreceive) to the Microsoft Windows® SharePoint™ Services managed path exclusion list.</span></span> 
  
-   <span data-ttu-id="708c8-111">本教學課程會使用兩台電腦模擬真實世界的實例，而不是搭配回送協議使用一台電腦。</span><span class="sxs-lookup"><span data-stu-id="708c8-111">This tutorial simulates a real-world scenario by using two computers instead of a single computer with a loop-back agreement.</span></span> <span data-ttu-id="708c8-112">每當本教學課程提到電腦名稱時，都會使用預留位置做為電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="708c8-112">Whenever this tutorial uses computer names, it uses a placeholder as the computer name.</span></span> <span data-ttu-id="708c8-113">該預留位置取代為您選擇的實際電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="708c8-113">Replace that placeholder with the actual computer name you chose.</span></span> <span data-ttu-id="708c8-114">例如，如果電腦執行您 Contoso 解決方案名為**Contoso**，在教學課程中的任何取代\\ \\< contoso**_** *電腦*> 具有該電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="708c8-114">For example, if the computer that is running your Contoso solution is named **Contoso**, replace any occurrences in the tutorial of \\\\<contoso**_***computer*> with that computer name.</span></span>  
  
 <span data-ttu-id="708c8-115">本教學課程會在 Contoso 和 Fabrikam 之間，透過使用憑證促成安全通訊。</span><span class="sxs-lookup"><span data-stu-id="708c8-115">This tutorial promotes secure communication through certificates between Contoso and Fabrikam.</span></span> <span data-ttu-id="708c8-116">您必須產生任何憑證，您需要，並在個別電腦上安裝它們。</span><span class="sxs-lookup"><span data-stu-id="708c8-116">You must generate any certificates you require, and install them on the respective computers.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="708c8-117">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="708c8-117">Next steps</span></span>
  
-   [<span data-ttu-id="708c8-118">還原 Contoso 資料庫</span><span class="sxs-lookup"><span data-stu-id="708c8-118">Restoring the Contoso Database</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/restoring-the-contoso-database.md)  
  
-   [<span data-ttu-id="708c8-119">產生並啟用憑證</span><span class="sxs-lookup"><span data-stu-id="708c8-119">Generating and Enabling Certificates</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/generating-and-enabling-certificates.md)