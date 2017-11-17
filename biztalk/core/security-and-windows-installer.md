---
title: "安全性和 Windows Installer |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, Windows installer
- Windows installer
ms.assetid: efa68c3e-2006-4665-bd41-07defaf4e2e2
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4418994a4b5ff705d1faef751ac8c96ba86f9dc7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="security-and-windows-installer"></a><span data-ttu-id="a5160-102">安全性與 Windows Installer</span><span class="sxs-lookup"><span data-stu-id="a5160-102">Security and Windows Installer</span></span>
<span data-ttu-id="a5160-103">Windows Installer 是強大的工具，可用來安裝和更新 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a5160-103">Windows Installer is a powerful tool for installing and updating BizTalk applications.</span></span> <span data-ttu-id="a5160-104">在使用 Windows Installer 時，您應該注意可能由惡意的 Windows Installer (.msi) 檔案建立者製造的安全性問題，並採取步驟加以防止。</span><span class="sxs-lookup"><span data-stu-id="a5160-104">When using Windows Installer, you should be aware of the security issues that can be created by malicious Windows Installer (.msi) file creators and take steps to prevent them.</span></span>  
  
 <span data-ttu-id="a5160-105">系統管理員通常會執行 .msi 檔案，因此在應用程式安裝或更新期間所執行的程序具有很高的權限。</span><span class="sxs-lookup"><span data-stu-id="a5160-105">Administrators typically run .msi files, and therefore the processes that run during application installation or update have very high privileges.</span></span> <span data-ttu-id="a5160-106">惡意的 .msi 檔案建立者可能會以數種方式利用這項事實，包含以下各項：</span><span class="sxs-lookup"><span data-stu-id="a5160-106">A malicious .msi file creator could exploit this fact in a number of ways, including the following:</span></span>  
  
-   <span data-ttu-id="a5160-107">執行對系統或檔案進行不利變更的指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="a5160-107">Running script files that make undesirable changes to your system or files.</span></span>  
  
-   <span data-ttu-id="a5160-108">覆寫 COM 目錄。</span><span class="sxs-lookup"><span data-stu-id="a5160-108">Overwriting the COM catalog.</span></span>  
  
-   <span data-ttu-id="a5160-109">覆寫登錄值。</span><span class="sxs-lookup"><span data-stu-id="a5160-109">Overwriting registry values.</span></span> <span data-ttu-id="a5160-110">這些變更無法回復。</span><span class="sxs-lookup"><span data-stu-id="a5160-110">These changes cannot be rolled back.</span></span>  
  
-   <span data-ttu-id="a5160-111">灌爆檔案系統。</span><span class="sxs-lookup"><span data-stu-id="a5160-111">Flooding the file system.</span></span>  
  
 <span data-ttu-id="a5160-112">在處理 .msi 檔案時，應該至少考慮下列預防措施：</span><span class="sxs-lookup"><span data-stu-id="a5160-112">When dealing with .msi files, you should take the following precautions at a minimum:</span></span>  
  
-   <span data-ttu-id="a5160-113">只安裝您完全信任的 .msi 檔案。</span><span class="sxs-lookup"><span data-stu-id="a5160-113">Install only .msi files that you completely trust.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a5160-114">最佳作法是由負責產生 .msi 檔案的人員採取額外的步驟來簽署 .msi 檔案，以讓使用者可以確認檔案來源是可信任的。</span><span class="sxs-lookup"><span data-stu-id="a5160-114">As a best practice, individuals who are responsible for generating .msi files should take additional steps to sign the .msi files so that users can verify that the source of the file is trusted.</span></span>  
  
-   <span data-ttu-id="a5160-115">在實際執行環境中使用 .msi 檔案之前，請徹底地加以測試。</span><span class="sxs-lookup"><span data-stu-id="a5160-115">Thoroughly test your .msi files before using them in a production environment.</span></span>  
  
-   <span data-ttu-id="a5160-116">將 .msi 檔案儲存在受保護的資料夾中 (以適當的判別存取控制清單 (DACL) 進行保護)。</span><span class="sxs-lookup"><span data-stu-id="a5160-116">Store the .msi files in protected folders that are secured with appropriate discretionary access control lists (DACLs).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5160-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5160-117">See Also</span></span>  
 [<span data-ttu-id="a5160-118">應用程式部署的安全性考量</span><span class="sxs-lookup"><span data-stu-id="a5160-118">Security Considerations for Application Deployment</span></span>](../core/security-considerations-for-application-deployment.md)