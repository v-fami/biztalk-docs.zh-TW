---
title: "驗證部署 Setup1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CLASSPATH, verifying
- deployment, verifying setup
ms.assetid: 6c719e4c-9a61-480f-a4e4-0a1c518d1364
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5799d164dc2470236c3ab0286e38d19986a4d5a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="verifying-the-deployment-setup"></a><span data-ttu-id="6a2b7-102">驗證部署設定</span><span class="sxs-lookup"><span data-stu-id="6a2b7-102">Verifying the Deployment Setup</span></span>
<span data-ttu-id="6a2b7-103">使用 BizTalk Server 匯入繫結檔案之前，必須確認下列項目：</span><span class="sxs-lookup"><span data-stu-id="6a2b7-103">Before you use the BizTalk Server to import a binding file, you must verify the following:</span></span>  
  
-   <span data-ttu-id="6a2b7-104">CLASSPATH 指向 JD Edwards EnterpriseOne 專屬檔案的特定位置。</span><span class="sxs-lookup"><span data-stu-id="6a2b7-104">The CLASSPATH is pointing to a specific location for the JD Edwards EnterpriseOne-specific files.</span></span> <span data-ttu-id="6a2b7-105">確認這些檔案的位置在新電腦上是相同的，否則請編輯繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="6a2b7-105">Verify that the location of these files is the same on the new computer, or edit the binding file.</span></span>  
  
-   <span data-ttu-id="6a2b7-106">在新電腦上用於存放回應的資料夾存在且相同，否則請編輯繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="6a2b7-106">The folders for the responses exist and are identical on the new computer, or edit the binding file.</span></span>  
  
-   <span data-ttu-id="6a2b7-107">JD Edwards EnterpriseOne 系統密碼 (如果出現在組態中) 以 ***** 格式儲存在繫結檔案中。</span><span class="sxs-lookup"><span data-stu-id="6a2b7-107">JD Edwards EnterpriseOne system passwords, if present in the configuration, are saved as ***** in the binding file.</span></span> <span data-ttu-id="6a2b7-108">如需詳細資訊，請參閱[部署限制](../core/deployment-limitations4.md)。</span><span class="sxs-lookup"><span data-stu-id="6a2b7-108">For more information see [Deployment Limitations](../core/deployment-limitations4.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a2b7-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a2b7-109">See Also</span></span>  
 [<span data-ttu-id="6a2b7-110">部署連接埠和組件</span><span class="sxs-lookup"><span data-stu-id="6a2b7-110">Deploying Ports and Assemblies</span></span>](../core/deploying-ports-and-assemblies3.md)