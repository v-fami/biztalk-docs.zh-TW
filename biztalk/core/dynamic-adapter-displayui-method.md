---
title: "動態配接器 DisplayUI 方法 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9183d2ee-4265-4fee-9d1d-7e2462d8ff37
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd26bc5e5e344f53537e16135bf0a30b8b1443c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="dynamic-adapter-displayui-method"></a><span data-ttu-id="3589e-102">動態配接器 DisplayUI 方法</span><span class="sxs-lookup"><span data-stu-id="3589e-102">Dynamic Adapter DisplayUI Method</span></span>
<span data-ttu-id="3589e-103">這個方法在**IDynamicAdapterConfig**介面會顯示自訂配接器的自訂使用者介面。</span><span class="sxs-lookup"><span data-stu-id="3589e-103">This method on the **IDynamicAdapterConfig** interface displays the custom user interface for the custom adapter.</span></span> <span data-ttu-id="3589e-104">如此可讓使用者根據其 BizTalk 專案中選取的服務來檢視、選取及匯入相關的支援檔案。</span><span class="sxs-lookup"><span data-stu-id="3589e-104">This enables the user to view, select, and import the related supporting files based upon the selected services into their BizTalk project.</span></span>  
  
 <span data-ttu-id="3589e-105">在 file 配接器中，修改中的程式碼**displayUI** AdapterManagement.cs 檔案來選取要接受結構描述類型建立自訂使用者介面 (UI) 的方法。</span><span class="sxs-lookup"><span data-stu-id="3589e-105">In the file adapter, modify the code within the **displayUI** method of the AdapterManagement.cs file to create a custom user interface (UI) for selecting the type of schema to accept.</span></span> <span data-ttu-id="3589e-106">當選取結構描述之後，請選擇適當的 WSDL 檔案。</span><span class="sxs-lookup"><span data-stu-id="3589e-106">After a schema is selected, choose the appropriate WSDL file.</span></span>  
  
 <span data-ttu-id="3589e-107">下列程式碼取自**displayUI** AdapterManagement.cs 檔案的方法。</span><span class="sxs-lookup"><span data-stu-id="3589e-107">The following code is from the **displayUI** method of the AdapterManagement.cs file.</span></span>  
  
```  
/// <summary>  
        /// Acquire wsdl(s) from which to build the user interface  
        /// </summary>  
        /// <param name="endPointConfiguration"></param>  
        /// <param name="owner"></param>  
        /// <param name="WSDLList">Array of custom UI's WSDL (returned)</param>  
        /// <returns></returns>  
        public Result DisplayUI(IPropertyBag endPointConfiguration,   
            IWin32Window owner,  
            out string [] WSDLList)   
      {  
            WSDLList = new string[1];  
            WSDLList[0] = GetResource("AdapterManagement.service1.wsdl");  
            return Result.Continue;  
        }  
```