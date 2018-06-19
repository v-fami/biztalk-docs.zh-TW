---
title: 如何顯示管理組件的覆寫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8261a514-b4c4-4e6b-ac35-40a3e3e090e0
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a28c4ab2ef8f82fdd770203816239ad78e74418e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22297686"
---
# <a name="how-to-display-overrides-for-a-management-pack"></a><span data-ttu-id="1f52d-102">如何顯示管理組件的覆寫</span><span class="sxs-lookup"><span data-stu-id="1f52d-102">How to Display Overrides for a Management Pack</span></span>
<span data-ttu-id="1f52d-103">若要顯示的管理組件，請使用下列程序。</span><span class="sxs-lookup"><span data-stu-id="1f52d-103">To display overrides for a management pack, use the following procedure.</span></span>  
  
### <a name="to-display-overrides-for-a-management-pack"></a><span data-ttu-id="1f52d-104">若要顯示覆寫管理組件</span><span class="sxs-lookup"><span data-stu-id="1f52d-104">To display overrides for a management pack</span></span>  
  
1.  <span data-ttu-id="1f52d-105">在 管理伺服器中，按一下 **程式**，然後按一下  **System Center**。</span><span class="sxs-lookup"><span data-stu-id="1f52d-105">In your management server, click **Programs**, and then click **System Center**.</span></span>  
  
2.  <span data-ttu-id="1f52d-106">按一下**命令殼層**。</span><span class="sxs-lookup"><span data-stu-id="1f52d-106">Click **Command Shell**.</span></span>  
  
3.  <span data-ttu-id="1f52d-107">在命令殼層中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="1f52d-107">In the Command Shell, type the following command:</span></span>   
    `$mp = get-scommanagementpack -DisplayName "Operations Manager Internal Library"`   
    `$mp.GetOverrides()`  
  
4.  <span data-ttu-id="1f52d-108">建立.csv 檔案。</span><span class="sxs-lookup"><span data-stu-id="1f52d-108">A .csv file is created.</span></span> <span data-ttu-id="1f52d-109">此.csv 檔案可以在 Office Excel 中開啟。</span><span class="sxs-lookup"><span data-stu-id="1f52d-109">The .csv file can be opened in Office Excel.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1f52d-110">在 Office Excel 時，您可能需要指定此.csv 檔案為文字檔。</span><span class="sxs-lookup"><span data-stu-id="1f52d-110">In Office Excel, you may be required to specify that the .csv file is a text file.</span></span>  
  
 <span data-ttu-id="1f52d-111">例如，下列命令會顯示其中一個核心管理組件的覆寫：</span><span class="sxs-lookup"><span data-stu-id="1f52d-111">For example, the following command displays the overrides for one of the core management packs:</span></span>   
`$mp = get-scommanagementpack -DisplayName "Contoso.BizTalk.Overrides.mp"`  
`$mp.GetOverrides()`