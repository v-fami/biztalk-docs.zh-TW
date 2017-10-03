---
title: "自動化 BizTalk Server 效能調整 |Microsoft 文件"
description: "使用 BTSTask 匯入或匯出 BizTalk Server 中的環境之間的效能設定"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07ff73b5-25d9-4f3f-9a4b-127c0b843741
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e4ea364345ed9f2a8f642e11650cfcd9d09f10f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="automate-biztalk-server-performance-tuning"></a><span data-ttu-id="78894-103">自動化 BizTalk Server 效能調整</span><span class="sxs-lookup"><span data-stu-id="78894-103">Automate BizTalk Server Performance Tuning</span></span>

## <a name="overview"></a><span data-ttu-id="78894-104">概觀</span><span class="sxs-lookup"><span data-stu-id="78894-104">Overview</span></span>
<span data-ttu-id="78894-105">您可以自動調整[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能設定匯入或匯出 BizTalk 設定，或藉由操作使用的設定[WMI](http://go.microsoft.com/fwlink/?LinkId=200464)。</span><span class="sxs-lookup"><span data-stu-id="78894-105">You can automate the tuning of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performance settings either by importing or exporting the BizTalk settings or by manipulating the settings using [WMI](http://go.microsoft.com/fwlink/?LinkId=200464).</span></span>  
  
 <span data-ttu-id="78894-106">在針對最佳效能設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境後，您可以將 BizTalk Server 設定匯出或匯入至 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="78894-106">After the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment is set up for optimum performance, you can export or import the BizTalk Server settings to an XML file.</span></span> <span data-ttu-id="78894-107">您可以使用「設定儀表板」或 BTSTask 命令列公用程式來匯入/匯出 BizTalk Server 設定。</span><span class="sxs-lookup"><span data-stu-id="78894-107">You can import/export the BizTalk Server settings either using the Settings Dashboard or the BTSTask command-line utility.</span></span> <span data-ttu-id="78894-108">**BTSTask.exe**與[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可讓 BizTalk 系統管理員建立新的指令碼時使用 BTSTask 命令。</span><span class="sxs-lookup"><span data-stu-id="78894-108">**BTSTask.exe** with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] allows BizTalk administrators to use BTSTask commands when creating new scripts.</span></span>  
  
 <span data-ttu-id="78894-109">如需匯入/匯出 BizTalk Server 設定資訊從一個環境到另一個使用[!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)]，請參閱[匯入或匯出 BizTalk 設定使用設定儀表板](how-to-import-biztalk-settings-using-settings-dashboard.md)。</span><span class="sxs-lookup"><span data-stu-id="78894-109">For information about importing/exporting BizTalk Server settings from one environment to another using [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)], see [Import or export BizTalk Settings Using Settings Dashboard](how-to-import-biztalk-settings-using-settings-dashboard.md).</span></span> 
  
## <a name="next-steps"></a><span data-ttu-id="78894-110">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="78894-110">Next steps</span></span> 
  
-   [<span data-ttu-id="78894-111">匯入或匯出 BizTalk 設定使用 BTSTask</span><span class="sxs-lookup"><span data-stu-id="78894-111">Import or export BizTalk Settings Using BTSTask</span></span>](../core/how-to-import-biztalk-settings-using-btstask.md)  
  
- [<span data-ttu-id="78894-112">BTSTask 命令列參考</span><span class="sxs-lookup"><span data-stu-id="78894-112">BTSTask Command-Line Reference</span></span>](btstask-command-line-reference.md)
  
## <a name="see-also"></a><span data-ttu-id="78894-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78894-113">See Also</span></span>  
 [<span data-ttu-id="78894-114">管理 BizTalk Server 效能設定</span><span class="sxs-lookup"><span data-stu-id="78894-114">Managing BizTalk Server Performance Settings</span></span>](../core/managing-biztalk-server-performance-settings.md)