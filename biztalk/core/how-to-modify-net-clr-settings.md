---
title: "如何修改.NET CLR 設定 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Bts10.settings.HostInstanceCLR
ms.assetid: 085743d8-27a6-4d8b-98c7-bb5b5c75848c
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d134faf06aebbb24cafd716722d63172a5ceb68b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-modify-net-clr-settings"></a>如何修改.NET CLR 設定
若要更新 Windows 與 BizTalk 主控件執行個體相關聯的.NET 執行緒集區中可用的執行緒數目，您可以修改適當的 Common Runtime Language (CLR) Hosting 值使用 BizTalk 設定儀表板。 本主題提供修改這些設定的逐步程序。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行此作業，您必須以 BizTalk Server Administrators 群組的成員身分登入。  
  
### <a name="to-modify-the-net-clr-settings-of-a-host-instance"></a>若要修改主控件執行個體的 .NET CLR 設定  
  
1.  在**BizTalk Server 管理主控台**，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下 **設定**。  
  
2.  在**BizTalk 設定儀表板**對話方塊**主控件執行個體**索引標籤上，按一下 [ **.NET CLR** ] 索引標籤。  
  
3.  執行下列作業，按一下 **套用**以套用所做的修改，並前進到另一個索引標籤。或按一下**確定**以套用變更並結束 設定儀表板。  
  
    |使用|動作|界限值|預設值|升級邏輯|  
    |--------------|----------------|---------------------|-------------------|-------------------|  
    |**主控件執行個體**|從下拉式方塊選取 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段電腦上執行中的主控件執行個體。|-|-|-|  
  
     **執行緒設定**  
  
    |使用|動作|界限值|預設值|升級邏輯|  
    |--------------|----------------|---------------------|-------------------|-------------------|  
    |**最大值。背景工作執行緒**|指定 .NET CLR 工作者執行緒的最大數目。|[工作者執行緒數下限, 500]|25|將主控件執行個體登錄設定移轉至主控件執行個體設定，並忽略 Version、Flavor、Flags 和 MinCompletionPortThreads。|  
    |**工作者執行緒數下限**|指定 .NET CLR 工作者執行緒的最小數目。|[0, 500]|5|將主控件執行個體登錄設定移轉至主控件執行個體設定，並忽略 Version、Flavor、Flags 和 MinCompletionPortThreads。|  
    |**最大值。IO 執行緒**|指定 IO 執行緒的最大數目。|[IO 執行緒數下限, 1000]|250|將主控件執行個體登錄設定移轉至主控件執行個體設定，並忽略 Version、Flavor、Flags 和 MinCompletionPortThreads。|  
    |**最小值。IO 執行緒**|指定 IO 執行緒的最小數目。|[0, 1000]|25|將主控件執行個體登錄設定移轉至主控件執行個體設定，並忽略 Version、Flavor、Flags 和 MinCompletionPortThreads。|  
  
     .NET CLR 設定為每個核心 CPU。  
  
    > [!NOTE]
    >  若要還原預設設定，請按一下**還原預設值**。  
  
    > [!NOTE]
    >  **背景工作執行緒**用來處理佇列的工作項目和**I/O 執行緒**專用的回呼執行緒來處理已完成的非同步 I/O 要求 I/O 完成通訊埠相關聯。  
  
    > [!NOTE]
    >  如果 BizTalk 已升級從舊版中，於 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc$ 值*hostname*\CLR 主控登錄機碼將會設定 設定儀表板。  
  
## <a name="see-also"></a>另請參閱  
 [如何修改主控件執行個體設定](../core/how-to-modify-host-instance-settings.md)