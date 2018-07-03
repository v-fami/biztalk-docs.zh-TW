---
title: 將配接器至 BizTalk Server 安裝 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1164468d-75a9-4116-87a6-6055948c198b
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13e810a14fec9b51c0d6b0ef1d7b55db234d0a0b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005623"
---
# <a name="install-the-adapter-into-biztalk-server"></a>將配接器安裝到 BizTalk Server 中
將正確的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 項目寫入登錄之後，必須將配接器新增至 BizTalk 管理資料庫。 配接器新增至此資料庫之後，即是目前所設定要使用的配接器，只要設定正確就可以開始處理訊息。 您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台，將配接器安裝到資料庫中。 在資料庫中安裝配接器之後，請重新啟動主控件執行個體。  

> [!NOTE]
>  為了能在 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 中看見新增的配接器，必須在 HKLM 登錄中正確註冊該配接器，而且必須實作必要的配接器介面。  

### <a name="to-install-the-static-sample-adapter"></a>安裝範例靜態配接器  

1. 按一下 **開始**，指向**所有程式**，指向[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  

2. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按兩下**BizTalk 群組**節點。  

3. 依序展開**平台設定**，然後選取**配接器**。  

4. 以滑鼠右鍵按一下**配接器**，按一下**新增**，然後按一下**配接器**。  

5. 在 **配接器屬性**對話方塊方塊中，執行下列動作。  


   |  使用   |                      以進行此動作                       |
   |-------------|-------------------------------------------------------|
   |    [屬性]     |                   型別**靜態**。                    |
   |   配接器   | 選取 [ **Static dotnetfile]** 從下拉式清單。 |
   | 描述 |            型別**範例靜態配接器**。            |


6. 按一下 [確定] 。  

    靜態配接器現在會出現在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台右邊視窗的配接器清單中。  

### <a name="to-stop-and-restart-the-host-instance"></a>停止並重新啟動主控件執行個體  

1. 按一下 **開始**，指向**所有程式**，指向[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**。  

2. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按兩下**BizTalk 群組**節點。  

3. 依序展開**平台設定**，選取**主機**，然後選取**BizTalkServerApplication**結果窗格中。  

4. 主控件執行個體 （通常是電腦名稱），以滑鼠右鍵按一下，然後按一下**停止**。  

    主控件執行個體狀態會變更為**已停止**。  

5. 在 [結果] 窗格中，以滑鼠右鍵按一下主控件執行個體，然後**啟動**。  

    主控件執行個體狀態會變更為**開始擱置**。 您必須按一下**重新整理**，或以滑鼠右鍵按一下主控件執行個體，然後按一下**重新整理**，以將狀態變更為**執行**。