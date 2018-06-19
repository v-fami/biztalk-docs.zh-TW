---
title: 如何將 64 位元成品新增至應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- artifacts, 64-bit support
- scripts, 64-bit support
- virtual directories, 64-bit support
- artifacts, applications
- 64-bit support, COM components
- 64-bit support, virtual directories
- applications, artifacts
- 64-bit support, scripts
- 64-bit support, artifacts
- COM components, 64-bit support
- BizTalk Server, 64-bit support
- applications, 64-bit support
ms.assetid: 46aca7d4-c5be-421e-b16d-7f3095c8cc67
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69707401fee8b7f48b30a79bab166a9f22c29a89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246622"
---
# <a name="how-to-add-a-64-bit-artifact-to-an-application"></a><span data-ttu-id="9c1b7-102">如何將 64 位元成品新增至應用程式</span><span class="sxs-lookup"><span data-stu-id="9c1b7-102">How to Add a 64-Bit Artifact to an Application</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9c1b7-103"> 包含 64 位元應用程式的支援。</span><span class="sxs-lookup"><span data-stu-id="9c1b7-103"> includes support for 64-bit applications.</span></span> <span data-ttu-id="9c1b7-104">這表示您可以用與 32 位元成品相同的方式，將 64 位元成品新增到 BizTalk 應用程式，然而，在 32 位元電腦上安裝下列 64 位元成品時，您可能會遇到下列問題：</span><span class="sxs-lookup"><span data-stu-id="9c1b7-104">This means that you can add 64-bit artifacts to a BizTalk application in the same manner as 32-bit artifacts; however, you may encounter the following issues when installing the following 64-bit artifacts on a 32-bit computer:</span></span>  
  
-   <span data-ttu-id="9c1b7-105">**從 Web 伺服器正在執行的 64 位元工作者處理序的虛擬目錄。**</span><span class="sxs-lookup"><span data-stu-id="9c1b7-105">**Virtual directory from a Web server that is running a 64-bit worker process.**</span></span> <span data-ttu-id="9c1b7-106">這個虛擬目錄會安裝到 32 位元電腦上，不過可能不會正確運作。</span><span class="sxs-lookup"><span data-stu-id="9c1b7-106">The virtual directory will install on a 32-bit computer, but it may not function correctly.</span></span> <span data-ttu-id="9c1b7-107">會記錄一項不相符狀況。</span><span class="sxs-lookup"><span data-stu-id="9c1b7-107">A mismatch will be logged.</span></span>  
  
-   <span data-ttu-id="9c1b7-108">**Unmanaged 的 COM 或 Managed COM + 元件會標示為 64 位元。**</span><span class="sxs-lookup"><span data-stu-id="9c1b7-108">**Unmanaged COM or Managed COM+ components marked as 64 bit.**</span></span> <span data-ttu-id="9c1b7-109">這些元件不會安裝到 32 位元電腦。</span><span class="sxs-lookup"><span data-stu-id="9c1b7-109">These components will not install on a 32-bit computer.</span></span>  
  
-   <span data-ttu-id="9c1b7-110">**64 位元指令碼儲存為.exe 檔案。**</span><span class="sxs-lookup"><span data-stu-id="9c1b7-110">**64-bit scripts saved as .exe files.**</span></span> <span data-ttu-id="9c1b7-111">這種類型的指令碼可能不會正確運作。</span><span class="sxs-lookup"><span data-stu-id="9c1b7-111">This type of script may not function correctly.</span></span>  
  
 <span data-ttu-id="9c1b7-112">如需新增成品的一般指示，請參閱[如何建立或新增成品](../core/how-to-create-or-add-an-artifact.md)。</span><span class="sxs-lookup"><span data-stu-id="9c1b7-112">For general instructions on adding artifacts, see [How to Create or Add an Artifact](../core/how-to-create-or-add-an-artifact.md).</span></span> <span data-ttu-id="9c1b7-113">如需新增特定成品類型的指示，請參閱[管理成品](../core/managing-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="9c1b7-113">For instructions on adding specific artifact types, see [Managing Artifacts](../core/managing-artifacts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c1b7-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c1b7-114">See Also</span></span>  
 <span data-ttu-id="9c1b7-115">[建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md) </span><span class="sxs-lookup"><span data-stu-id="9c1b7-115">[Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md) </span></span>  
 [<span data-ttu-id="9c1b7-116">如何安裝 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="9c1b7-116">How to Install a BizTalk Application</span></span>](../core/how-to-install-a-biztalk-application.md)