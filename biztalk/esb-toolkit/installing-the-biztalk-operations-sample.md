---
title: "安裝 BizTalk 作業範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57c982c2-f796-4c63-9bca-7e8965779850
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa8fb289e5bb7950f9ad8bca3dac98035bada176
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="installing-the-biztalk-operations-sample"></a><span data-ttu-id="081f9-102">安裝 BizTalk 作業範例</span><span class="sxs-lookup"><span data-stu-id="081f9-102">Installing the BizTalk Operations Sample</span></span>
<span data-ttu-id="081f9-103">Microsoft BizTalk 作業範例需要安裝及設定 ESB BizTalk 作業服務。</span><span class="sxs-lookup"><span data-stu-id="081f9-103">The Microsoft BizTalk Operations sample requires the ESB BizTalk Operations service installed and configured.</span></span> <span data-ttu-id="081f9-104">ESB BizTalk 作業服務是其中一個核心 Web 服務可以安裝及設定使用 ESB 組態工具。</span><span class="sxs-lookup"><span data-stu-id="081f9-104">ESB BizTalk Operations service is one of the core Web services that can be installed and configured using the ESB Configuration Tool.</span></span> <span data-ttu-id="081f9-105">如需有關使用 ESB 組態工具的詳細資訊，請參閱[http://msdn.microsoft.com/library/jj684558(v=bts.80).aspx](http://msdn.microsoft.com/library/jj684558\(v=bts.80\).aspx).</span><span class="sxs-lookup"><span data-stu-id="081f9-105">For more information about using the ESB Configuration Tool, see [http://msdn.microsoft.com/library/jj684558(v=bts.80).aspx](http://msdn.microsoft.com/library/jj684558\(v=bts.80\).aspx).</span></span> <span data-ttu-id="081f9-106">BizTalk 作業 Web 服務的預設位置是 http://localhost/ESB.BizTalkOperationsService/Operations.asmx;不過，您可以變更這個應用程式組態檔中如果部署中的不同位置或遠端伺服器的服務。</span><span class="sxs-lookup"><span data-stu-id="081f9-106">The default location of the BizTalk Operations Web service is http://localhost/ESB.BizTalkOperationsService/Operations.asmx; however, you can change this in the application configuration file if you deploy the service in a different location or a remote server.</span></span>  
  
 <span data-ttu-id="081f9-107">您必須從方案專案中安裝 BizTalk 作業範例。</span><span class="sxs-lookup"><span data-stu-id="081f9-107">You must install BizTalk Operations sample from the solution project.</span></span>  
  
 <span data-ttu-id="081f9-108">**若要安裝 BizTalk 作業範例**</span><span class="sxs-lookup"><span data-stu-id="081f9-108">**To install the BizTalk Operations sample**</span></span>  
  
1.  <span data-ttu-id="081f9-109">開啟名為 ESB.BizTalkOperations.Test.Client.csproj \Source\Samples\BizTalkOperations 資料夾安裝方案[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]到 Visual Studio 中的範例。</span><span class="sxs-lookup"><span data-stu-id="081f9-109">Open the solution named ESB.BizTalkOperations.Test.Client.csproj from the \Source\Samples\BizTalkOperations folder where you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] samples into Visual Studio.</span></span>  
  
2.  <span data-ttu-id="081f9-110">使用上的命令**建置**功能表編譯方案。</span><span class="sxs-lookup"><span data-stu-id="081f9-110">Use the commands on the **Build** menu to compile the solution.</span></span>