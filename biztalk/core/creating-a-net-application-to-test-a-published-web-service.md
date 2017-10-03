---
title: "建立.NET 應用程式來測試已發佈的 Web 服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing, Web services
- Web services, testing
ms.assetid: 94b2223b-45d7-4b86-b4ec-87cc027d7e2a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d13c69a471d546fe8d2b70363dad5cced8bbe62f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-net-application-to-test-a-published-web-service"></a><span data-ttu-id="1e8a6-102">建立.NET 應用程式來測試已發佈的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="1e8a6-102">Creating a .NET Application to Test a Published Web Service</span></span>
<span data-ttu-id="1e8a6-103">若要測試已發佈的 Web 服務，您可以建立 ASP.NET Web 用戶端應用程式，該應用程式會使用您已發佈的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="1e8a6-103">To test your published Web service, you can create an ASP.NET Web client application that consumes your published Web service.</span></span> <span data-ttu-id="1e8a6-104">[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 說明集合內有實用的逐步解說，說明如何建立 ASP.NET Web 用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="1e8a6-104">The [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Help Collection contains a valuable walkthrough for creating an ASP.NET Web client application.</span></span> <span data-ttu-id="1e8a6-105">您可以使用逐步解說來測試已發佈的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="1e8a6-105">You can use the walkthrough to test your published Web service.</span></span>  
  
 <span data-ttu-id="1e8a6-106">逐步解說會建立 ASP.NET Web 用戶端應用程式、新增 Web 參考，並提供範例程式碼，說明如何存取已發佈的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="1e8a6-106">The walkthrough creates an ASP.NET Web client application, adds a Web reference, and provides sample code to show you how to access your published Web service.</span></span> <span data-ttu-id="1e8a6-107">逐步解說會引導您以偵錯模式執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="1e8a6-107">The walkthrough takes you through running the application in debug mode.</span></span>  
  
 <span data-ttu-id="1e8a6-108">如資訊和程序的相關建立 XML Web 服務用戶端專案，請參閱 「 逐步解說:: 存取 XML Web 服務使用 Visual Basic 或 Visual C#"中[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]協助處[http://go.microsoft.com/fwlink/?LinkId=62263](http://go.microsoft.com/fwlink/?LinkId=62263)。</span><span class="sxs-lookup"><span data-stu-id="1e8a6-108">For information and procedures about creating an XML Web service client project, see "Walkthrough: Accessing an XML Web Service Using Visual Basic or Visual C#" in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Help Collection at [http://go.microsoft.com/fwlink/?LinkId=62263](http://go.microsoft.com/fwlink/?LinkId=62263).</span></span> <span data-ttu-id="1e8a6-109">您可以用 BizTalk 已發佈的 Web 服務取代此範例中使用的 Web 服務 TempConvert1。</span><span class="sxs-lookup"><span data-stu-id="1e8a6-109">You can replace the Web service used in this example, TempConvert1, with a BizTalk published Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e8a6-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e8a6-110">See Also</span></span>  
 [<span data-ttu-id="1e8a6-111">測試已發佈 Web 服務</span><span class="sxs-lookup"><span data-stu-id="1e8a6-111">Testing Published Web Services</span></span>](../core/testing-published-web-services.md)