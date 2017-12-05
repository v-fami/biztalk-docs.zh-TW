---
title: "如何變更警示的頻率會評估 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68f326ed-2017-4853-89b9-146cb0785554
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f921699e9a98724c8ca2c36f99d7eb9b9848875
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-change-the-frequency-with-which-alerts-are-evaluated"></a><span data-ttu-id="9a21c-102">如何變更評估警示的頻率</span><span class="sxs-lookup"><span data-stu-id="9a21c-102">How to Change the Frequency With Which Alerts Are Evaluated</span></span>
<span data-ttu-id="9a21c-103">以預設設定部署時，有時候 SQL Notification Services 產生器可能無法跟上 BAM 事件提供者引發事件的速度。</span><span class="sxs-lookup"><span data-stu-id="9a21c-103">There are cases in which the SQL Notifications services generator may not keep up with events being raised by the BAM event provider when deployed with the default settings.</span></span> <span data-ttu-id="9a21c-104">您可以修改 Notification Services 的 adf.xml 檔案，針對警示增加評估事件的頻率 (配量持續時間)。</span><span class="sxs-lookup"><span data-stu-id="9a21c-104">You can increase the frequency (the quantum duration) with which events are evaluated for alerts by modifying the Notification Services adf.xml file.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9a21c-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="9a21c-105">Prerequisites</span></span>  
 <span data-ttu-id="9a21c-106">若要執行此程序，您必須以具有「主要匯入」資料庫讀寫權限的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 群組 (通常是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的「系統管理員」群組) 成員登入。</span><span class="sxs-lookup"><span data-stu-id="9a21c-106">To perform this procedure you must be logged on as a member of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group that has permissions to read and write the Primary Import database, typically this will be a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-modify-the-notification-services-generator-quantum-duration"></a><span data-ttu-id="9a21c-107">若要修改 Notification Services 產生器配量持續時間</span><span class="sxs-lookup"><span data-stu-id="9a21c-107">To modify the Notification Services generator quantum duration</span></span>  
  
1.  <span data-ttu-id="9a21c-108">開啟 [Notification Services 命令提示字元]。</span><span class="sxs-lookup"><span data-stu-id="9a21c-108">Open the Notification Services Command prompt.</span></span> <span data-ttu-id="9a21c-109">按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2005**，按一下 **組態工具**，然後按一下  **Notification Services 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="9a21c-109">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2005**, click **Configuration Tools**, and then click **Notification Services Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="9a21c-110">取得 Notification Services 的組態檔。</span><span class="sxs-lookup"><span data-stu-id="9a21c-110">Get the Notification Services configuration file.</span></span> <span data-ttu-id="9a21c-111">在命令提示字元中，輸入： **cscript ProcessBamNSFiles.vbs-Get config.xml adf.xml \<PimaryImport 資料庫伺服器\> \< PimaryImport 資料庫名稱\>**。</span><span class="sxs-lookup"><span data-stu-id="9a21c-111">At the command prompt, type: **cscript ProcessBamNSFiles.vbs -Get config.xml adf.xml \<PimaryImport database server\> \< PimaryImport database name\>**.</span></span>  
  
3.  <span data-ttu-id="9a21c-112">修改或加入\<QuantumDuration\>項目底下\<u\>節點在 adf.xml 檔案中。</span><span class="sxs-lookup"><span data-stu-id="9a21c-112">Modify or add the \<QuantumDuration\> element under the \<ApplicationExecutionSettings\> node in the in the adf.xml file.</span></span> <span data-ttu-id="9a21c-113">如需 QuantumDuration 項目的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=78803](http://go.microsoft.com/fwlink/?LinkId=78803)。</span><span class="sxs-lookup"><span data-stu-id="9a21c-113">For more information on the QuantumDuration element, see [http://go.microsoft.com/fwlink/?LinkId=78803](http://go.microsoft.com/fwlink/?LinkId=78803).</span></span>  
  
4.  <span data-ttu-id="9a21c-114">在命令提示字元中，輸入： **cscript ProcessBamNSFiles.vbs-更新 config.xml adf.xml \<PimaryImport 資料庫伺服器\> \< PimaryImport 資料庫名稱\>。**</span><span class="sxs-lookup"><span data-stu-id="9a21c-114">At the command prompt, type: **cscript ProcessBamNSFiles.vbs -Update  config.xml adf.xml  \<PimaryImport database server\> \< PimaryImport database name\>.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a21c-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="9a21c-115">See Also</span></span>  
 [<span data-ttu-id="9a21c-116">Notification Services 設定檔的 BAM 命令列指令碼</span><span class="sxs-lookup"><span data-stu-id="9a21c-116">BAM Command-Line Script for Notification Services Configuration Files</span></span>](../core/bam-command-line-script-for-notification-services-configuration-files.md)