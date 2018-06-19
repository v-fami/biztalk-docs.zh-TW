---
title: 步驟 4： 建立範例 XML BeginDoc1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e494b4b2-4c83-4293-8ae8-acae29018e7f
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a48a4ee378560ad2d0360445e3fb732bb46e79f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276726"
---
# <a name="step-4-create-a-sample-xml-begindoc"></a><span data-ttu-id="9fdf2-102">步驟 4： 建立範例 XML BeginDoc</span><span class="sxs-lookup"><span data-stu-id="9fdf2-102">Step 4: Create a Sample XML BeginDoc</span></span>
<span data-ttu-id="9fdf2-103">將下列程式碼儲存到 XML 檔案中。</span><span class="sxs-lookup"><span data-stu-id="9fdf2-103">Save the following into an XML file.</span></span> <span data-ttu-id="9fdf2-104">如果您的測試會使用此範例中的步驟，並使用範例的 J.D.</span><span class="sxs-lookup"><span data-stu-id="9fdf2-104">If your test uses the steps in this example, and uses the example's J.D.</span></span> <span data-ttu-id="9fdf2-105">Edwards OneWorld 物件選項，[//csales/b4200310]，您可以將這放入 Input 資料夾並將其指定的 Out 資料夾 （繫結至 EndDocOut 連接埠的資料夾）。</span><span class="sxs-lookup"><span data-stu-id="9fdf2-105">Edwards OneWorld object selection, [JDE://CSALES/B4200310], you can drop this into the Input folder and what it come out the designated Out folder (the folder bound to the EndDocOut port).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9fdf2-106">您必須修改某些值，以指向您 J.D.</span><span class="sxs-lookup"><span data-stu-id="9fdf2-106">You will have to modify some of the values to point to your J.D.</span></span> <span data-ttu-id="9fdf2-107">Edwards OneWorld 伺服器，例如，此值設定 szCMComputerID 中。</span><span class="sxs-lookup"><span data-stu-id="9fdf2-107">Edwards OneWorld server, for example, the value set in szCMComputerID.</span></span>  
  
```  
<ns0:F4211FSBeginDoc xmlns:ns0="http://schemas.microsoft.com/  
   [JDE://CSALES/B4200310]">  
   <ns0:mnCMJobNumber></ns0:mnCMJobNumber>  
   <ns0:cCMDocAction>A</ns0:cCMDocAction>  
   <ns0:cCMProcessEdits>1</ns0:cCMProcessEdits>  
   <ns0:szCMComputerID>BVISION01</ns0:szCMComputerID>  
   <ns0:cCMUpdateWriteToWF>2</ns0:cCMUpdateWriteToWF>  
   <ns0:szCMProgramID>XMLInterop</ns0:szCMProgramID>  
   <ns0:szCMVersion>ZJDE0001</ns0:szCMVersion>  
   <ns0:szOrderType>SO</ns0:szOrderType>  
   <ns0:szBusinessUnit>M30</ns0:szBusinessUnit>  
   <ns0:szOriginalOrderCo></ns0:szOriginalOrderCo>  
   <ns0:szOriginalOrderNo></ns0:szOriginalOrderNo>  
   <ns0:szOriginalOrderType></ns0:szOriginalOrderType>  
   <ns0:mnAddressNumber>1001</ns0:mnAddressNumber>  
   <ns0:jdOrderDate></ns0:jdOrderDate>  
   <ns0:szReference></ns0:szReference>  
   <ns0:cApplyFreightYN>Y</ns0:cApplyFreightYN>  
   <ns0:szCurrencyCode></ns0:szCurrencyCode>  
   <ns0:cWKSourceOfData></ns0:cWKSourceOfData>  
   <ns0:cWKProcMode></ns0:cWKProcMode>  
   <ns0:mnWKSuppressProcess>0</ns0:mnWKSuppressProcess>  
   <ns0:cRetrieveOrderNo>1</ns0:cRetrieveOrderNo>  
   <ns0:nSourceOfOrder>0</ns0:nSourceOfOrder>  
</ns0:F4211FSBeginDoc>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9fdf2-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9fdf2-108">See Also</span></span>  
 <span data-ttu-id="9fdf2-109">[步驟 1： 參考結構描述 DLL](../core/step-1-reference-the-schema-dll2.md) </span><span class="sxs-lookup"><span data-stu-id="9fdf2-109">[Step 1: Reference the Schema DLL](../core/step-1-reference-the-schema-dll2.md) </span></span>  
 <span data-ttu-id="9fdf2-110">[步驟 2： 建立協調流程](../core/step-2-create-the-orchestration1.md) </span><span class="sxs-lookup"><span data-stu-id="9fdf2-110">[Step 2: Create the Orchestration](../core/step-2-create-the-orchestration1.md) </span></span>  
 [<span data-ttu-id="9fdf2-111">步驟 3： 完成及執行專案</span><span class="sxs-lookup"><span data-stu-id="9fdf2-111">Step 3: Complete and Run the Project</span></span>](../core/step-3-complete-and-run-the-project2.md)