---
title: MT 訊息範例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 629042cc-b941-4c58-b0dd-ede056caf573
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73098c20aeb03e8013f7e20e04c8bb37ce31266e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22208886"
---
# <a name="examples-of-mt-messages"></a><span data-ttu-id="a54e1-102">MT 訊息的範例</span><span class="sxs-lookup"><span data-stu-id="a54e1-102">Examples of MT Messages</span></span>
<span data-ttu-id="a54e1-103">**命令來產生不同的 MT 訊息的解決方案 （InfoPath 表單範本）：**</span><span class="sxs-lookup"><span data-stu-id="a54e1-103">**Commands to generate the solution (InfoPath form template) for the Different MT messages:**</span></span>  
  
 <span data-ttu-id="a54e1-104">下列範例會要求"SWIFT 基底 Types.xsd"、"SWIFT 常見資料 Types.xsd","MT102.xsd"、"MT500.xsd 」 和 「 MT103.xsd"的結構描述都位於 c:\schemas。</span><span class="sxs-lookup"><span data-stu-id="a54e1-104">The following examples require that the "SWIFT Base Types.xsd", "SWIFT Common Data Types.xsd","MT102.xsd", "MT500.xsd", and "MT103.xsd" schemas are all in c:\schemas.</span></span> <span data-ttu-id="a54e1-105">這會產生方案的 「 C:\GeneratedForms"資料夾中的 InfoPath 表單範本。</span><span class="sxs-lookup"><span data-stu-id="a54e1-105">This will generate the solution for InfoPath Form Template in the "C:\GeneratedForms" folder.</span></span> <span data-ttu-id="a54e1-106">將 InfoPath 表單需要產生的訊息的名稱與相同的方案資料夾名稱。</span><span class="sxs-lookup"><span data-stu-id="a54e1-106">The folder name of the solution would be same as the name of the message for which the InfoPath form needs to be generated.</span></span> <span data-ttu-id="a54e1-107">這些範例假設，此公用程式已放置於 「 C:\FormGeneratorUtility2008"資料夾。</span><span class="sxs-lookup"><span data-stu-id="a54e1-107">These examples assume that the utility has been placed in “C:\FormGeneratorUtility2008” folder.</span></span> <span data-ttu-id="a54e1-108">取代您選擇在公用程式的位置下命令。</span><span class="sxs-lookup"><span data-stu-id="a54e1-108">Replace the location that you have selected for the utility in the below commands.</span></span>  
  
-   <span data-ttu-id="a54e1-109">**若要產生的表單 MT103 結構描述：**</span><span class="sxs-lookup"><span data-stu-id="a54e1-109">**To generate a form for the MT103 schema:**</span></span>  
  
     `FormGenerator.exe -b “C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas MT103`  
  
-   <span data-ttu-id="a54e1-110">**若要產生的表單 MT103、 MT102 和 MT500 結構描述：**</span><span class="sxs-lookup"><span data-stu-id="a54e1-110">**To generate a form for the MT103, MT102, and MT500 schema:**</span></span>  
  
     `FormGenerator.exe -b “C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas MT103 MT102 MT500`  
  
-   <span data-ttu-id="a54e1-111">**若要產生的表單 MT103 結構描述 （從檔案）：**</span><span class="sxs-lookup"><span data-stu-id="a54e1-111">**To generate a form for the MT103 schema (from the file):**</span></span>  
  
     `FormGenerator.exe -b “C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas -f P1forms.txt`