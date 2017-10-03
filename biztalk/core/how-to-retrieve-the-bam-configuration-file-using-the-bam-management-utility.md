---
title: "如何擷取 BAM 組態檔使用 BAM 管理公用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67ce5e0c-467a-486c-8eec-217a2a26d7b4
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0eb7dee70d3a5b8dc7226203df9f48aefe1d5fc0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-retrieve-the-bam-configuration-file-using-the-bam-management-utility"></a><span data-ttu-id="fec92-102">如何使用 BAM 管理公用程式擷取 BAM 組態檔</span><span class="sxs-lookup"><span data-stu-id="fec92-102">How to Retrieve the BAM Configuration File Using the BAM Management Utility</span></span>
<span data-ttu-id="fec92-103">系統管理員和開發人員可以使用 BAM 管理公用程式，擷取目前的 BAM 基礎結構組態。</span><span class="sxs-lookup"><span data-stu-id="fec92-103">Administrators and developers can use the BAM Management utility to retrieve the current configuration of the BAM infrastructure.</span></span> <span data-ttu-id="fec92-104">擷取的組態可以用來將 BAM 安裝移轉到新的伺服器，或可以修改並使用此組態更新現有的 BAM 安裝。</span><span class="sxs-lookup"><span data-stu-id="fec92-104">The retrieved configuration can be used to migrate a BAM installation to a new server or it can be modified and used to update an existing BAM installation.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fec92-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="fec92-105">Prerequisites</span></span>  
 <span data-ttu-id="fec92-106">以下是執行此主題中之程序的必要條件：</span><span class="sxs-lookup"><span data-stu-id="fec92-106">The following are prerequisites for performing the procedure in this topic:</span></span>  
  
-   <span data-ttu-id="fec92-107">以設定的 BAM 資料庫</span><span class="sxs-lookup"><span data-stu-id="fec92-107">Configured BAM databases</span></span>  
  
-   <span data-ttu-id="fec92-108">讀取 BAM 主要匯入資料庫的權限</span><span class="sxs-lookup"><span data-stu-id="fec92-108">Permissions to read the BAM Primary Import database</span></span>  
  
### <a name="to-retrieve-the-bam-configuration-file-using-the-bam-management-utility"></a><span data-ttu-id="fec92-109">使用 BAM 管理公用程式擷取 BAM 組態檔</span><span class="sxs-lookup"><span data-stu-id="fec92-109">To retrieve the BAM configuration file using the BAM Management utility</span></span>  
  
1.  <span data-ttu-id="fec92-110">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="fec92-110">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="fec92-111">瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。</span><span class="sxs-lookup"><span data-stu-id="fec92-111">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="fec92-112">在命令提示字元輸入下列命令： **bm get-config-FileName:\<輸出檔 >**，其中\<*輸出檔*> 取代為您的 BAM 組態的名稱檔案。</span><span class="sxs-lookup"><span data-stu-id="fec92-112">Type the following at the command line prompt: **bm get-config -FileName:\<output file>**, where \<*output file*> is replaced by the name of your BAM configuration file.</span></span> <span data-ttu-id="fec92-113">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="fec92-113">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fec92-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fec92-114">See Also</span></span>  
 [<span data-ttu-id="fec92-115">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="fec92-115">BAM Management Utility</span></span>](../core/bam-management-utility.md)