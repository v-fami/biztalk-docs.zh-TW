---
title: 產生類別 0 和 MT121 Form |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1470b8e1-0008-4f15-8958-ba4c7ecbffd8
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40f9de5ff6e5f988422574640e13a45f8fd81632
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22207302"
---
# <a name="generating-category-0-and-mt121-forms"></a>產生類別 0 和 MT121 表單
類別 0 和 MT121 InfoPath 表單產生需要不同的範本檔案。 類別 0 form 分成 5 的類別。 一般類別訊息會產生相同的方式進行其餘的 MT 類別。 其他 4 類別，以訊息名稱的範例如下：  
  
-   **若要產生類別 0 GAHeader 表單 （MT036、 MT042、 MT047、 MT072、 MT077 和 MT085）：**  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\GAHeader” " C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas -f GAHeaderForms.txt\`  
  
-   **若要產生類別 0 NoTextBlocks 表單 （MT035、 MT043、 MT048 和 MT049）：**  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\NoTextBlocks” " C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas –f NoTextBlocksForms.txt`  
  
-   **若要產生類別 0 NoTrailer 表單 (MT021):**  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\NoTrailer” " C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas –f NoTrailerForms.txt`  
  
-   **若要產生類別 0 NoTrailerTextBlocks 表單 (MT082):**  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\NoTrailerTextBlocks” " C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas –f NoTrailerTextBlocks.txt`  
  
-   **若要產生類別目錄 1 NoHeaderTextBlock 表單 (MT121):**  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\ NoHeaderTextBlock” " C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas -f NoHeaderTextBlockForms.txt`