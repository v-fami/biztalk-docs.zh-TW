---
title: "部署連接埠和 Assemblies2 |Microsoft 文件"
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
ms.assetid: abbc1391-2b90-42a5-a747-416bc517bb39
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74c3cc840b9dca222d1b55e9277b1ffd6cf326db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-ports-and-assemblies"></a><span data-ttu-id="025a1-102">部署連接埠和組件</span><span class="sxs-lookup"><span data-stu-id="025a1-102">Deploying Ports and Assemblies</span></span>
<span data-ttu-id="025a1-103">與[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您可以複製連接埠和組件的目標電腦上。</span><span class="sxs-lookup"><span data-stu-id="025a1-103">With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="025a1-104">匯出至 XML 檔案傳送埠/接收位置組態。</span><span class="sxs-lookup"><span data-stu-id="025a1-104"> exports send ports/receive location configuration into an XML file.</span></span>  
  
 <span data-ttu-id="025a1-105">您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="025a1-105">You can use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to do the following tasks:</span></span>  
  
-   <span data-ttu-id="025a1-106">在 BizTalk 組態資料庫中部署或移除 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組件。</span><span class="sxs-lookup"><span data-stu-id="025a1-106">Deploy or remove [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies in a BizTalk Configuration database.</span></span>  
  
-   <span data-ttu-id="025a1-107">在全域組件快取 (GAC) 中安裝或解除安裝組件。</span><span class="sxs-lookup"><span data-stu-id="025a1-107">Install or uninstall the assemblies in the global assembly cache (GAC).</span></span>  
  
-   <span data-ttu-id="025a1-108">將 BizTalk 組件繫結資訊匯入到繫結檔案，或是將它從繫結檔案中匯出。</span><span class="sxs-lookup"><span data-stu-id="025a1-108">Import or export BizTalk assembly binding information to and from binding files.</span></span>  
  
 <span data-ttu-id="025a1-109">如需有關如何使用資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署連接埠和組件，請參閱[如何匯出 BizTalk 應用程式的繫結](../core/how-to-export-bindings-for-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="025a1-109">For information about how to use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to deploy ports and assemblies, see [How to Export Bindings for a BizTalk Application](../core/how-to-export-bindings-for-a-biztalk-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="025a1-110">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service 只要求來源 (開發) 電腦上必須有 Visual Studio；</span><span class="sxs-lookup"><span data-stu-id="025a1-110">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service only requires that you have Visual Studio on a source (development) computer.</span></span> <span data-ttu-id="025a1-111">實際執行電腦上不需要有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="025a1-111">Visual Studio is not required on the production computer.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="025a1-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="025a1-112">In This Section</span></span>  
  
-   [<span data-ttu-id="025a1-113">驗證部署設定</span><span class="sxs-lookup"><span data-stu-id="025a1-113">Verifying the Deployment Setup</span></span>](../core/verifying-the-deployment-setup2.md)  
  
-   [<span data-ttu-id="025a1-114">如何清除目標電腦</span><span class="sxs-lookup"><span data-stu-id="025a1-114">How to Clean the Target Computer</span></span>](../core/how-to-clean-the-target-computer2.md)  
  
-   [<span data-ttu-id="025a1-115">部署限制</span><span class="sxs-lookup"><span data-stu-id="025a1-115">Deployment Limitations</span></span>](../core/deployment-limitations1.md)