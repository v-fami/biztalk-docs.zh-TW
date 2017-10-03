---
title: "如何使用 ThrowDetailedError 參數 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web services, security
- Web services, debugging
ms.assetid: 8a8af3c0-a9a2-42fe-b0be-a5a106403747
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 194306da3b021e7460b88a3d8e76801a2eeaebba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-throwdetailederror-switch"></a><span data-ttu-id="c0a96-102">如何使用 ThrowDetailedError 參數</span><span class="sxs-lookup"><span data-stu-id="c0a96-102">How to Use the ThrowDetailedError Switch</span></span>
<span data-ttu-id="c0a96-103">如果發生錯誤時，Web 用戶端會接收泛型**SoapException**。</span><span class="sxs-lookup"><span data-stu-id="c0a96-103">If an error occurs, the Web client receives a generic **SoapException**.</span></span>  
  
 <span data-ttu-id="c0a96-104">若要偵錯已發佈的 Web 服務，您可以在 Web.config 檔案中加入某個參數，以便控制從該發佈的 Web 服務傳回之例外狀況詳細資料的等級。</span><span class="sxs-lookup"><span data-stu-id="c0a96-104">To debug your published Web service, you can add a switch to the Web.config file to control the level of the exception details returned from the published Web service.</span></span>  
  
 <span data-ttu-id="c0a96-105">Web.config 檔案包含應用程式設定參數**ThrowDetailedError**。</span><span class="sxs-lookup"><span data-stu-id="c0a96-105">The Web.config file contains an application setting switch, **ThrowDetailedError**.</span></span> <span data-ttu-id="c0a96-106">**False**是預設設定**ThrowDetailedError**。</span><span class="sxs-lookup"><span data-stu-id="c0a96-106">**False** is the default setting for **ThrowDetailedError**.</span></span> <span data-ttu-id="c0a96-107">如果您將設定變更為**True**，伺服器 proxy 將內部例外狀況資訊傳回給 Web 用戶端，讓您偵錯已發佈的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="c0a96-107">If you change the setting to **True**, the server proxy returns inner exception information to the Web client enabling you to debug the published Web service.</span></span>  
  
 <span data-ttu-id="c0a96-108">下列 XML 程式碼示範**ThrowDetailedError**下的 Web.config 檔案中出現的交換器\<appSettings > 節點：</span><span class="sxs-lookup"><span data-stu-id="c0a96-108">The following XML code shows the **ThrowDetailedError** switch that appears in the Web.config file under the \<appSettings> node:</span></span>  
  
```  
<appSettings>  
  <add key="ThrowDetailedError" value="False" />  
<appSettings/>  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="c0a96-109">依照預設，BizTalk Server 不會將內部例外狀況資訊傳回給 Web 用戶端，因為這種資訊可能包含機密資訊 (例如應用程式呼叫堆疊)。</span><span class="sxs-lookup"><span data-stu-id="c0a96-109">BizTalk Server does not return inner exception information to the Web client by default since it may contain sensitive information, such as application call stacks.</span></span> <span data-ttu-id="c0a96-110">偵錯之後，您應該設定**ThrowDetailedError**設**False**。</span><span class="sxs-lookup"><span data-stu-id="c0a96-110">After debugging, you should set the **ThrowDetailedError** setting to **False**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0a96-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0a96-111">See Also</span></span>  
 [<span data-ttu-id="c0a96-112">偵錯已發佈的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="c0a96-112">Debugging Published Web Services</span></span>](../core/debugging-published-web-services.md)