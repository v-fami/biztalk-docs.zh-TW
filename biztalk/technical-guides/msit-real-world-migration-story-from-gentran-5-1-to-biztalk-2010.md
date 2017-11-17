---
title: "MSIT： 真實世界移轉劇本 Gentran 5.1 從 BizTalk 2010 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31326e2f-fb86-4b2c-88cd-b9406695038b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b742777c5e547078c2fa3fbf1a8d5bd8c466924
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="msit-real-world-migration-story-from-gentran-51-to-biztalk-2010"></a><span data-ttu-id="894ed-102">MSIT： 真實世界移轉劇本 Gentran 5.1 從 BizTalk 2010</span><span class="sxs-lookup"><span data-stu-id="894ed-102">MSIT: Real World Migration Story from Gentran 5.1 to BizTalk 2010</span></span>
<span data-ttu-id="894ed-103">BizTalk 技術文章</span><span class="sxs-lookup"><span data-stu-id="894ed-103">BizTalk Technical Article</span></span>  
  
 <span data-ttu-id="894ed-104">**MSIT： 真實世界移轉劇本 Gentran 5.1 從 BizTalk 2010**</span><span class="sxs-lookup"><span data-stu-id="894ed-104">**MSIT: Real World Migration Story from Gentran 5.1 to BizTalk 2010**</span></span>  
  
 <span data-ttu-id="894ed-105">**作者：** Amit Kumar Dua、 Microsoft &#124; Banupriya Thirumaran Microsoft</span><span class="sxs-lookup"><span data-stu-id="894ed-105">**Author:** Amit Kumar Dua, Microsoft  &#124;  Banupriya Thirumaran, Microsoft</span></span>  
  
 <span data-ttu-id="894ed-106">**審稿者：** Mandi Ohlinger，Microsoft &#124; Nitin Mehrotra Microsoft</span><span class="sxs-lookup"><span data-stu-id="894ed-106">**Reviewed By:** Mandi Ohlinger, Microsoft  &#124;  Nitin Mehrotra, Microsoft</span></span>  
  
 <span data-ttu-id="894ed-107">**參與者：** Nikhil Tayal，Microsoft &#124; Anil 錢德 Lingam Microsoft</span><span class="sxs-lookup"><span data-stu-id="894ed-107">**Contributors:** Nikhil Tayal, Microsoft  &#124;  Anil Chandra Lingam, Microsoft</span></span>  
  
 <span data-ttu-id="894ed-108">**發行日期：** 2014 年 10 月</span><span class="sxs-lookup"><span data-stu-id="894ed-108">**Published:** October 2014</span></span>  
  
 <span data-ttu-id="894ed-109">**適用於：** BizTalk Server 2010，Gentran 伺服器</span><span class="sxs-lookup"><span data-stu-id="894ed-109">**Applies To:** BizTalk Server 2010, Gentran Server</span></span>  
  
 <span data-ttu-id="894ed-110">**摘要：** Microsoft IT (MSIT) 整合平台會使用 BizTalk Server 和 Gentran。</span><span class="sxs-lookup"><span data-stu-id="894ed-110">**Summary:** The Microsoft IT (MSIT) integration platform uses BizTalk Server and Gentran.</span></span> <span data-ttu-id="894ed-111">直到最近，Microsoft IT 會有 Gentran 足跡良好與否。</span><span class="sxs-lookup"><span data-stu-id="894ed-111">Until recently, Microsoft IT had a good presence of Gentran footprints.</span></span> <span data-ttu-id="894ed-112">BizTalk server 支援雲端運算和 AS2/EDI 功能之後，沒有機會 Gentran 取代 Microsoft BizTalk Server 2010。</span><span class="sxs-lookup"><span data-stu-id="894ed-112">With BizTalk Server supporting cloud computing and AS2/EDI capabilities, there is an opportunity to replace Gentran with Microsoft BizTalk Server 2010.</span></span>  <span data-ttu-id="894ed-113">Gentran 支援 Windows Server 2003 和 SQL server 2005。亦即延伸支援即將結束。</span><span class="sxs-lookup"><span data-stu-id="894ed-113">Gentran supports Windows Server 2003 and SQL server 2005; which are in extended support that is soon ending.</span></span> <span data-ttu-id="894ed-114">沒有任何以支援較新的平台，包括 Windows Server 2008/2012年和 SQL Server 2008/2014 Gentran 藍圖。</span><span class="sxs-lookup"><span data-stu-id="894ed-114">There is no roadmap for Gentran to support newer platforms, including Windows Server 2008/2012 and SQL Server 2008/2014.</span></span>  
  
 <span data-ttu-id="894ed-115">MSIT 會視為這有機會：</span><span class="sxs-lookup"><span data-stu-id="894ed-115">MSIT viewed this as an opportunity to:</span></span>  
  
-   <span data-ttu-id="894ed-116">取得用於較新的技術平台</span><span class="sxs-lookup"><span data-stu-id="894ed-116">Get to the newer technology platforms</span></span>  
  
-   <span data-ttu-id="894ed-117">移除可支援性條件約束</span><span class="sxs-lookup"><span data-stu-id="894ed-117">Remove the supportability constraints</span></span>  
  
-   <span data-ttu-id="894ed-118">簡化的整合平台的整體架構</span><span class="sxs-lookup"><span data-stu-id="894ed-118">Simplify the overall architecture of the integration platform</span></span>  
  
-   <span data-ttu-id="894ed-119">請更符合成本效益且健全的整合平台</span><span class="sxs-lookup"><span data-stu-id="894ed-119">Make the integration platform more cost effective and robust</span></span>  
  
 <span data-ttu-id="894ed-120">BizTalk Server 2010 是經過證實的整合平台、 具有許多功能和功能，並支援新的平台技術。</span><span class="sxs-lookup"><span data-stu-id="894ed-120">BizTalk Server 2010 is a proven integration platform, has numerous capabilities and features, and supports the new platform technologies.</span></span>  
  
 <span data-ttu-id="894ed-121">這份技術白皮書討論的策略和從 Gentran 5.1 移轉至 BizTalk Server 所採取的步驟。</span><span class="sxs-lookup"><span data-stu-id="894ed-121">This white paper discusses the strategy and steps taken to migrate from Gentran 5.1 to BizTalk Server.</span></span>  
  
 <span data-ttu-id="894ed-122">若要檢閱文件，請下載[MSIT： 真實世界移轉劇本從 Gentran 5.1 BizTalk 2010](http://download.microsoft.com/download/6/D/E/6DEE8EE9-0F26-4991-8FE5-B0E5239C0980/Real%20World%20Migration%20Story%20from%20Gentran%20to%20BizTalk.docx) Word 文件。</span><span class="sxs-lookup"><span data-stu-id="894ed-122">To review the document, please download the [MSIT: Real World Migration Story from Gentran 5.1 to BizTalk 2010](http://download.microsoft.com/download/6/D/E/6DEE8EE9-0F26-4991-8FE5-B0E5239C0980/Real%20World%20Migration%20Story%20from%20Gentran%20to%20BizTalk.docx) Word document.</span></span>