---
title: "部署連接埠和 Assemblies1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, deploying
- deployment, ports
- deployment, assemblies
- assemblies, deploying
ms.assetid: e259f7fe-c443-4015-a630-f08220e5437a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf2515cd5ee80f62a55e0b26b33bb93c3685ce6b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-ports-and-assemblies"></a><span data-ttu-id="1308c-102">部署連接埠和組件</span><span class="sxs-lookup"><span data-stu-id="1308c-102">Deploying Ports and Assemblies</span></span>
<span data-ttu-id="1308c-103">您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在目標電腦上複製連接埠和組件。</span><span class="sxs-lookup"><span data-stu-id="1308c-103">Using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer.</span></span> <span data-ttu-id="1308c-104">精靈會將傳送埠/接收位置組態匯出到 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="1308c-104">The wizard exports the send ports/receive location configuration into an XML file.</span></span>  
  
 <span data-ttu-id="1308c-105">您可以使用 BizTalk Server 執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="1308c-105">You use BizTalk Server to do the following tasks:</span></span>  
  
-   <span data-ttu-id="1308c-106">在BizTalk 組態資料庫中部署或移除 BizTalk Server 組件。</span><span class="sxs-lookup"><span data-stu-id="1308c-106">Deploy or remove BizTalk Server assemblies in a BizTalk Configuration database.</span></span>  
  
-   <span data-ttu-id="1308c-107">在全域組件快取 (GAC) 中安裝或解除安裝組件。</span><span class="sxs-lookup"><span data-stu-id="1308c-107">Install or uninstall the assemblies in the global assembly cache (GAC).</span></span>  
  
-   <span data-ttu-id="1308c-108">將 BizTalk Server 組件繫結資訊匯入到繫結檔案，或是將它從繫結檔案中匯出。</span><span class="sxs-lookup"><span data-stu-id="1308c-108">Import or export BizTalk Server assembly binding information to and from binding files.</span></span>  
  
 <span data-ttu-id="1308c-109">如需有關如何使用資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署連接埠和組件，請參閱[如何匯出 BizTalk 應用程式的繫結](../core/how-to-export-bindings-for-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="1308c-109">For information about how to use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to deploy ports and assemblies, see [How to Export Bindings for a BizTalk Application](../core/how-to-export-bindings-for-a-biztalk-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1308c-110">Microsoft BizTalk Adapter for TIBCO Rendezvous 只要求來源 (開發) 電腦上必須有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="1308c-110">Microsoft BizTalk Adapter for TIBCO Rendezvous only requires that you have Visual Studio on a source (development) computer.</span></span> <span data-ttu-id="1308c-111">實際執行電腦上不需要有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="1308c-111">Visual Studio is not required on the production computer.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1308c-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="1308c-112">In This Section</span></span>  
  
-   [<span data-ttu-id="1308c-113">驗證部署設定</span><span class="sxs-lookup"><span data-stu-id="1308c-113">Verifying the Deployment Setup</span></span>](../core/verifying-the-deployment-setup3.md)  
  
-   [<span data-ttu-id="1308c-114">如何清除目標電腦</span><span class="sxs-lookup"><span data-stu-id="1308c-114">How to Clean the Target Computer</span></span>](../core/how-to-clean-the-target-computer1.md)