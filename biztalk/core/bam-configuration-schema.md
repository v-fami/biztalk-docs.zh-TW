---
title: BAM 組態結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [BAM], scaling
- scaling, BAM
- BAM, scaling
- configuration schema [BAM]
ms.assetid: 7eeeb07f-012e-44eb-a8b5-06e374946e2d
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b0d73435dc0245c3c3ce2b1574aa5a70b468c60
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230222"
---
# <a name="bam-configuration-schema"></a><span data-ttu-id="3ba17-102">BAM 組態結構描述</span><span class="sxs-lookup"><span data-stu-id="3ba17-102">BAM Configuration Schema</span></span>
<span data-ttu-id="3ba17-103">BAM 組態結構描述定義了 XML 文件，其中包含 BAM 管理公用程式用以部署的基礎結構之相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3ba17-103">The BAM configuration schema defines an XML document that contains information about your infrastructure that the BAM Manager Utility uses for deployment.</span></span> <span data-ttu-id="3ba17-104">您可以將資料庫部署至多部伺服器以獲致延展性。</span><span class="sxs-lookup"><span data-stu-id="3ba17-104">You can deploy your databases to multiple servers for scalability.</span></span> <span data-ttu-id="3ba17-105">為了支援此延展性，請確定 BAM 組態 XML 文件中包含了個別的伺服器名稱，以及下列資料庫的組態設定：</span><span class="sxs-lookup"><span data-stu-id="3ba17-105">To support this scalability, ensure that the BAM configuration XML document contains the different server names and configuration settings for the following databases:</span></span>  
  
-   <span data-ttu-id="3ba17-106">BAMPrimaryImport</span><span class="sxs-lookup"><span data-stu-id="3ba17-106">BAMPrimaryImport</span></span>  
  
-   <span data-ttu-id="3ba17-107">BAMStarSchema</span><span class="sxs-lookup"><span data-stu-id="3ba17-107">BAMStarSchema</span></span>  
  
-   <span data-ttu-id="3ba17-108">BAMAnalysis</span><span class="sxs-lookup"><span data-stu-id="3ba17-108">BAMAnalysis</span></span>  
  
-   <span data-ttu-id="3ba17-109">BAMArchive</span><span class="sxs-lookup"><span data-stu-id="3ba17-109">BAMArchive</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3ba17-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="3ba17-110">In This Section</span></span>  
  
-   [<span data-ttu-id="3ba17-111">BAM DTS 封裝</span><span class="sxs-lookup"><span data-stu-id="3ba17-111">BAM DTS Packages</span></span>](../core/bam-dts-packages.md)  
  
## <a name="see-also"></a><span data-ttu-id="3ba17-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ba17-112">See Also</span></span>  
 [<span data-ttu-id="3ba17-113">變更 BAM 執行階段設定</span><span class="sxs-lookup"><span data-stu-id="3ba17-113">Changing BAM Runtime Settings</span></span>](../core/changing-bam-runtime-settings.md)