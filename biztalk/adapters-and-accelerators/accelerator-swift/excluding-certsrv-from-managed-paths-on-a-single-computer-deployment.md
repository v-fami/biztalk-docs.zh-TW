---
title: "排除 CertSrv 從受管理的路徑上的單一電腦部署 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed paths
- certificate server (CertSrv)
- certificates, certificate server (CertSrv)
ms.assetid: 39916663-b80e-49d8-ba9b-49276eb564fc
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c77fc1733859cd903bafcebc26162323feff82d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="excluding-certsrv-from-managed-paths-on-a-single-computer-deployment"></a><span data-ttu-id="3d4ec-102">從單一電腦部署受管理的路徑排除 CertSrv</span><span class="sxs-lookup"><span data-stu-id="3d4ec-102">Excluding CertSrv from Managed Paths on a Single-Computer Deployment</span></span>
<span data-ttu-id="3d4ec-103">如果您已部署[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]在單一電腦上，而且也安裝憑證伺服器的相同電腦上，您需要從受管理的路徑中排除憑證伺服器 (CertSrv) [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] SharePoint Server 管理中心。</span><span class="sxs-lookup"><span data-stu-id="3d4ec-103">If you have deployed [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] on a single computer and also installed the certificate server on the same computer, you need to exclude the certificate server (CertSrv) from the managed paths in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] SharePoint Server Central Administration.</span></span>  
  
### <a name="to-exclude-certsrv-from-the-managed-paths"></a><span data-ttu-id="3d4ec-104">若要從受管理的路徑排除 CertSrv</span><span class="sxs-lookup"><span data-stu-id="3d4ec-104">To exclude CertSrv from the managed paths</span></span>  
  
1.  <span data-ttu-id="3d4ec-105">按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，然後按一下**SharePoint 管理中心內**。</span><span class="sxs-lookup"><span data-stu-id="3d4ec-105">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **SharePoint Central Administration**.</span></span>  
  
2.  <span data-ttu-id="3d4ec-106">在 [管理中心] 視窗中**虛擬伺服器設定**區段中，按一下**設定虛擬伺服器設定**。</span><span class="sxs-lookup"><span data-stu-id="3d4ec-106">In the Central Administration window, in the **Virtual Server Configuration** section, click **Configure virtual server settings**.</span></span>  
  
3.  <span data-ttu-id="3d4ec-107">在 [虛擬伺服器清單] 視窗中，按一下**Default Web Site**。</span><span class="sxs-lookup"><span data-stu-id="3d4ec-107">In the Virtual Server List window, click **Default Web Site**.</span></span>  
  
4.  <span data-ttu-id="3d4ec-108">在 [虛擬伺服器設定] 視窗中**虛擬伺服器管理**區段中，按一下**定義管理的路徑**。</span><span class="sxs-lookup"><span data-stu-id="3d4ec-108">In the Virtual Server Settings window, in the **Virtual Server Management** section, click **Define managed paths**.</span></span>  
  
5.  <span data-ttu-id="3d4ec-109">在 [定義管理的路徑] 視窗中**新增路徑**區段中，輸入**CertSrv**中**路徑**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="3d4ec-109">In the Define Managed Paths window, in the **Add a New Path** section, enter **CertSrv** in the **Path** text box.</span></span> <span data-ttu-id="3d4ec-110">在**類型**區段中，按一下**排除的路徑**。</span><span class="sxs-lookup"><span data-stu-id="3d4ec-110">In the **Type** section, click **Excluded Path**.</span></span> <span data-ttu-id="3d4ec-111">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="3d4ec-111">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="3d4ec-112">關閉 [定義管理的路徑] 視窗。</span><span class="sxs-lookup"><span data-stu-id="3d4ec-112">Close the Define Managed Paths window.</span></span>