---
title: 攔截器組態檔 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 490f5607-e7f6-4f7f-9121-1070db32a7cf
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1bb4a57272ebae5b831552d9446dbdbc937dca1f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256918"
---
# <a name="interceptor-configuration-file"></a><span data-ttu-id="598d4-102">攔截器組態檔</span><span class="sxs-lookup"><span data-stu-id="598d4-102">Interceptor Configuration File</span></span>
<span data-ttu-id="598d4-103">Windows Workflow Foundation 和 Windows Communication Foundation 的 BAM 攔截器需要依賴攔截器組態檔來判斷要攔截哪些事件和日期項目。</span><span class="sxs-lookup"><span data-stu-id="598d4-103">The BAM interceptors for Windows Workflow Foundation and Windows Communication Foundation rely on an interceptor configuration file to determine what events and date elements to intercept.</span></span> <span data-ttu-id="598d4-104">組態檔就是 XML，根據您所針對的技術，由攔截器組態結構描述和 Windows Workflow Foundation 結構描述或 Windows Communication Framework 結構描述定義。</span><span class="sxs-lookup"><span data-stu-id="598d4-104">The configuration file is XML and is defined by the interceptor configuration schema and either the Windows Workflow Foundation schema or the Windows Communication Framework schema depending upon which technology you are targeting.</span></span>  
  
 <span data-ttu-id="598d4-105">本節將著重於基本攔截器組態，包括項目和屬性。</span><span class="sxs-lookup"><span data-stu-id="598d4-105">This section focuses on the base interceptor configuration including elements and attributes.</span></span> <span data-ttu-id="598d4-106">其他功能則由採用特定技術的攔截器提供，將另闢章節說明。</span><span class="sxs-lookup"><span data-stu-id="598d4-106">Additional functionality is provided by the technology-specific interceptors and are explained in separate sections.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="598d4-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="598d4-107">In This Section</span></span>  
  
-   [<span data-ttu-id="598d4-108">使用 IntelliSense 建立攔截器組態檔</span><span class="sxs-lookup"><span data-stu-id="598d4-108">Using IntelliSense to Create an Interceptor Configuration File</span></span>](../core/using-intellisense-to-create-an-interceptor-configuration-file.md)  
  
-   [<span data-ttu-id="598d4-109">攔截器組態結構描述</span><span class="sxs-lookup"><span data-stu-id="598d4-109">Interceptor Configuration Schema</span></span>](../core/interceptor-configuration-schema.md)  
  
-   [<span data-ttu-id="598d4-110">攔截器組態檔的結構</span><span class="sxs-lookup"><span data-stu-id="598d4-110">Structure of an Interceptor Configuration File</span></span>](../core/structure-of-an-interceptor-configuration-file.md)  
  
## <a name="see-also"></a><span data-ttu-id="598d4-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="598d4-111">See Also</span></span>  
 <span data-ttu-id="598d4-112">[BAM WF 攔截器](../core/bam-wf-interceptor.md) </span><span class="sxs-lookup"><span data-stu-id="598d4-112">[BAM WF Interceptor](../core/bam-wf-interceptor.md) </span></span>  
 [<span data-ttu-id="598d4-113">BAM WCF 攔截器</span><span class="sxs-lookup"><span data-stu-id="598d4-113">BAM WCF Interceptor</span></span>](../core/bam-wcf-interceptor.md)