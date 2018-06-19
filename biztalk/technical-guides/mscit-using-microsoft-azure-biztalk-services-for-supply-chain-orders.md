---
title: MSCIT： 使用 Microsoft Azure BizTalk 服務的供應鏈訂單 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 22091261-cd17-45b2-8746-dc174b52dcff
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6a1609be7326db4988d31d51597cde3fd280227
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22299214"
---
# <a name="mscit-using-microsoft-azure-biztalk-services-for-supply-chain-orders"></a><span data-ttu-id="28fef-102">供應鏈訂單 MSCIT： 使用 Microsoft Azure BizTalk 服務</span><span class="sxs-lookup"><span data-stu-id="28fef-102">MSCIT: Using Microsoft Azure BizTalk Services for Supply Chain Orders</span></span>
<span data-ttu-id="28fef-103">**Microsoft 裝置 （& s) Studios： 使用 Microsoft Azure BizTalk 服務的供應鏈訂單**</span><span class="sxs-lookup"><span data-stu-id="28fef-103">**Microsoft Devices & Studios: Using Microsoft Azure BizTalk Services for Supply Chain Orders**</span></span>  
  
 <span data-ttu-id="28fef-104">BizTalk 技術文章</span><span class="sxs-lookup"><span data-stu-id="28fef-104">BizTalk Technical Article</span></span>  
  
 <span data-ttu-id="28fef-105">**作者：** Anil Kongari (Microsoft)，Dipti Sharma (Microsoft)、 Mandi Ohlinger (Microsoft)</span><span class="sxs-lookup"><span data-stu-id="28fef-105">**Writer:** Anil Kongari (Microsoft), Dipti Sharma (Microsoft), Mandi Ohlinger (Microsoft)</span></span>  
  
 <span data-ttu-id="28fef-106">**技術校閱：** Anil Kongari (Microsoft)、 Hariharan Sundaram (Microsoft)、 Dipti Sharma (Microsoft)、 Heena Parmar (Microsoft)</span><span class="sxs-lookup"><span data-stu-id="28fef-106">**Technical Reviewers:** Anil Kongari (Microsoft), Hariharan Sundaram (Microsoft), Dipti Sharma (Microsoft), Heena Parmar (Microsoft)</span></span>  
  
 <span data-ttu-id="28fef-107">**發行日期：** 2013 年 10 月</span><span class="sxs-lookup"><span data-stu-id="28fef-107">**Published:** October 2013</span></span>  
  
 <span data-ttu-id="28fef-108">**適用於：** Microsoft Azure BizTalk 服務 (MABS) 和 BizTalk Server 2013</span><span class="sxs-lookup"><span data-stu-id="28fef-108">**Applies To:** Microsoft Azure BizTalk Services (MABS) and BizTalk Server 2013</span></span>  
  
 <span data-ttu-id="28fef-109">**摘要：** 製造、 供應鏈和資訊服務 (MSCIS) 群組是在 Microsoft 全域供應鏈管理群組。</span><span class="sxs-lookup"><span data-stu-id="28fef-109">**Summary:** The Manufacturing, Supply Chain, and Information Services (MSCIS) group is a Global Supply Chain Management group at Microsoft.</span></span> <span data-ttu-id="28fef-110">每年，Microsoft 會啟動新的產品。</span><span class="sxs-lookup"><span data-stu-id="28fef-110">Every year, Microsoft launches new products.</span></span> <span data-ttu-id="28fef-111">MSCIS 會負責將這些新產品上市。</span><span class="sxs-lookup"><span data-stu-id="28fef-111">MSCIS is responsible for bringing these new products to market.</span></span> <span data-ttu-id="28fef-112">若要支援這些產品，新的夥伴會新增至供應鏈，包括供應商，製造商、 散發者、 零售商、 服務中心、 承運業者，等等。</span><span class="sxs-lookup"><span data-stu-id="28fef-112">To support these products, new partners are added to the Supply Chain, including Supplier, Manufacturer, Distributor, Retailer, Service Center, Carrier, and so on.</span></span>  
  
 <span data-ttu-id="28fef-113">每年增加的交易夥伴數目。</span><span class="sxs-lookup"><span data-stu-id="28fef-113">The number of partner transactions increases yearly.</span></span> <span data-ttu-id="28fef-114">在高負載期間有輸送量與相關的問題。</span><span class="sxs-lookup"><span data-stu-id="28fef-114">During high load, there are issues related to throughput.</span></span> <span data-ttu-id="28fef-115">提供鏈結 BizTalk 中樞處理更多的交易 （增加的磁碟區），同時終端系統或協力廠商系統不能保持同步。</span><span class="sxs-lookup"><span data-stu-id="28fef-115">While the Supply Chain BizTalk hub processes more transactions (increased volume), the end system or partner system is not able to keep up.</span></span>  
  
 <span data-ttu-id="28fef-116">目前的挑戰是尖峰銷售準備企業對企業 (B2B) 系統。</span><span class="sxs-lookup"><span data-stu-id="28fef-116">The current challenge is to prepare the business-to-business (B2B) systems for peak sales.</span></span> <span data-ttu-id="28fef-117">在 Technology Adoption Program (TAP)，MSCIS 探索平台即服務 (PaaS) 使用 Microsoft Azure BizTalk 服務 (MABS)。</span><span class="sxs-lookup"><span data-stu-id="28fef-117">As part of Technology Adoption Program (TAP), MSCIS is exploring Platform as a Service (PaaS) using Microsoft Azure BizTalk Services (MABS).</span></span> <span data-ttu-id="28fef-118">MABS 提供重要的功能，可以解決的小數位數的情況。</span><span class="sxs-lookup"><span data-stu-id="28fef-118">MABS provides key capabilities that can solve the scale situation.</span></span> <span data-ttu-id="28fef-119">MSCIS 建立概念的證明 (POC) 牽涉到使用 Microsoft Azure BizTalk 服務 (MABS) 和 BizTalk Server 2013 的混合式解決方案。</span><span class="sxs-lookup"><span data-stu-id="28fef-119">MSCIS created a Proof of Concept (POC) involving a hybrid solution that uses Microsoft Azure BizTalk Services (MABS) and BizTalk Server 2013.</span></span> <span data-ttu-id="28fef-120">需求為提供掌控執行從端對端，向下包括相應增加尖峰 sales 和小數位數的能力，一般的銷售。</span><span class="sxs-lookup"><span data-stu-id="28fef-120">The requirement is to provide flawless execution from end-to-end, including the ability to scale up for peak sales and scale down for normal sales.</span></span>  
  
 <span data-ttu-id="28fef-121">這份技術白皮書討論測試使用 Microsoft Azure BizTalk 服務 (MABS) 和 BizTalk Server 2013 的解決方案。</span><span class="sxs-lookup"><span data-stu-id="28fef-121">This white paper discusses the solutions tested using Microsoft Azure BizTalk Services (MABS) and BizTalk Server 2013.</span></span>  
  
 <span data-ttu-id="28fef-122">若要檢閱文件，請下載[提供鏈結訂單使用 Microsoft Azure BizTalk 服務](http://download.microsoft.com/download/6/D/E/6DEE8EE9-0F26-4991-8FE5-B0E5239C0980/Using%20Windows%20Azure%20BizTalk%20Services%20for%20Supply%20Chain%20Orders.docx)Word 文件。</span><span class="sxs-lookup"><span data-stu-id="28fef-122">To review the document, please download the [Using Microsoft Azure BizTalk Services for Supply Chain Orders](http://download.microsoft.com/download/6/D/E/6DEE8EE9-0F26-4991-8FE5-B0E5239C0980/Using%20Windows%20Azure%20BizTalk%20Services%20for%20Supply%20Chain%20Orders.docx) Word document.</span></span>