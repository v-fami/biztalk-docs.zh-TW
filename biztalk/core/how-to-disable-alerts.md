---
title: "如何停用警示 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- alerts, disabling
- managing [BAM definitions], disabling alerts
- Disable-Alerts command [BAM]
ms.assetid: c5938bc2-1043-4633-8cad-02caf442f2e8
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0252fc98cdf792626094ffee75fae95c1cab3b00
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-disable-alerts"></a><span data-ttu-id="659e7-102">如何停用警示</span><span class="sxs-lookup"><span data-stu-id="659e7-102">How to Disable Alerts</span></span>
<span data-ttu-id="659e7-103">系統管理員使用**停用警示**命令以停用所有指定之檢視上的警示。</span><span class="sxs-lookup"><span data-stu-id="659e7-103">Administrators use the **disable-alerts** command to disable all of the alerts on the specified view.</span></span>  
  
### <a name="to-disable-an-alert"></a><span data-ttu-id="659e7-104">若要停用警示</span><span class="sxs-lookup"><span data-stu-id="659e7-104">To disable an alert</span></span>  
  
1.  <span data-ttu-id="659e7-105">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="659e7-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="659e7-106">在命令提示字元中，輸入 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking，以瀏覽至追蹤資料夾。</span><span class="sxs-lookup"><span data-stu-id="659e7-106">Navigate to the tracking folder by typing [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking at the command prompt.</span></span> <span data-ttu-id="659e7-107">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="659e7-107">Press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="659e7-108">型別**bm 停用警示的檢視：\<檢視名稱 >**。</span><span class="sxs-lookup"><span data-stu-id="659e7-108">Type **bm disable-alerts -View:\<view name>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="659e7-109">如果您匯出 BAM 組態 xml，不會修改與警示相關的 XML。</span><span class="sxs-lookup"><span data-stu-id="659e7-109">If you have exported a BAM configuration as XML, do not modify the XML related to alerts.</span></span> <span data-ttu-id="659e7-110">如果您變更與警示相關的 XML，且又部署變更，bm.exe 將會偵測到該變更並啟用 BAM 警示。</span><span class="sxs-lookup"><span data-stu-id="659e7-110">If you change XML related to alerts and deploy the changes, bm.exe will detect the change and enable BAM alerts.</span></span>  
  
4.  <span data-ttu-id="659e7-111">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="659e7-111">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="659e7-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="659e7-112">See Also</span></span>  
 <span data-ttu-id="659e7-113">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="659e7-113">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="659e7-114">[BAM 管理公用程式](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="659e7-114">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 [<span data-ttu-id="659e7-115">如何啟用警示</span><span class="sxs-lookup"><span data-stu-id="659e7-115">How to Enable Alerts</span></span>](../core/how-to-enable-alerts.md)