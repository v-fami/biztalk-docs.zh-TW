---
title: MSCIT： 從 BizTalk Server 2009 中樞到 BizTalk Server 2013 R2 虛擬化集線器供應鏈移轉 |Microsoft 文件
ms.custom: ''
ms.prod: biztalk-server
ms.date: 06/08/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7366ffc2-d1f6-44df-b1f8-f07b99cf5d11
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a3cc49424ead924bdb98dd196f7792806d2702f
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
ms.locfileid: "22299006"
---
# <a name="mscit-supply-chain-migration-from-biztalk-server-2009-hub-to-biztalk-server-2013-r2-virtualized-hub"></a><span data-ttu-id="ecf17-102">MSCIT： 從 BizTalk Server 2009 中樞的供應鏈移轉至 BizTalk Server 2013 R2 虛擬化的中樞</span><span class="sxs-lookup"><span data-stu-id="ecf17-102">MSCIT: Supply Chain migration from BizTalk Server 2009 hub to BizTalk Server 2013 R2 virtualized hub</span></span>
<span data-ttu-id="ecf17-103">從 BizTalk Server 2010 應用程式移轉至 BizTalk Server 2013 R2。</span><span class="sxs-lookup"><span data-stu-id="ecf17-103">Application migration from BizTalk Server 2010 to BizTalk Server 2013 R2.</span></span>  
  
 <span data-ttu-id="ecf17-104">**作者**: Arvind Chaudhary、 Microsoft &#124; Piyush Prasad、 Microsoft</span><span class="sxs-lookup"><span data-stu-id="ecf17-104">**Author**: Arvind Chaudhary, Microsoft &#124; Piyush Prasad, Microsoft</span></span>  
  
 <span data-ttu-id="ecf17-105">**發行**: 2015 年 9 月</span><span class="sxs-lookup"><span data-stu-id="ecf17-105">**Published**: September 2015</span></span>  
  
 <span data-ttu-id="ecf17-106">**適用於**: BizTalk Server 2013 R2</span><span class="sxs-lookup"><span data-stu-id="ecf17-106">**Applies to**: BizTalk Server 2013 R2</span></span>  
  
 <span data-ttu-id="ecf17-107">**摘要**： 描述的原因，以及由 Microsoft IT 應用程式從 BizTalk Server 2009 和 2010年移轉至 BizTalk Server 2013 R2 移轉程序。</span><span class="sxs-lookup"><span data-stu-id="ecf17-107">**Summary**:  Describes the reasons and the  migration process taken by Microsoft IT to migrate applications from BizTalk Server 2009 and 2010 to BizTalk Server 2013 R2.</span></span> <span data-ttu-id="ecf17-108">MSIT 識別訊息資料流、 轉換 Visual Studio 中的 BizTalk 專案、 移動交易夥伴管理合作對象和協議，和更新應用程式繫結。</span><span class="sxs-lookup"><span data-stu-id="ecf17-108">MSIT identified message streams, converted the BizTalk projects in Visual Studio, moved trading partner management parties and agreements, and updated the application bindings.</span></span>  
  
 <span data-ttu-id="ecf17-109">您也可以閱讀 MSIT 面臨的挑戰和使用的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="ecf17-109">You can also read about the challenges MSIT faced and the best practices used.</span></span>  
  
 <span data-ttu-id="ecf17-110">下載[BizTalk Server 2013 R2 從 BizTalk Server 2009/2010 MSIT 移轉劇本](http://download.microsoft.com/download/6/D/E/6DEE8EE9-0F26-4991-8FE5-B0E5239C0980/MSIT-Whitepaper%20Migration%20Story%20BizTalk%202013%20R2.docx)白皮書。</span><span class="sxs-lookup"><span data-stu-id="ecf17-110">Download the [MSIT Migration story from BizTalk Server 2009/2010 to BizTalk Server 2013 R2](http://download.microsoft.com/download/6/D/E/6DEE8EE9-0F26-4991-8FE5-B0E5239C0980/MSIT-Whitepaper%20Migration%20Story%20BizTalk%202013%20R2.docx) whitepaper.</span></span>