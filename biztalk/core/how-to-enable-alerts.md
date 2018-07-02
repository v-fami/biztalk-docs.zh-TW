---
title: 如何啟用警示 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Enable-Alerts command [BAM]
- managing [BAM definitions], enabling alerts
- alerts, enabling
ms.assetid: 18f494b7-54fb-4aaf-89d1-7e3fe91f35c6
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9fee863613feea040e05856d8246f94b4a3f835
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969151"
---
# <a name="how-to-enable-alerts"></a><span data-ttu-id="bc785-102">如何啟用警示</span><span class="sxs-lookup"><span data-stu-id="bc785-102">How to Enable Alerts</span></span>
<span data-ttu-id="bc785-103">系統管理員可以使用**啟用警示**命令以啟用所有指定的檢視上的警示。</span><span class="sxs-lookup"><span data-stu-id="bc785-103">Administrators use the **enable-alerts** command to enable all of the alerts on the specified view.</span></span>  
  
### <a name="to-enable-an-alert"></a><span data-ttu-id="bc785-104">若要啟用警示</span><span class="sxs-lookup"><span data-stu-id="bc785-104">To enable an alert</span></span>  
  
1. <span data-ttu-id="bc785-105">開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="bc785-105">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="bc785-106">在命令提示字元中，輸入 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking，以瀏覽至追蹤資料夾。</span><span class="sxs-lookup"><span data-stu-id="bc785-106">Navigate to the tracking folder by typing [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking at the command prompt.</span></span> <span data-ttu-id="bc785-107">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="bc785-107">Press **ENTER**.</span></span>  
  
3. <span data-ttu-id="bc785-108">型別**bm 啟用警示-檢視：\<檢視表名稱\>**。</span><span class="sxs-lookup"><span data-stu-id="bc785-108">Type **bm enable-alerts -View:\<view name\>**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="bc785-109">如果您有匯出 BAM 組態為 XML，不會修改與警示相關的 XML。</span><span class="sxs-lookup"><span data-stu-id="bc785-109">If you have exported a BAM configuration as XML, do not modify the XML related to alerts.</span></span> <span data-ttu-id="bc785-110">如果您變更與警示相關的 XML，且又部署變更，bm.exe 將會偵測到該變更並啟用 BAM 警示。</span><span class="sxs-lookup"><span data-stu-id="bc785-110">If you change XML related to alerts and deploy the changes, bm.exe will detect the change and enable BAM alerts.</span></span>  
  
4. <span data-ttu-id="bc785-111">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="bc785-111">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc785-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc785-112">See Also</span></span>  
 <span data-ttu-id="bc785-113">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="bc785-113">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="bc785-114">[BAM 管理公用程式](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="bc785-114">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 [<span data-ttu-id="bc785-115">在此輸入連結描述</span><span class="sxs-lookup"><span data-stu-id="bc785-115">enter link description here</span></span>](../core/how-to-disable-alerts.md)