---
title: "在 BizTalk Server proactivity |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b924ddae-0e7f-4058-b308-7ea9537fb45f
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4508507c0cf84141bc63df7a53eeab7c38c9f390
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="proactivity-in-biztalk-server"></a><span data-ttu-id="6d683-102">在 BizTalk Server proactivity</span><span class="sxs-lookup"><span data-stu-id="6d683-102">Proactivity in BizTalk Server</span></span>
<span data-ttu-id="6d683-103">BizTalk 技術文章</span><span class="sxs-lookup"><span data-stu-id="6d683-103">BizTalk Technical Article</span></span>  
  
 <span data-ttu-id="6d683-104">**BizTalk Server 的主動性**</span><span class="sxs-lookup"><span data-stu-id="6d683-104">**Proactivity in BizTalk Server**</span></span>  
  
 <span data-ttu-id="6d683-105">**作者：** Tord 高興 Nordahl (包威 AS)</span><span class="sxs-lookup"><span data-stu-id="6d683-105">**Writer:** Tord Glad Nordahl (Bouvet AS)</span></span>  
  
 <span data-ttu-id="6d683-106">**技術校閱：**有 Pereira (Devscope)、 Steef-jan Wiggers (Motion10)、 Erik Thue (包威 AS)、 Alexander Thue (包威 AS)、 Saravana Kumar (BizTalk360)、 Mandi Ohlinger (Microsoft)</span><span class="sxs-lookup"><span data-stu-id="6d683-106">**Technical Reviewers:** Sandro Pereira (Devscope), Steef-Jan Wiggers (Motion10), Erik Thue (Bouvet AS), Alexander Thue (Bouvet AS), Saravana Kumar  (BizTalk360), Mandi Ohlinger (Microsoft)</span></span>  
  
 <span data-ttu-id="6d683-107">**發行日期：** 2013 年 7 月</span><span class="sxs-lookup"><span data-stu-id="6d683-107">**Published:** July 2013</span></span>  
  
 <span data-ttu-id="6d683-108">**適用於：** BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="6d683-108">**Applies To:** BizTalk Server</span></span>  
  
 <span data-ttu-id="6d683-109">**摘要：**技術白皮書適用於從 BizTalk Server 2004 BizTalk Server 2013 環境。</span><span class="sxs-lookup"><span data-stu-id="6d683-109">**Summary:** The white paper applies from BizTalk Server 2004 to BizTalk Server 2013 environments.</span></span>  <span data-ttu-id="6d683-110">目標是提供一些如何主動和解決，或避免之前發生, 的潛在問題的線索。</span><span class="sxs-lookup"><span data-stu-id="6d683-110">The goal is to provide some insight of how to be proactive and resolve, or avoid, potential problems before they occur.</span></span> <span data-ttu-id="6d683-111">它適用於所有類型的 BizTalk 使用者，包括架構設計人員、 開發人員和系統管理員。</span><span class="sxs-lookup"><span data-stu-id="6d683-111">It applies to all types of BizTalk users, including architects, developers, and administrators.</span></span> <span data-ttu-id="6d683-112">並非所有所述的案例可能會發生在您的環境，這份技術白皮書中未提及的某些情況下可能會發生。</span><span class="sxs-lookup"><span data-stu-id="6d683-112">Not all scenarios described may occur in your environment and some scenarios not mentioned in this white paper can occur.</span></span>  
  
 <span data-ttu-id="6d683-113">由於本質和重要性的 BizTalk Server 中，設定和最佳作法可能會因環境。包括網路設定、 架構設計、 版本、 訊息流程和資源。</span><span class="sxs-lookup"><span data-stu-id="6d683-113">Due to the nature and importance of BizTalk Server, settings and best practices can vary by environment; including network settings, architecture design, versions, message flow, and resources.</span></span> <span data-ttu-id="6d683-114">這份技術白皮書討論一般的安裝程式，並建議值。</span><span class="sxs-lookup"><span data-stu-id="6d683-114">This white paper discussed the common setup and recommended values.</span></span>  
  
 <span data-ttu-id="6d683-115">若要檢閱文件，請下載[BizTalk Server 中的 Proactivity](http://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Proactivity%20in%20BizTalk%20Server.docx) Word 文件。</span><span class="sxs-lookup"><span data-stu-id="6d683-115">To review the document, please download the [Proactivity in BizTalk Server](http://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Proactivity%20in%20BizTalk%20Server.docx) Word document.</span></span>