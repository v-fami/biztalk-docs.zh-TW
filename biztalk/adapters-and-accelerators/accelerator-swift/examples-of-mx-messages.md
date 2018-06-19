---
title: MX 訊息範例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b592034f-2dd3-40e4-8f0b-eb6d65c38fff
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f5280f8ec2ce16344562907a95c1b0afa8c6627
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22209142"
---
# <a name="examples-of-mx-messages"></a><span data-ttu-id="a3bb5-102">MX 訊息的範例</span><span class="sxs-lookup"><span data-stu-id="a3bb5-102">Examples of MX Messages</span></span>
<span data-ttu-id="a3bb5-103">命令列來產生不同的 MX 訊息的解決方案 （InfoPath 表單範本）</span><span class="sxs-lookup"><span data-stu-id="a3bb5-103">Command Lines to generate the solution (InfoPath form template) for the Different MX messages</span></span>  
  
 <span data-ttu-id="a3bb5-104">下列範例會要求在 「 pacs.004.001.01"和"pain.002.001.01 」 結構描述都位於 c:\schemas。</span><span class="sxs-lookup"><span data-stu-id="a3bb5-104">The following examples require that the “pacs.004.001.01" and “pain.002.001.01” schemas are all in c:\schemas.</span></span> <span data-ttu-id="a3bb5-105">這會產生方案的 「 C:\GeneratedForms"資料夾中的 InfoPath 表單範本。</span><span class="sxs-lookup"><span data-stu-id="a3bb5-105">This will generate the solution for InfoPath Form Template in the "C:\GeneratedForms" folder.</span></span> <span data-ttu-id="a3bb5-106">將 InfoPath 表單需要產生的訊息的名稱與相同的方案資料夾名稱。</span><span class="sxs-lookup"><span data-stu-id="a3bb5-106">The folder name of the solution would be same as the name of the message for which the InfoPath form needs to be generated.</span></span> <span data-ttu-id="a3bb5-107">這些範例假設此公用程式，已放在"C:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\FormGeneratorUtility"資料夾中。</span><span class="sxs-lookup"><span data-stu-id="a3bb5-107">These examples assume that the utility has been placed in “C:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\FormGeneratorUtility” folder.</span></span> <span data-ttu-id="a3bb5-108">取代您選擇在公用程式的位置下命令。</span><span class="sxs-lookup"><span data-stu-id="a3bb5-108">Replace the location that you have selected for the utility in the below commands.</span></span>  
  
-   <span data-ttu-id="a3bb5-109">**若要產生的表單 pacs.004.001.01 結構描述：**</span><span class="sxs-lookup"><span data-stu-id="a3bb5-109">**To generate a form for the pacs.004.001.01 schema:**</span></span>  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\MXTemplates” " C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas pacs.004.001.01`  
  
-   <span data-ttu-id="a3bb5-110">**若要產生的表單 pacs.004.001.01 和 pain.002.001.01 結構描述：**</span><span class="sxs-lookup"><span data-stu-id="a3bb5-110">**To generate a form for the pacs.004.001.01 and pain.002.001.01 schema:**</span></span>  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\MXTemplates” “C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas pacs.004.001.01 pain.002.001.01`