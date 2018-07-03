---
title: 排除 CertSrv 從受管理的路徑上的單一電腦部署 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managed paths
- certificate server (CertSrv)
- certificates, certificate server (CertSrv)
ms.assetid: 39916663-b80e-49d8-ba9b-49276eb564fc
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1651131369ef4a8e0c4683b82f5b97163e33382f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987839"
---
# <a name="excluding-certsrv-from-managed-paths-on-a-single-computer-deployment"></a><span data-ttu-id="50242-102">從單一電腦部署的受管理路徑中排除 CertSrv</span><span class="sxs-lookup"><span data-stu-id="50242-102">Excluding CertSrv from Managed Paths on a Single-Computer Deployment</span></span>
<span data-ttu-id="50242-103">如果您已部署[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]在單一電腦上也安裝了憑證伺服器的相同電腦上，您需要排除憑證伺服器 (/certsrv) 從 Microsoft SharePoint Server 管理中心 中受管理的路徑。</span><span class="sxs-lookup"><span data-stu-id="50242-103">If you have deployed [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] on a single computer and also installed the certificate server on the same computer, you need to exclude the certificate server (CertSrv) from the managed paths in Microsoft SharePoint Server Central Administration.</span></span>  
  
### <a name="to-exclude-certsrv-from-the-managed-paths"></a><span data-ttu-id="50242-104">若要從受管理的路徑中排除 CertSrv</span><span class="sxs-lookup"><span data-stu-id="50242-104">To exclude CertSrv from the managed paths</span></span>  
  
1.  <span data-ttu-id="50242-105">按一下 **開始**，指向**所有程式**，指向**系統管理工具**，然後按一下**SharePoint 管理中心**。</span><span class="sxs-lookup"><span data-stu-id="50242-105">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **SharePoint Central Administration**.</span></span>  
  
2.  <span data-ttu-id="50242-106">在 [管理中心] 視窗中，在**虛擬伺服器組態**區段中，按一下**設定虛擬伺服器設定**。</span><span class="sxs-lookup"><span data-stu-id="50242-106">In the Central Administration window, in the **Virtual Server Configuration** section, click **Configure virtual server settings**.</span></span>  
  
3.  <span data-ttu-id="50242-107">在 [虛擬伺服器清單] 視窗中，按一下**Default Web Site**。</span><span class="sxs-lookup"><span data-stu-id="50242-107">In the Virtual Server List window, click **Default Web Site**.</span></span>  
  
4.  <span data-ttu-id="50242-108">在 [虛擬伺服器設定] 視窗中，在**虛擬伺服器管理**區段中，按一下**定義管理的路徑**。</span><span class="sxs-lookup"><span data-stu-id="50242-108">In the Virtual Server Settings window, in the **Virtual Server Management** section, click **Define managed paths**.</span></span>  
  
5.  <span data-ttu-id="50242-109">在 [定義管理的路徑] 視窗中，在**加入新路徑**區段中，輸入**CertSrv**中**路徑**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="50242-109">In the Define Managed Paths window, in the **Add a New Path** section, enter **CertSrv** in the **Path** text box.</span></span> <span data-ttu-id="50242-110">在 **型別**區段中，按一下**排除的路徑**。</span><span class="sxs-lookup"><span data-stu-id="50242-110">In the **Type** section, click **Excluded Path**.</span></span> <span data-ttu-id="50242-111">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="50242-111">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="50242-112">關閉 [定義管理的路徑] 視窗。</span><span class="sxs-lookup"><span data-stu-id="50242-112">Close the Define Managed Paths window.</span></span>