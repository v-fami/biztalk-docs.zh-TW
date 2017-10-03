---
title: "管理 BizTalk 主控件和主控件執行個體 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [hosts]
- hosts, managing
- managing [hosts], about managing hosts
ms.assetid: 7f329804-ca44-4799-8a5d-38b3146d8e5e
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e60981f69bc3ff71bdd8581659f9cdd20f87467
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="managing-biztalk-hosts-and-host-instances"></a>管理 BizTalk 主控件和主控件執行個體
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 主控件是一組零個以上 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段程序的邏輯集，您可以在其中部署如配接器處理常式、接收位置 (包括管線)，以及協調流程等項目。 如需主控件的詳細資訊，請參閱[主機](../core/hosts.md)。  
  
 主控件執行個體是處理、接收和傳輸訊息的程序。 您可以在每部執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]、而且具有一或多個主控件與之對應的伺服器上安裝主控件執行個體。 如需主控件執行個體的詳細資訊，請參閱[主控件執行個體](../core/host-instances.md)。  
  
 主控件具有下列特性：  
  
-   主控件是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 物件的邏輯容器。  
  
-   每部伺服器上僅能存在一個特定主控件的執行個體。  
  
-   您可以將一個主控件對應到多部伺服器。  
  
 主控件執行個體具有下列特性：  
  
-   主控件執行個體是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 物件的實體容器。  
  
-   當您將伺服器對應到主控件時，需建立主控件執行個體。  
  
-   當負載平衡或是針對容錯移轉時，一部伺服器上可以有多個主控件執行個體 (屬於不同主控件)。  
  
 下圖顯示伺服器、主控件與主控件執行個體之間的關係。  
  
 ![主控件、 主控件執行個體和伺服器關係](../core/media/ebiz-ops-adm01.gif "ebiz_ops_adm01")  
主控件、主控件執行個體與伺服器之間的關係  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何建立 BizTalk Server 主控件環境](../core/how-to-create-a-biztalk-server-hosting-environment.md)  
  
-   [如何建立新的主機](../core/how-to-create-a-new-host.md)  
  
-   [如何修改主控件屬性](../core/how-to-modify-host-properties.md)  
  
-   [如何刪除主控件](../core/how-to-delete-a-host.md)  
  
-   [如何新增主控件執行個體](../core/how-to-add-a-host-instance.md)  
  
-   [如何啟動主控件執行個體](../core/how-to-start-a-host-instance.md)  
  
-   [如何停止主控件執行個體](../core/how-to-stop-a-host-instance.md)  
  
-   [如何刪除主控件執行個體](../core/how-to-delete-a-host-instance.md)  
  
-   [如何修改主控件執行個體屬性](../core/how-to-modify-host-instance-properties.md)