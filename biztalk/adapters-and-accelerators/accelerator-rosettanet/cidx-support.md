---
title: CIDX 支援 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CIDX, procedures
- CIDX, about CIDX
- CIDX, Elemica Exchange Server Provider (ESP)
- CIDX, PIPs
- CIDX
- Elemica Exchange Server Provider (ESP)
- procedures [CIDX]
- PIPs, CIDX
ms.assetid: 58b75ad3-f6b9-47c0-8dbf-506a3eaf010b
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57500dc25e719d7ef693975b74850cbc04289dec
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997807"
---
# <a name="cidx-support"></a><span data-ttu-id="180d1-102">CIDX 支援</span><span class="sxs-lookup"><span data-stu-id="180d1-102">CIDX Support</span></span>
<span data-ttu-id="180d1-103">Microsoft[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]支援 CIDX （化學產業資料交換） XML 訊息交換。</span><span class="sxs-lookup"><span data-stu-id="180d1-103">Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] provides support for CIDX (Chemical Industry Data Exchange) XML message exchange.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="180d1-104"> 支援 CIDX Chem eStandards 2.0 和 3.0，這兩者都使用 RosettaNet 實作架構 (RNIF) 1.1 版。</span><span class="sxs-lookup"><span data-stu-id="180d1-104"> supports CIDX Chem eStandards versions 2.0 and 3.0, both of which use the RosettaNet Implementation Framework (RNIF) 1.1.</span></span>  
  
 <span data-ttu-id="180d1-105">[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 非同步簡單公開程序 (支援單向動作和雙向動作訊息) 會使用並傳送 CIDX 服務內容。</span><span class="sxs-lookup"><span data-stu-id="180d1-105">The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] asynchronous simple public processes (supporting single-action and double-action messages) consume and route CIDX service content.</span></span>  
  
 <span data-ttu-id="180d1-106">對於採用 CIDX PIP 的協議，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 將驗證訊息中的下列資訊：</span><span class="sxs-lookup"><span data-stu-id="180d1-106">For an agreement based on a CIDX PIP, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will validate the following in a message:</span></span>  
  
- <span data-ttu-id="180d1-107">僅 RNIF 1.1 版本</span><span class="sxs-lookup"><span data-stu-id="180d1-107">RNIF 1.1 version only</span></span>  
  
- <span data-ttu-id="180d1-108">無 0A1</span><span class="sxs-lookup"><span data-stu-id="180d1-108">No 0A1</span></span>  
  
- <span data-ttu-id="180d1-109">僅單向動作</span><span class="sxs-lookup"><span data-stu-id="180d1-109">Only Single Action</span></span>  
  
  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="180d1-110"> 不會防止您設定`Standard`程序組態為 「 CIDX 」 之後您已設定, 的屬性`0A1 agreement`會使用該設定檔為 （這不支援對 CIDX） 的 「 0A1 」 協議屬性。</span><span class="sxs-lookup"><span data-stu-id="180d1-110"> will not prevent you from setting the `Standard` property for a process configuration to "CIDX", after you have set the `0A1 agreement` property for an agreement that uses that profile to "0A1" (which is not supported for CIDX).</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="180d1-111"> 不會執行可能阻止此欄位交互驗證。</span><span class="sxs-lookup"><span data-stu-id="180d1-111"> does not perform the cross-field validation that would prevent this.</span></span>  
  
## <a name="applying-a-pip-to-a-cidx-implementation"></a><span data-ttu-id="180d1-112">將 PIP 套用至 CIDX 實作</span><span class="sxs-lookup"><span data-stu-id="180d1-112">Applying a PIP to a CIDX Implementation</span></span>  
 <span data-ttu-id="180d1-113">若要將 PIP 套用至 CIDX 實作，將`Standard`程序組態設定檔中的屬性**CIDX**。</span><span class="sxs-lookup"><span data-stu-id="180d1-113">To apply a PIP to a CIDX implementation, set the `Standard` property in the process configuration profile to **CIDX**.</span></span> <span data-ttu-id="180d1-114">完成之後，您將能夠輸入值的訊息標準 」、 「 標準版本 」 和 「 承載繫結識別碼。</span><span class="sxs-lookup"><span data-stu-id="180d1-114">After you have finished, you will be able to enter values for the Message standard, Standard version, and Payload binding ID.</span></span> <span data-ttu-id="180d1-115">您可以在 CIDX Chem eStandards 的規格中找到這些值。</span><span class="sxs-lookup"><span data-stu-id="180d1-115">You can find these values in the CIDX Chem eStandards specification.</span></span>  
  
## <a name="connecting-to-the-elemica-network"></a><span data-ttu-id="180d1-116">連線到 Elemica 網路</span><span class="sxs-lookup"><span data-stu-id="180d1-116">Connecting to the Elemica Network</span></span>  
 <span data-ttu-id="180d1-117">您可以讓 Microsoft 安裝[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]以連線到 Elemica [!INCLUDE[btsExchangeSvrNoVersion](../../includes/btsexchangesvrnoversion-md.md)] Provider (ESP)。</span><span class="sxs-lookup"><span data-stu-id="180d1-117">You can enable an installation of Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] to connect to the Elemica [!INCLUDE[btsExchangeSvrNoVersion](../../includes/btsexchangesvrnoversion-md.md)] Provider (ESP).</span></span> <span data-ttu-id="180d1-118">您可以使用 CIDX 訊息交換，透過 Elemica 網路買賣化學工業產品及管理供應鏈。</span><span class="sxs-lookup"><span data-stu-id="180d1-118">You can use the Elemica network for chemical-industry buying, selling, and supply-chain management using CIDX message exchange.</span></span>  
  
 <span data-ttu-id="180d1-119">您可以使用 Elemica Connectivity Pack 中的專案檔，自訂 [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] 以連線到 Elemica。</span><span class="sxs-lookup"><span data-stu-id="180d1-119">You customize [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] to connect to Elemica using project files in the Elemica Connectivity Pack.</span></span> <span data-ttu-id="180d1-120">您可以下載從 Connectivity Pack [ http://go.microsoft.com/fwlink/?LinkId=46195 ](http://go.microsoft.com/fwlink/?LinkId=46195)。</span><span class="sxs-lookup"><span data-stu-id="180d1-120">You can download the Connectivity Pack from [http://go.microsoft.com/fwlink/?LinkId=46195](http://go.microsoft.com/fwlink/?LinkId=46195).</span></span> <span data-ttu-id="180d1-121">詳細資訊，請參閱 MSDN 上的 < 連接到 Elemica 網路利用 BizTalk Accelerator for RosettaNet 3.0 > 技術白皮書[ http://go.microsoft.com/fwlink/?linkid=46539 ](http://go.microsoft.com/fwlink/?linkid=46539)。</span><span class="sxs-lookup"><span data-stu-id="180d1-121">For more information, see the “Connecting to the Elemica Network with BizTalk Accelerator for RosettaNet 3.0” white paper on MSDN at [http://go.microsoft.com/fwlink/?linkid=46539](http://go.microsoft.com/fwlink/?linkid=46539).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="180d1-122">《利用 BizTalk Accelerator for RosettaNet 3.0 連線至 Elemica 網路》白皮書 (英文) 中的資訊對 [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] 有效。</span><span class="sxs-lookup"><span data-stu-id="180d1-122">The information in the "Connecting to the Elemica Network with BizTalk Accelerator for RosettaNet 3.0" white paper is valid for [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)].</span></span>  
  
## <a name="cidx-procedures"></a><span data-ttu-id="180d1-123">CIDX 程序</span><span class="sxs-lookup"><span data-stu-id="180d1-123">CIDX Procedures</span></span>  
 <span data-ttu-id="180d1-124">下列章節說明如何設定 CIDX 訊息交換：</span><span class="sxs-lookup"><span data-stu-id="180d1-124">The following sections described how to set up CIDX message exchange:</span></span>  
  
-   [<span data-ttu-id="180d1-125">設定 CIDX eStandards 訊息交換</span><span class="sxs-lookup"><span data-stu-id="180d1-125">Setting Up CIDX eStandards Message Exchange</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md)  
  
-   [<span data-ttu-id="180d1-126">建立或編輯協議</span><span class="sxs-lookup"><span data-stu-id="180d1-126">Creating or Editing an Agreement</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)  
  
-   [<span data-ttu-id="180d1-127">匯入以 XSD 為基礎的 PIP</span><span class="sxs-lookup"><span data-stu-id="180d1-127">Importing an XSD-based PIP</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/importing-an-xsd-based-pip.md)  
  
## <a name="see-also"></a><span data-ttu-id="180d1-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="180d1-128">See Also</span></span>  
 <span data-ttu-id="180d1-129">[BizTalk Accelerator for RosettaNet 新增至 BizTalk Server](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="180d1-129">[What BizTalk Accelerator for RosettaNet Adds to BizTalk Server](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md) </span></span>  
 [<span data-ttu-id="180d1-130">CIDX 訊息標準</span><span class="sxs-lookup"><span data-stu-id="180d1-130">CIDX Messaging Standards</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/cidx-messaging-standards.md)