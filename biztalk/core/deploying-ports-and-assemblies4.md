---
title: "部署連接埠和 Assemblies4 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying assemblies
- ports, deploying
- Deployment Wizard
- deploying ports
- assemblies, deploying
- deployment, ports and assemblies
ms.assetid: 5a94a2c8-748c-4d1c-a87e-1cd763565886
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b83df400cba64ee55cab230826bf5bf75b1bca69
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-ports-and-assemblies"></a><span data-ttu-id="d12ab-102">部署連接埠和組件</span><span class="sxs-lookup"><span data-stu-id="d12ab-102">Deploying Ports and Assemblies</span></span>
<span data-ttu-id="d12ab-103">您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在目標電腦上複製連接埠和組件。</span><span class="sxs-lookup"><span data-stu-id="d12ab-103">Using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer.</span></span> <span data-ttu-id="d12ab-104">BizTalk Server 會將傳送埠/接收位置組態匯出到 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="d12ab-104">BizTalk Server exports the send ports/receive location configuration into an XML file.</span></span>  
  
 <span data-ttu-id="d12ab-105">您可以使用 BizTalk Server 執行以下工作：</span><span class="sxs-lookup"><span data-stu-id="d12ab-105">You can use BizTalk Server to do the following tasks:</span></span>  
  
-   <span data-ttu-id="d12ab-106">在 BizTalk 組態資料庫中部署或移除 BizTalk Server 組件</span><span class="sxs-lookup"><span data-stu-id="d12ab-106">Deploy or remove BizTalk Server assemblies in a BizTalk Configuration database</span></span>  
  
-   <span data-ttu-id="d12ab-107">在全域組件快取 (GAC) 中安裝或解除安裝組件</span><span class="sxs-lookup"><span data-stu-id="d12ab-107">Install or uninstall the assemblies in the global assembly cache (GAC)</span></span>  
  
-   <span data-ttu-id="d12ab-108">將 BizTalk Server 組件繫結資訊匯入到繫結檔案，或是將它從繫結檔案中匯出</span><span class="sxs-lookup"><span data-stu-id="d12ab-108">Import or export BizTalk Server assembly binding information to and from binding files</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d12ab-109">Microsoft BizTalk Adapter for JD Edwards OneWorld 只要求來源 (部署) 電腦上必須有 Visual Studio；</span><span class="sxs-lookup"><span data-stu-id="d12ab-109">The Microsoft BizTalk Adapter for JD Edwards OneWorld only requires that you have Visual Studio on a source (development) computer.</span></span> <span data-ttu-id="d12ab-110">實際執行電腦上不需要有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="d12ab-110">Visual Studio is not required on the production computer.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d12ab-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="d12ab-111">In This Section</span></span>  
  
-   [<span data-ttu-id="d12ab-112">匯入繫結檔案</span><span class="sxs-lookup"><span data-stu-id="d12ab-112">Importing Binding Files</span></span>](../core/importing-binding-files3.md)  
  
-   [<span data-ttu-id="d12ab-113">部署限制</span><span class="sxs-lookup"><span data-stu-id="d12ab-113">Deployment Limitations</span></span>](../core/deployment-limitations2.md)