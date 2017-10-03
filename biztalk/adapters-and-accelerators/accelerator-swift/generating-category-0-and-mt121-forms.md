---
title: "產生類別 0 和 MT121 Form |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1470b8e1-0008-4f15-8958-ba4c7ecbffd8
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40f9de5ff6e5f988422574640e13a45f8fd81632
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="generating-category-0-and-mt121-forms"></a><span data-ttu-id="83100-102">產生類別 0 和 MT121 表單</span><span class="sxs-lookup"><span data-stu-id="83100-102">Generating Category 0 and MT121 Forms</span></span>
<span data-ttu-id="83100-103">類別 0 和 MT121 InfoPath 表單產生需要不同的範本檔案。</span><span class="sxs-lookup"><span data-stu-id="83100-103">Category 0 and MT121 InfoPath forms generation require different template files.</span></span> <span data-ttu-id="83100-104">類別 0 form 分成 5 的類別。</span><span class="sxs-lookup"><span data-stu-id="83100-104">Category 0 forms are divided into 5 categories.</span></span> <span data-ttu-id="83100-105">一般類別訊息會產生相同的方式進行其餘的 MT 類別。</span><span class="sxs-lookup"><span data-stu-id="83100-105">General categories messages are generated in the same way as do the rest of the MT categories.</span></span> <span data-ttu-id="83100-106">其他 4 類別，以訊息名稱的範例如下：</span><span class="sxs-lookup"><span data-stu-id="83100-106">Examples of other 4 categories with their message names are given below:</span></span>  
  
-   <span data-ttu-id="83100-107">**若要產生類別 0 GAHeader 表單 （MT036、 MT042、 MT047、 MT072、 MT077 和 MT085）：**</span><span class="sxs-lookup"><span data-stu-id="83100-107">**To generate category 0 GAHeader forms (MT036, MT042, MT047, MT072, MT077, and MT085):**</span></span>  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\GAHeader” " C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas -f GAHeaderForms.txt\`  
  
-   <span data-ttu-id="83100-108">**若要產生類別 0 NoTextBlocks 表單 （MT035、 MT043、 MT048 和 MT049）：**</span><span class="sxs-lookup"><span data-stu-id="83100-108">**To generate category 0 NoTextBlocks forms (MT035, MT043, MT048, and MT049):**</span></span>  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\NoTextBlocks” " C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas –f NoTextBlocksForms.txt`  
  
-   <span data-ttu-id="83100-109">**若要產生類別 0 NoTrailer 表單 (MT021):**</span><span class="sxs-lookup"><span data-stu-id="83100-109">**To generate category 0 NoTrailer forms (MT021):**</span></span>  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\NoTrailer” " C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas –f NoTrailerForms.txt`  
  
-   <span data-ttu-id="83100-110">**若要產生類別 0 NoTrailerTextBlocks 表單 (MT082):**</span><span class="sxs-lookup"><span data-stu-id="83100-110">**To generate category 0 NoTrailerTextBlocks forms (MT082):**</span></span>  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\NoTrailerTextBlocks” " C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas –f NoTrailerTextBlocks.txt`  
  
-   <span data-ttu-id="83100-111">**若要產生類別目錄 1 NoHeaderTextBlock 表單 (MT121):**</span><span class="sxs-lookup"><span data-stu-id="83100-111">**To generate category 1 NoHeaderTextBlock forms (MT121):**</span></span>  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\ NoHeaderTextBlock” " C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas -f NoHeaderTextBlockForms.txt`