---
title: 如何移除 BAM 定義 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- definitions [BAM], deleting
- deleting, definitions [BAM]
- managing [BAM definitions], deleting definitions
- Remove-All command
ms.assetid: a905f54b-7c55-49b8-809b-030ad65f3e46
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ad47285be2cb3188cc130e07d42204acbb5c7bd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018202"
---
# <a name="how-to-remove-bam-definitions"></a><span data-ttu-id="ef89c-102">如何移除 BAM 定義</span><span class="sxs-lookup"><span data-stu-id="ef89c-102">How to Remove BAM Definitions</span></span>
<span data-ttu-id="ef89c-103">系統管理員可以使用**全部移除**命令以移除所有的檢視與特定的 BAM 定義檔案所需的基礎活動表 BAM 管理公用程式。</span><span class="sxs-lookup"><span data-stu-id="ef89c-103">Administrators use the **remove-all** command of the BAM Management utility to remove all views and underlying activity tables for a particular BAM definition file.</span></span>  
  
### <a name="to-remove-bam-definitions"></a><span data-ttu-id="ef89c-104">移除 BAM 定義</span><span class="sxs-lookup"><span data-stu-id="ef89c-104">To Remove BAM definitions</span></span>  
  
1. <span data-ttu-id="ef89c-105">開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="ef89c-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="ef89c-106">瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。</span><span class="sxs-lookup"><span data-stu-id="ef89c-106">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3. <span data-ttu-id="ef89c-107">型別**bm 全部移除 DefinitionFile:\<def 檔\>**。</span><span class="sxs-lookup"><span data-stu-id="ef89c-107">Type **bm remove-all DefinitionFile:\<def file\>**.</span></span>  
  
4. <span data-ttu-id="ef89c-108">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="ef89c-108">Press ENTER.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef89c-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef89c-109">See Also</span></span>  
 <span data-ttu-id="ef89c-110">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="ef89c-110">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 [<span data-ttu-id="ef89c-111">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="ef89c-111">BAM Management Utility</span></span>](../core/bam-management-utility.md)