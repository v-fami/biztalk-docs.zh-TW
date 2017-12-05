---
title: "將管線元件部署 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, pipeline components [custom]
- pipeline components [custom], deploying
ms.assetid: 98b47fbf-62c0-4012-a406-58c4d56b305a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 041bd8c6e6fa9c3969be18f0804460c00de5f11a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="deploying-pipeline-components"></a><span data-ttu-id="52e58-102">部署管線元件</span><span class="sxs-lookup"><span data-stu-id="52e58-102">Deploying Pipeline Components</span></span>
<span data-ttu-id="52e58-103">所有.NET 管線元件組件 （原生和自訂） 必須都位於\<*安裝目錄*\>\Pipeline Components 資料夾執行的伺服器。</span><span class="sxs-lookup"><span data-stu-id="52e58-103">All the .NET pipeline component assemblies (native and custom) must be located in the \<*installation directory*\>\Pipeline Components folder to be executed by the server.</span></span> <span data-ttu-id="52e58-104">如果具有自訂元件的管線將要在數台伺服器之間部署，該元件的二進位檔必須存在於每一部伺服器上的指定資料夾中。</span><span class="sxs-lookup"><span data-stu-id="52e58-104">If the pipeline with a custom component will be deployed across several servers, the component's binaries must be present in the specified folder on every server.</span></span>  
  
 <span data-ttu-id="52e58-105">您不需要將 BizTalk 執行階段所要使用的自訂管線元件加入到全域組件快取 (GAC)。</span><span class="sxs-lookup"><span data-stu-id="52e58-105">You do not need to add a custom pipeline component to be used by the BizTalk Runtime to the Global Assembly Cache (GAC).</span></span>  
  
 <span data-ttu-id="52e58-106">此管線中的自訂 COM 元件也會出現在工具箱中 (前提是這些元件會在電腦上註冊為 COM 元件)。</span><span class="sxs-lookup"><span data-stu-id="52e58-106">Custom COM components in the pipeline will also appear in the Toolbox, provided they are registered on the computer as a COM component.</span></span> <span data-ttu-id="52e58-107">自訂.NET 管線元件必須放入\<*安裝目錄*\>\Pipeline Components 資料夾。</span><span class="sxs-lookup"><span data-stu-id="52e58-107">Custom .NET pipeline components must be placed into the \<*installation directory*\>\Pipeline Components folder.</span></span>  
  
 <span data-ttu-id="52e58-108">當二進位檔位於正確的位置之後，您需要將此元件新增至工具箱。</span><span class="sxs-lookup"><span data-stu-id="52e58-108">After the binary files are in the correct location, you need to add the component to the Toolbox.</span></span> <span data-ttu-id="52e58-109">如需新增管線元件至工具箱的指示，請參閱[如何使用 [工具箱]](../core/how-to-use-the-toolbox.md)。</span><span class="sxs-lookup"><span data-stu-id="52e58-109">For instructions on adding the pipeline component to the Toolbox, see [How to Use the Toolbox](../core/how-to-use-the-toolbox.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52e58-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="52e58-110">See Also</span></span>  
 [<span data-ttu-id="52e58-111">開發自訂管線元件</span><span class="sxs-lookup"><span data-stu-id="52e58-111">Developing Custom Pipeline Components</span></span>](../core/developing-custom-pipeline-components.md)