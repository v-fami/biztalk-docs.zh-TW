---
title: 安裝 BizTalk Server 2010 Accelerator for SWIFT |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 78d996ce-40ea-4d01-b083-c55ccace4b26
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8dcec7f25211fac8c99a89ce7ce85840f457971a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298102"
---
# <a name="installing-biztalk-server-2010-accelerator-for-swift"></a><span data-ttu-id="420fb-102">安裝 BizTalk Server 2010 Accelerator for SWIFT</span><span class="sxs-lookup"><span data-stu-id="420fb-102">Installing BizTalk Server 2010 Accelerator for SWIFT</span></span>
<span data-ttu-id="420fb-103">![標誌](../technical-guides/media/bts-10-installaccelerator-logo.gif "BTS_10_InstallAccelerator_Logo")</span><span class="sxs-lookup"><span data-stu-id="420fb-103">![Logo](../technical-guides/media/bts-10-installaccelerator-logo.gif "BTS_10_InstallAccelerator_Logo")</span></span>  
  
 <span data-ttu-id="420fb-104">BizTalk 技術文章</span><span class="sxs-lookup"><span data-stu-id="420fb-104">BizTalk Technical Article</span></span>  
  
 <span data-ttu-id="420fb-105">**安裝 BizTalk Server 2010 Accelerator for SWIFT**</span><span class="sxs-lookup"><span data-stu-id="420fb-105">**Installing BizTalk Server 2010 Accelerator for SWIFT**</span></span>  
  
 <span data-ttu-id="420fb-106">**作者：** Maria Quian，Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="420fb-106">**Writer:** Maria Quian, Microsoft Corporation</span></span>  
  
 <span data-ttu-id="420fb-107">**技術校閱：** 安德列斯 Naranjo，Mandi Ohlinger</span><span class="sxs-lookup"><span data-stu-id="420fb-107">**Technical Reviewers:** Andres Naranjo, Mandi Ohlinger</span></span>  
  
 <span data-ttu-id="420fb-108">**發行日期：** 2012 年 6 月</span><span class="sxs-lookup"><span data-stu-id="420fb-108">**Published:** June 2012</span></span>  
  
 <span data-ttu-id="420fb-109">**適用於：** BizTalk Server 2010 Accelerator for SWIFT</span><span class="sxs-lookup"><span data-stu-id="420fb-109">**Applies To:** BizTalk Server 2010 Accelerator for SWIFT</span></span>  
  
 <span data-ttu-id="420fb-110">**摘要：** 成功安裝的 Microsoft BizTalk Server 2010 Accelerator for SWIFT (A4SWIFT) 的基礎是了解 A4SWIFT 功能以及每項功能所依存的 BizTalk 元件。</span><span class="sxs-lookup"><span data-stu-id="420fb-110">**Summary:** The foundation for a successful installation of Microsoft BizTalk Server 2010 Accelerator for SWIFT (A4SWIFT) is an understanding of the A4SWIFT features and the BizTalk components on which each feature depends.</span></span> <span data-ttu-id="420fb-111">每個 A4SWIFT 功能取決於其他已正確設定的 BizTalk 元件。</span><span class="sxs-lookup"><span data-stu-id="420fb-111">Each A4SWIFT feature depends on other properly configured BizTalk components.</span></span> <span data-ttu-id="420fb-112">會影響建置 A4SWIFT 環境的其他考量包括現有的網路基礎結構和已設定的 BizTalk Server 環境。</span><span class="sxs-lookup"><span data-stu-id="420fb-112">Other considerations that affect building an A4SWIFT environment include an existing network infrastructure and an already configured BizTalk Server environment.</span></span> <span data-ttu-id="420fb-113">本文件將參考，並將現有的文件建置 BizTalk Server 環境。</span><span class="sxs-lookup"><span data-stu-id="420fb-113">This document will refer and use the existing documentation for building BizTalk Server environments.</span></span> <span data-ttu-id="420fb-114">A4SWIFT 繼承 BizTalk Server 2010 的所有軟硬體需求。</span><span class="sxs-lookup"><span data-stu-id="420fb-114">A4SWIFT inherits all software and hardware requirements for BizTalk Server 2010.</span></span>  
  
 <span data-ttu-id="420fb-115">安裝指南適用於每個 A4SWIFT 相關的元件，但不是的單一編譯文件 elaborates 安裝/設定步驟。</span><span class="sxs-lookup"><span data-stu-id="420fb-115">An installation guide is available for each A4SWIFT related component but not a single compiled document that elaborates on the installation/configuration steps.</span></span> <span data-ttu-id="420fb-116">本文件會將它們結合在一起，並識別某些安裝和設定期間遇到的常見問題。</span><span class="sxs-lookup"><span data-stu-id="420fb-116">This document will bring them together and identify some of the common issues encountered during installation and configuration.</span></span>  
  
 <span data-ttu-id="420fb-117">若要檢閱文件，請下載[安裝 BizTalk Server 2010 Accelerator for SWIFT](http://go.microsoft.com/fwlink/?LinkId=255118) Word 文件。</span><span class="sxs-lookup"><span data-stu-id="420fb-117">To review the document, please download the [Installing BizTalk Server 2010 Accelerator for SWIFT](http://go.microsoft.com/fwlink/?LinkId=255118) Word document.</span></span>