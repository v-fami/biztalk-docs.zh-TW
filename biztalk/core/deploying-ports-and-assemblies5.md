---
title: "部署連接埠和 Assemblies5 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, deploying
- assemblies, deploying
- deployment, ports and assemblies
ms.assetid: 11d980c4-2502-4da2-b505-d7326aae619a
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31df94e2a659fa29e6f21d2bd705de31da3c6b9a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-ports-and-assemblies"></a><span data-ttu-id="34549-102">部署連接埠和組件</span><span class="sxs-lookup"><span data-stu-id="34549-102">Deploying Ports and Assemblies</span></span>
<span data-ttu-id="34549-103">您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在目標電腦上複製連接埠和組件。</span><span class="sxs-lookup"><span data-stu-id="34549-103">Using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="34549-104">傳送埠/接收位置將組態匯出成 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="34549-104"> exports the send ports/receive location configuration into an XML file.</span></span>  
  
 <span data-ttu-id="34549-105">您會使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="34549-105">You use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to perform these tasks:</span></span>  
  
-   <span data-ttu-id="34549-106">在 BizTalk 組態資料庫中部署或移除 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組件。</span><span class="sxs-lookup"><span data-stu-id="34549-106">Deploy or remove [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies in a BizTalk Configuration database.</span></span>  
  
-   <span data-ttu-id="34549-107">在全域組件快取 (GAC) 中安裝或解除安裝組件。</span><span class="sxs-lookup"><span data-stu-id="34549-107">Install or uninstall the assemblies in the global assembly cache (GAC).</span></span>  
  
-   <span data-ttu-id="34549-108">將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組件繫結資訊匯入到繫結檔案，或是將它從繫結檔案中匯出。</span><span class="sxs-lookup"><span data-stu-id="34549-108">Import or export [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assembly binding information to and from binding files.</span></span>  
  
 <span data-ttu-id="34549-109">如需有關如何使用資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署連接埠和組件，請參閱[如何匯出 BizTalk 應用程式的繫結](../core/how-to-export-bindings-for-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="34549-109">For information about how to use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to deploy ports and assemblies, see [How to Export Bindings for a BizTalk Application](../core/how-to-export-bindings-for-a-biztalk-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34549-110">Microsoft BizTalk Adapter for PeopleSoft Enterprise 只要求來源 (開發) 電腦上必須有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="34549-110">The Microsoft BizTalk Adapter for PeopleSoft Enterprise only requires that you have Visual Studio on a source (development) computer.</span></span> <span data-ttu-id="34549-111">實際執行電腦上不需要有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="34549-111">Visual Studio is not required on the production computer.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="34549-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="34549-112">In This Section</span></span>  
  
-   [<span data-ttu-id="34549-113">匯入繫結檔案</span><span class="sxs-lookup"><span data-stu-id="34549-113">Importing Binding Files</span></span>](../core/importing-binding-files1.md)  
  
-   [<span data-ttu-id="34549-114">部署限制</span><span class="sxs-lookup"><span data-stu-id="34549-114">Deployment Limitations</span></span>](../core/deployment-limitations3.md)