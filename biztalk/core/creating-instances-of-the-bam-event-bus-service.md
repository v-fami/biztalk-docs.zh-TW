---
title: 建立 BAM 事件匯流排服務的執行個體 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 454bdde7-45a6-41ab-9196-f662273f0f2b
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: daf847afc8f5c1d284a8266d70006a0f43508ed9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983999"
---
# <a name="creating-instances-of-the-bam-event-bus-service"></a>建立 BAM 事件匯流排服務的執行個體
BAM 事件匯流排服務是在 BizTalk 應用程式主控件內執行。 您可以使用預設主控件來裝載 BAM 事件匯流排服務，或自行建立新主控件。 如果主控件裝載 BAM 事件匯流排服務，您爲該主控件所建立的任何新執行個體也都將裝載服務。  
  
 如需預設主控件的資訊，請參閱[主機](../core/hosts.md)。  
  
 如需建立主控件的資訊，請參閱[如何建立新的主控件](../core/how-to-create-a-new-host.md)。  
  
 如需建立主控件執行個體的資訊，請參閱[如何新增主控件執行個體](../core/how-to-add-a-host-instance.md)。  
  
 建立和設定主控件和主控件執行個體的相關資訊，請參閱[管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md)。  
  
### <a name="to-create-the-host-that-hosts-the-bam-event-bus-service"></a>若要建立裝載 BAM 事件匯流排服務的主控件  
  
1. 按一下 **開始**，指向**所有程式**，按一下  **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在 BizTalk 管理主控台 視窗中，依序展開**BizTalk Server 管理**節點，展開**Biztalk 群組**節點，展開**平台設定**節點以滑鼠右鍵按一下**主機**節點中，選取**新增**，然後按一下**主機**。  
  
3. 在 **主機內容**對話方塊中，於**名稱**方塊中，輸入主機的描述性名稱。  
  
4. 在 **一般**索引標籤上，選取**允許主控件追蹤**核取方塊。  
  
    新的子節點會顯示在**主機**與新的主控件名稱的節點。  
  
5. 在  **Windows 群組**方塊中，輸入要指派此主控件，然後按一下 Windows 群組的名稱**確定**。  
  
    新的子節點會顯示在**主機**與新的主控件名稱的節點。  
  
### <a name="to-create-a-new-host-instance-of-the-host"></a>若要為主控件建立新的主控件執行個體  
  
1.  以滑鼠右鍵按一下**主控件執行個體**節點中，選取**新增**，然後按一下**主控件執行個體**。  
  
2.  選取伺服器主控件執行個體將會執行，然後按一下**確定**。  
  
### <a name="to-add-hosting-tracking-to-the-host"></a>若要為主控件新增裝載追蹤  
  
1.  以滑鼠右鍵按一下您想要重新設定，然後按一下 的主機**屬性**。  
  
2.  在上**一般**索引標籤上，選取**允許主控件追蹤**，然後按一下**確定**。  
  
3.  重新啟動該主控件的所有執行個體。  
  
### <a name="to-remove-hosting-tracking-from-the-host"></a>若要從主控件移除裝載追蹤  
  
1.  以滑鼠右鍵按一下您要從中移除主控件追蹤，主應用的程式，然後按一下**屬性**。  
  
2.  清除**允許主控件追蹤**核取方塊，然後按一下**確定**。  
  
3.  重新啟動該主控件的執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM 事件匯流排服務](../core/managing-the-bam-event-bus-service.md)   
 [BAM 安全性建議](../core/bam-security-recommendations.md)   
 [商務活動監控 (BAM)](../core/business-activity-monitoring-bam.md)