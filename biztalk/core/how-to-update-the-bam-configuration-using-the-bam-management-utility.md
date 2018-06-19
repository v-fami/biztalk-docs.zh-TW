---
title: 如何更新 BAM 組態使用 BAM 管理公用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 714a834e-1879-4019-9b54-e511705bd67a
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b08209d3b3a1555bbc674e469ea9f8a4b1f81a9d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25971036"
---
# <a name="how-to-update-the-bam-configuration-using-the-bam-management-utility"></a><span data-ttu-id="79e60-102">如何使用 BAM 管理公用程式更新 BAM 組態</span><span class="sxs-lookup"><span data-stu-id="79e60-102">How to Update the BAM Configuration Using the BAM Management Utility</span></span>
<span data-ttu-id="79e60-103">系統管理員可以使用 BAM 管理公用程式更新現有的 BAM 安裝。</span><span class="sxs-lookup"><span data-stu-id="79e60-103">Administrators can use the BAM Management utility to update an existing BAM installation.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="79e60-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="79e60-104">Prerequisites</span></span>  
 <span data-ttu-id="79e60-105">您必須具有要進行更新之 BAM 資料庫的系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="79e60-105">You must have Administrator permissions on the BAM database being updated.</span></span>  
  
### <a name="to-update-the-bam-configuration-using-the-bam-management-utility"></a><span data-ttu-id="79e60-106">使用 BAM 管理公用程式更新 BAM 組態</span><span class="sxs-lookup"><span data-stu-id="79e60-106">To update the BAM configuration using the BAM Management utility</span></span>  
  
1.  <span data-ttu-id="79e60-107">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="79e60-107">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="79e60-108">瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。</span><span class="sxs-lookup"><span data-stu-id="79e60-108">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="79e60-109">在命令提示字元輸入下列命令： **bm 更新-config-FileName:\<組態檔\>**，其中\<*組態檔*\>是取代為您的 BAM 組態檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="79e60-109">Type the following at the command line prompt: **bm update-config -FileName:\<config file\>**, where \<*configuration file*\> is replaced by the name of your BAM configuration file.</span></span> <span data-ttu-id="79e60-110">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="79e60-110">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79e60-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="79e60-111">See Also</span></span>  
 [<span data-ttu-id="79e60-112">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="79e60-112">BAM Management Utility</span></span>](../core/bam-management-utility.md)